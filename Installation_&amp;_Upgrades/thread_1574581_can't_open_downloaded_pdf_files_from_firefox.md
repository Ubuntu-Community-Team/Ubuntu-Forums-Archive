---
title: "can't open downloaded pdf files from firefox"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by jayanthan on 2010-09-14
hi

when i download a pdf file and open it from downloaded file list it opens with gimp.
now i've tried all i can. the gnome-open association is with evince.
i've tried changing the application management in firefox preferences to gnome-open and evince for pdf.
still pdf files can only be opened with gimp.
what should be done now. 

MozPlugger 1.10 is already installed.
but i dont have the adminstrative powers


i'm pasting the mozpluggerrc (pdf part)
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
repeat noisy swallow(evince) fill: evince "$file"
repeat noisy swallow(kpdf) fill: kpdf "$file"
repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
GV()

---

