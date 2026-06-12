---
title: "Change default file name in pdf_file_generator"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Delstrons on 2008-04-23
Hi there,

I am trying to print the output of a C++ program using the pdf_file_generator.  The C++ program sends 6 files to the pdf generator but the pdf generator is giving the same name to all of them and therefore overwrites all but the last one.  Does anybody know how to make the generatr assign consecutive file names so that I don't have this issue? (i.e pdfname_0001, pdfname_0002, and so on...)  I have really basic understanding of Ubuntu. Thanks

---

### Post by Delstrons on 2008-04-23
Found useful info at 

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/134671](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/134671)

Changing Label 0 to Label 1 worked fine

---

