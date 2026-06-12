---
title: "Ubuntu 10.04 freeze during installation on Asus A7S8X-MX"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by antarctyca on 2010-09-20
Try to install ubuntu 10.04 on Asus A7S8X-MX (chip SiS 741GX, cpu Athlon 2500+ Barton, non x64, ram 2GB). Installing from CD i386 on IDE a disk. Installation does not occur, no information on dysplay, only cursor on black screen.
 
What's wrong?

---

### Post by sikander3786 on 2010-09-20
First of all check the MD5SUM of the downloaded image. See here.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If they do match, check your cd for defects, hit any key as soon as the computer passes the BIOS screen, keep on hitting until you see a menu containing Check CD for defects.

If even the menu doesn't show up, try burning a new cd at the lowest speed possible.

---

### Post by antarctyca on 2010-09-20
Thank you, sikander3786
 
I think CD is ok, because i've installed Ubuntu from it on the other PC. About the menu I did not know, thanks again for the help. As you prompt, i tried several menu options: "Try without installation", "Install", "Check disk", but only "Test memory" is success. In other modes I see only the cursor on the black screen.
 
May be, problem is SiS chip itself?

---

### Post by sikander3786 on 2010-09-20
It might be the SiS graphics chip. You might be interested in the alternate installer. It should work. It is a bit advanced installation but not that much difficult.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

You can find the installation instructions here.

[https://help.ubuntu.com/10.04/installation-guide/index.html](https://help.ubuntu.com/10.04/installation-guide/index.html)

---

### Post by antarctyca on 2010-09-20
Solved.
 
I've connected the monitor through the old PCI videoadapter to check the SiS chip video. The result hasn't changed. Hence the problem should be lockalized by another way.
 
Last component to check was the RAM. The memory test has shown set of errors, since 50 percent of execution. It has appeared, two gigabyte-size modules of different manufacturers are incompatible.
 
Thanks to all, especially to Ubuntu developers and sikander3786

---

