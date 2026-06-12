---
title: "no printers in firefox??"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by harty83 on 2008-10-16
I have no printers other than print to file showing up in firefox.  Then when I try to print to file, firefox locks up.

Any idea on a remedy?

Using 64bit edition of Intrepid

---

### Post by bash on 2008-10-16
You using 32 or 64bit Firefox?

---

### Post by harty83 on 2008-10-16
64bit edition

---

### Post by harty83 on 2008-10-19
Bump...this is annoying.  I need to be able to print from firefox.

Thanks!
Alan

---

### Post by ktp on 2008-10-19
I am able to print to PDF on 64-bit.  Just printed this page.

---

### Post by cariboo on 2008-10-19
Rename you profile and create a new one to see if that fixes the problem. the profile is located in ~/.mozilla. Press Ctrl-h in Nautilus to see hidden files and directories.

JIm

---

### Post by harty83 on 2008-10-19
> **cariboo907 said:**
> Rename you profile and create a new one to see if that fixes the problem. the profile is located in ~/.mozilla. Press Ctrl-h in Nautilus to see hidden files and directories.

JIm

This does not help.  Still no printers in firefox other than print to file which seems to sporadically lock up firefox.

---

### Post by harty83 on 2008-10-20
Any other clues as to why firefox does not have any printers available other than print to file?  Everything else has my cups printers available.

---

### Post by philinux on 2008-10-20
Give

```
firefox -safe-mode

```
a try from the terminal.

---

### Post by harty83 on 2008-10-20
> **philinux said:**
> Give

```
firefox -safe-mode

```
a try from the terminal.

Still no go.  

I just tried uninstalling and reinstalling everything firefox with no luck.

What libraries tell firefox what printers are available?  Again this is on a 64bit installation of Intrepid.

---

### Post by harty83 on 2008-10-26
Bump.  Any new ideas? Ibex is a few days from release and I still can't see any printers in firefox 64bit edition.

---

### Post by harty83 on 2008-10-26
Solved.  I got to looking around at my links.  Apparently /usr/bin/firefox was linked to a firefox installation in /opt/firefox which I had under hardy.  Fixed the links and now I have printers :-)

Sorry!

---

