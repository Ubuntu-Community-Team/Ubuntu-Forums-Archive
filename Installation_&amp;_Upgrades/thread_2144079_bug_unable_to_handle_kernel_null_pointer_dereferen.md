---
title: "bug: unable to handle kernel null pointer dereference at 0000013c"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-05-11
Am trying to install xubuntu 12.04.2 on Dell Inspiron 1502.  It boots fine from a memory stick, but when I click on Installation, it gets the message:  bug: unable to handle kernel null pointer dereference at 0000013c.  Message shows up when I click "Continue" after the installation window that says I am connected to power, have 4.x GB space on disk, and am not connected to the Internet.  I have tried multiple times.  I also tried Ubuntu 12.04.2 with similar results except the address given is 00000144.

Anybody else have this problem?  Anybody have a solution?  It seems bad when I can't even get linux installed.

Thanks in advance.

---

### Post by hansdown on 2013-05-11
Hi 
Ralph L.

For starters, You need to have a GOOD internet conection, as some files need to be downlowded during the install.

---

### Post by IngerK on 2013-05-13
I have same problem, Dell latitude 600D. This is bad on LTS!
First I tried Ubuntu 12.04 LTS on my old D600, but ran into the kernel "pae"  problem. That's why I downloaded Xubuntu 12.04.LTS...

---

### Post by IngerK on 2013-05-13
Lubuntu works.

---

### Post by Ralph L on 2013-05-15
I tried and tried again to get either xubuntu 12.04 or ubuntu 12.04 to get by the dereference problem, and suddenly it worked and I was able to install ubuntu.  I didn't try xubuntu again as I didn't want to screw up a working system.  On the try that actually worked I selected "Install Ubuntu" rather than "Try Ubuntu ...." at the beginning of the boot.  And I installed it from a memory stick rather than from a CD.  

However, I have had this problem before on other Dell Laptops (Latitude D610).  In that case I was able to install ubuntu 12.04--but again only after many tries and changing everything I could think of--like doing, or not doing, a repartition during the installation; using the "Install Ubuntu" or "Try Ubuntu..."; using a memory stick, or a CD, using Ubuntu 12.04, 12.04.1, or 12.04.2, or using xubuntu with its variations; running a memory test immediately before installation, or not.  At one point I tried Lubuntu and it didn't work.  Also, I tried ubuntu 12.10 and xubuntu 12.10 and neither of those would work.

So there seems to be some sort of intermittent bug in 12.04 and later that makes it incompatible with older Dell laptops.  So I can't mark this thing as solved.  It isn't!!!!!!!!!!!!!!

---

