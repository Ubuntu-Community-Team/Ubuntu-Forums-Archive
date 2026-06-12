---
title: "LaTeX Error: File `glossaries.sty' not found"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2010-04-05
Have searched around the web and here but can't find what package to load to solve the problem.  Running 9.10   Suggestions?

---

### Post by stinkinrich88 on 2010-04-20
any luck? Same problem here...

---

### Post by deeppow on 2010-04-20
Found these instructions elsewhere and I've gotten things to work.  I needed everything noted to get the setup I was using to work.


1. If you miss some package in your latex installation, first search for a missing package at  [http://tug.ctan.org/search.html](http://tug.ctan.org/search.html)

2. Second, you must know the PATH to your existing TDS tree (I will call it TEXMFLOCAL). Usually, you can see the path from the output during your latex compilation. On my Ubuntu Desktop, it is /usr/local/share/texmf/

You can also check it by typing
kpsewhich -expand-var "\$TEXMFLOCAL"

3. Installing "glossary" package.  Download glossary.zip from above web site.  Unzip it:

Execute: 
cd ./glossary
latex glossary.ins

Copy glossary.sty into TEXMFLOCAL/tex/latex/contrib/. (You may have to create this folder).

Copy glossary.perl into the LaTeX2HTML style files directory (e.g. latex2html/styles. (I copied to TEXMFLOCAL/tex/latex/html/).

Execute:
sudo texhash TEXMFLOCAL

4. Installing "glossaries" package.  Download glossaries.tds.zip from above web site.

Execute:
sudo unzip glossaries.tds.zip -d TEXMFLOCAL/
sudo texhash TEXMFLOCAL


Note, that TEXMFLOCAL is a path to a folder pointed by kpsewhich -expand-var "\$TEXMFLOCAL".
Installing "xfor" package

Note: It might require to update xkeyval

5. Download xfor.tds.zip from above web site.

Execute:
sudo unzip xfor.tds.zip -d TEXMFLOCAL/
sudo texhash TEXMFLOCAL

---

### Post by stinkinrich88 on 2010-04-20
Sorted, thanks!

---

### Post by ammar.afzal on 2010-11-23
Hi, Thanks for the post. well i followed it and was able to remove the error 'not found', but now i have a new error message **'option clash for package glossary makeglossary'** any idea about that, how to get rid of this. also i am using Kile on Ubuntu 10.04.
BR

---

