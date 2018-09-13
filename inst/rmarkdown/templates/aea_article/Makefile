AEA_TEMPLATE_URL=https://www.aeaweb.org/content/file?id=57

all: inst /usr/local/bin/pdflatex

inst: aea_template \
			template.yaml \
			skeleton/aea.bst \
			skeleton/AEA.cls \
			skeleton/multicol.sty \
			skeleton/setspace.sty \
			skeleton/references.bib

aea_template.zip:
				curl "$(AEA_TEMPLATE_URL)" -o $@

aea_template: aea_template.zip
				unzip -j $< "latex_templates/*" -d $@

template.yaml:
				mkdir -p $(dir $@)
				echo "name: American Economics Association journals\ndescription: >\n  Template for creating an article for submission to journals published by the American Economics Association: AEJ, AER, JEL, PP.\ncreate_dir: true" > $@

resources/template.tex: aer_template/AER-Article.tex
				mkdir -p $(dir $@)
				## cp $< $@
				## I edited the included template to be compatible with R Markdown

skeleton/aea.bst: aea_template/aea.bst
				mkdir -p $(dir $@)
				cp $< $@

skeleton/AEA.cls: aea_template/AEA.cls
				mkdir -p $(dir $@)
				cp $< $@

skeleton/multicol.sty: aea_template/multicol.sty
				mkdir -p $(dir $@)
				cp $< $@

skeleton/setspace.sty: aea_template/setspace.sty
				mkdir -p $(dir $@)
				cp $< $@

skeleton/references.bib:
				mkdir -p $(dir $@)
				echo "@article{coman1911,\n \\
 					ISSN = "00028282",\n \\
 					URL = "http://www.jstor.org/stable/1802904",\n \\
 					author = "Katharine Coman",\n \\
 					journal = "The American Economic Review",\n \\
 					number = "1",\n \\
 					pages = "1--19",\n \\
 					publisher = "American Economic Association",\n \\
 					title = "Some Unsettled Problems of Irrigation",\n \\
 					volume = "1",\n \\
				  year = "1911"\n \\
				}" > $@

/usr/local/bin/pdflatex:
				ln -s /Library/TeX/Distributions/.DefaultTeX/Contents/Programs/texbin/pdflatex /usr/local/bin

clean:
				rm -rf aea_template*


