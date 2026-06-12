---
title: "my HP laserjet MPF m1212nf prints pdf files as vertical lines"
date: 2018-02-04
forum: Installation &amp; Upgrades
---

### Post by sramij on 2018-02-04
Howdy;

I have installed my HP printer on ubuntu using hplip-3.17.11.run script. Everything went through OK.

However, pdf files are printed as vertical lines, almost completely black paper.

I've googled this subject a lot, but cannot find anything relevant. My GS version is 9.18.

Rami

---

### Post by ajgreeny on 2018-02-04
If you're using evince, the default document-reader application to open PDFs, try another PDF reader such as qpdfview or okular; I have in the past had a similar problem with evince being unable to print documents but other applications usually can.

---

### Post by sramij on 2018-02-07
@ajgreeny does your answer relate to printing as well? is it kinda the backend used to decode the pdfs before sending them over to the printer? I am not familiar with evince, but I probably use whats is default there on Ubuntu 16.04.

---

### Post by ajgreeny on 2018-02-07
Evince is the default PDF reader in 16.04, and it has been that application which caused mr printing problems in the past.
If to use another PDF reader it may print fine; that was my experience.

Installing okular will pull in several KDE/qt packages so you may like to try qpdfview or xpdf first.

---

