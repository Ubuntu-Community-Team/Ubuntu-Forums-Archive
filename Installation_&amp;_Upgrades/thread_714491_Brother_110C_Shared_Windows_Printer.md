---
title: "Brother 110C Shared Windows Printer"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by dgoodma on 2008-03-03
I have searched the Forums, do not see this exact issue addressed.

I have a Windows Shared Printer, a Brother 110C USB printer attached to a Windows XP desktop, and shared.

I have installed the lpr and cups drivers documented on this site:
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

The install seemed to work and created
/usr/local/Brother/cupswrapper/cupswrapperDCP110C-1.0.2

When I go through the add printer dialog, it sees the shared printer, then when I select Brother as the vendor, it wants the .PPD file. I navigate to the directory above, but there are no PPD files, just the one shown, but it will not accept that. I tried cp to add the .ppd, but it does not like that either.

Ideas?

This is on Linux MInt, "Daryna"... previously I did have this working on Ubuntu 7.10. I installed Mint just to compare. I posted this on the Mint Forum, but it is not as "active" as this forum. But, this sort of thing should work the same on both I would think?

---

### Post by empthollow on 2008-03-03
i would try messing with the cups web interface to try to add the printer there.  just type the following into a web browser on your linux machine.
```
localhost:631
```

---

### Post by dgoodma on 2008-03-04
Thanks, that gives the same error, it will not open the file that was downloaded from Brother.

---

### Post by empthollow on 2008-03-04
is it possible the file is corrupted?, you could try downloading it again.

---

