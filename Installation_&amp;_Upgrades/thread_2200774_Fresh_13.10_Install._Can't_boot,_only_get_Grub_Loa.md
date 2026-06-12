---
title: "Fresh 13.10 Install. Can't boot, only get Grub Loader"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by dswanson32 on 2014-01-21
I did a fresh install of Kubuntu 13.10 today on my desktop.  I previously had Linux Mint 15 but wanted to try Kubuntu.  The install went perfectly, I installed the OS on a 60 GB SSD and my /home is on a 1TB HDD.  It says the install was successful and the system needs to reboot.  After that happens all I get is the Grub Loader and I have no idea what to do.  I tried the command 'boot' but it says something like it couldn't load the kernel.  
System Specs:
MSI mobo
Intel G2020 2.9GHz processer
PNY 8GB RAM
ATI 7790 1GB GPU

Any help would be great, Thanks!

---

### Post by tfrue on 2014-01-21
If you can, live boot into Ubuntu, install boot-repair, and create the boot-info page and post the URL here. Please and thank you!
Here is a link to installing boot-repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Chris

---

### Post by tfrue on 2014-01-21
You may even try the recommend repair first, and see if that fixes it.

---

### Post by jp734 on 2014-01-21
grub loader??? you mean you are are getting "grub>" prompt??? If so, this happens on my pc all the time. Apparantly there is something wrong with my keyboard. Anyway, I just hit esc key and it brings me back to grup boot option (where you can select which OS to boot). Then it's back to normal.

---

### Post by dswanson32 on 2014-01-22
So I was able to run the boot-repair and all is good. Thanks!

---

### Post by tfrue on 2014-01-23
Good! Glad things turned out!

---

