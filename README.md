# couplet

**couplet** will resolve paired-end reads generated from **CEGX 5-Letter Seq** sequencing kits into 4-letter genomic reads annotated with the epigenomic status of cytosines.

It takes paired-end FASTQ files as an input and generates an output FASTQ file of resolved reads.

Additionally, metrics associated with the resolution process are written to a yaml file and reads that fail to resolve are written to a discarded reads FASTQ file-pair.

## Changes in this fork
- Resolved fastq records include ML:B:C tags by calculating likelihoods from the union of basecall quality scores at the relevant bases.

- Ambiguous modifications (i.e., either 5mC or 5hmC) are given a separate modification code "C+u" so that 5mC, 5hmC, and ambiguous modifications each have unique, non-overlapping lists of cytosines. This allows downstream tools such as modkit to handle them separately or combine them if desired.

- Certain package versions have been updated in `requirements.txt` to avoid installation issues.

## Installation
It is strongly recommended to use Python 3.10 with a virtual environment when running this software due to its dependence on outdated package versions. 

```
# Clone repository
gh repo clone sbasrai98/couplet
cd couplet

# Set up Python virtual environment
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
python3 -m pip install .
```