---
title: "ubuntu boot hangs"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by morningla on 2006-08-20
Hi, I did a search but it didn't seem like anyone else have this problem.  I am installing off the Boot DVD on a fresh NTFS HDD. Ubuntu boots and freezes at detecting hardware drivers...  Everytime it loads to that part it gets stuck.

I have no OS on that HDD.  Any suggestions?

will deleting the NTFS to a fresh partition help?  I was thinking it's just loading the files to RAM, am I wrong?  Why is it getting stuck at loading device drivers?

---

### Post by K.Mandla on 2006-08-20
Not sure. But it's best to leave Ubuntu's destination empty (as in "unpartitioned"). I would get rid of the NTFS partition first, and see if that helps.

---

### Post by morningla on 2006-08-20
tried, no difference

---

### Post by Titus A Duxass on 2006-08-20
If you have any strange or exotic hardware, either unplug it (for usb) or remove it.  Then try an install.

---

### Post by morningla on 2006-08-20
looks like you are right.  I took out my SB Audigy 1 Platinum and it worked.  Now it's getting stuck installing the OS at 74% everytime!??

Internet already works but I can't install the OS on my new 160GB HDD.  stuck at 74%

---

