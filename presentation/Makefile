# Basename of document to generate
SOURCE = crypto-party

# You want latexmk to *always* run, because make does not have all the info.
# Also, include non-file targets in .PHONY so they are run regardless of any
# file of the given name existing.
.PHONY: pdf presentation $(SOURCE).pdf all clean

# The first rule in a Makefile is the one executed by default ("make"). It
# should always be the "all" rule, so that "make" and "make all" are identical.
all: pdf

# MAIN LATEXMK RULE

# -pdf tells latexmk to generate PDF directly (instead of DVI).
# -pdflatex="" tells latexmk to call a specific backend with specific options.
# -use-make tells latexmk to call make for generating missing files.

# -interaction=nonstopmode keeps the pdflatex backend from stopping at a
# missing file reference and interactively asking you for an alternative.

$(SOURCE).pdf: $(SOURCE).tex
	latexmk -pdf -pdflatex="xelatex -interaction=nonstopmode" -use-make $<

pdf: $(SOURCE).pdf
	xreader $(SOURCE).pdf

presentation: $(SOURCE).pdf
	pdfpc --duration=45 --disable-auto-grouping $(SOURCE).pdf

clean:
	latexmk -CA
	rm -f $(SOURCE).run.xml $(SOURCE).bbl $(SOURCE).nav $(SOURCE).snm $(SOURCE).pdfpc
