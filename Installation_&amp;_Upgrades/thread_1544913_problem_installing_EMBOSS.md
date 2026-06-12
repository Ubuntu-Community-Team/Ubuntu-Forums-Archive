---
title: "problem installing EMBOSS"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by noninyo on 2010-08-03
Hi,

I am trying to install EMBOSS.

First I write:
> ./configure --prefix=/home/noninyo/packages/emboss-6.3.1then:
```
noninyo@desktop:~/packages/EMBOSS-6.3.1$ make
Making all in plplot
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot'
Making all in lib
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot/lib'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/plplot'
Making all in ajax
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax'
Making all in pcre
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/pcre'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/pcre'
Making all in expat
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/expat'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/expat'
Making all in zlib
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/zlib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/zlib'
Making all in core
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/core'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/core'
Making all in graphics
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/graphics'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/graphics'
Making all in ensembl
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/ensembl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/ensembl'
Making all in ajaxdb
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/ajaxdb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/ajaxdb'
Making all in acd
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/acd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax/acd'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/ajax'
Making all in nucleus
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/nucleus'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/nucleus'
Making all in emboss
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss'
Making all in acd
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/acd'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/acd'
Making all in data
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data'
Making all in AAINDEX
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/AAINDEX'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/AAINDEX'
Making all in CODONS
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/CODONS'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/CODONS'
Making all in REBASE
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/REBASE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/REBASE'
Making all in PRINTS
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/PRINTS'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/PRINTS'
Making all in PROSITE
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/PROSITE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/PROSITE'
Making all in JASPAR_CORE
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_CORE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_CORE'
Making all in JASPAR_FAM
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_FAM'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_FAM'
Making all in JASPAR_PHYLOFACTS
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PHYLOFACTS'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PHYLOFACTS'
Making all in JASPAR_CNE
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_CNE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_CNE'
Making all in JASPAR_POLII
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_POLII'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_POLII'
Making all in JASPAR_SPLICE
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_SPLICE'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_SPLICE'
Making all in JASPAR_PBM
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM'
Making all in JASPAR_PBM_HLH
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM_HLH'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM_HLH'
Making all in JASPAR_PBM_HOMEO
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM_HOMEO'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data/JASPAR_PBM_HOMEO'
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data'
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss/data'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/emboss'
Making all in test
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test'
Making all in data
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/data'
Making all in embl
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/embl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/embl'
Making all in genbank
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/genbank'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/genbank'
Making all in pir
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/pir'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/pir'
Making all in swiss
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/swiss'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/swiss'
Making all in swnew
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/swnew'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/swnew'
Making all in testdb
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test/testdb'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test/testdb'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/test'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/test'
Making all in doc
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc'
Making all in manuals
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/manuals'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/manuals'
Making all in programs
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs'
Making all in html
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs/html'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs/html'
Making all in text
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs/text'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs/text'
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs'
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/programs'
Making all in tutorials
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/tutorials'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc/tutorials'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/doc'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/doc'
Making all in jemboss
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss'
Making all in images
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/images'
Making all in lib
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib'
Making all in axis
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib/axis'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib/axis'
make[3]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib'
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/lib'
Making all in resources
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/resources'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/resources'
Making all in utils
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss/utils'
make[2]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss'
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1/jemboss'
make[1]: Entering directory `/home/noninyo/packages/EMBOSS-6.3.1'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/noninyo/packages/EMBOSS-6.3.1'
```
Does anyone know how can I fix this??
what does it mean "Nothing to be done for `all-am'."???

10x

---

### Post by kgarbutt on 2010-08-08
Hi noninyo,

I use emboss too. You can install it from the repositories. Open the terminal and type:

sudo apt-get install primer3 clustalw dialign emboss

It will install version 6.1.0.

You can also try emboss before you install it. There is emboss explorer at this web site:

[http://emboss.bioinformatics.nl/](http://emboss.bioinformatics.nl/)

Good Luck & happy cloning,

Ken

---

### Post by xiangwulu on 2013-01-30
hi, sorry that i post my problem here.

i tried to install soaplab2+emboss on amazon web service instance, 

i got java, ant, maven, tomcat installed, built soaplab2 firstly, it can be accessed at:[http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/]("http://ec2-176-34-220-249.eu-west-1.compute.amazonaws.com:8080/soaplab2/"), 

and then i install emboss followed this site: [http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html]("http://soaplab.sourceforge.net/soaplab2/EmbossNotes.html")

but for the step "**ant genemboss**", i got such error message:

```
[acd2xml] Processing digest...
  [acd2xml]     using /root/soaplab2/EMBOSS-6.5.7/share/EMBOSS/acd/digest.acd
  [acd2xml] ERROR: Modification of non-creatable array value attempted, subscript -1 at acd.y line 575.
  [acd2xml]

BUILD FAILED
/root/soaplab2/soaplab2/xmls/emboss.xml:75: The following error occurred while executing this line:
/root/soaplab2/soaplab2/xmls/acd2xml.xml:58: exec returned: 1
```

i searched on the internet for the similar error message but not much information useful. 

would anyone help? thanks so much!!

---

### Post by howefield on 2013-01-30
Old thread closed.

---

