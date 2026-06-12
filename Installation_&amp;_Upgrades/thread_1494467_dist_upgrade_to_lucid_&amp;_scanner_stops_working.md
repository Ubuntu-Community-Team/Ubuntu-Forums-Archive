---
title: "dist upgrade to lucid &amp; scanner stops working"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by raennnn on 2010-05-27
I've been using Karmic 64-bit on a new build for awhile.  The Epson 1240 scanner works fine using Xsane or Gscan2pdf.  After a distribution upgrade to Lucid, both Xsane and Gscan2pdf do not detect a scanner.  Lsusb shows the scanner as being present.

---

### Post by electronico_nc on 2010-06-02
Hi,
I had the same problem using a Brother DCP-375CW scanner.
While upgrading to Lucid, I noticed installer asking to use the Lucid ```
/etc/sane.d/dll.conf
``` or the installed one.
I've choosen to see the differences and I saw that installer wanted to remove this line :```
brother3
```I've written it on a paper... and choose the install the Lucid version.
After the upgrade completion, Xsane refused to find the scanner :  just added the "brother3" line to "/etc/sane.d/dll.conf" and everything is OK now.

I can't help with your specific scanner but I'm pretty sure it is the same thing.
Hope this helps

---

### Post by raennnn on 2010-06-03
Actually, power cycling the scanner solved the problem.  Sigh. (Duh)

---

