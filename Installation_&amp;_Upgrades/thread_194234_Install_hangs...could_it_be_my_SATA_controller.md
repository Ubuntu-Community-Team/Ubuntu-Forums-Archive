---
title: "Install hangs...could it be my SATA controller?"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by ckeck on 2006-06-11
Sorry if this has been asked before, but I cannot find a specific related topic recently...

I am trying to install the newest version of Ubuntu and my install/live CD keeps hanging at "Uncompressing Linux...Ok, booting the kernel."

What might the problem be? Missing SATA controller drivers? Thats the only thing I can think of, but I would think Ubuntu would have these included...motherboard isn't exactly brand new...

Please help...thanks a lot!

---

### Post by tommcd on 2006-06-11
Ubuntu should recognize the SATA controllers. 
One possibility: the CD you are using could be bad. If you downloaded it, did you verify the MD5sums? If not see this:
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
it gives instructions for windows and linux. At the bottom of the page where you download the ISO there is a download for MD5 sums. Download it along with the ISO and check it against the MD5 for the download.
If you got the CDs from ShipIt, they can be bad sometimes too, I've read. In that case try a different CD if you got more than one.
Also, burn the CD ISO at a very slow speed, like 2X or 4X, to make sure it soesn't get corrupted. Hope this helps.

---

### Post by ckeck on 2006-06-11
[QUOTE=tommcd]Ubuntu should recognize the SATA controllers. 
One possibility: the CD you are using could be bad. If you downloaded it, did you verify the MD5sums? If not see this:
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
it gives instructions for windows and linux. At the bottom of the page where you download the ISO there is a download for MD5 sums. Download it along with the ISO and check it against the MD5 for the download.
If you got the CDs from ShipIt, they can be bad sometimes too, I've read. In that case try a different CD if you got more than one.
Also, burn the CD ISO at a very slow speed, like 2X or 4X, to make sure it soesn't get corrupted. Hope this helps.[/QUOTE]

Thanks, I will check the disk image right now...hopefully thats the problem.

---

