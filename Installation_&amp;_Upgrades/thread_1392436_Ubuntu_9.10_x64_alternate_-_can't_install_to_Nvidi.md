---
title: "Ubuntu 9.10 x64 alternate - can't install to Nvidia RAID 0"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by smk666 on 2010-01-28
Hi! I have a little problem. I wanted to install Ubuntu 9.10 x64 to my desktop, side-by-side with existing windows 7 installation. Unfortunately, I have a RAID 0 setup based on two 500GB Seagate disks, and built in motherboard SATA controller (I have P5N-E-SLI, nForce 650 chipset). Alternate installer sees only the first 500GB disk in RAID, which is obviously empty and every boot to installer screws my RAID - BIOS says Error! instead of Healthy until i turn the PC on and off, reboot doesn't do the trick. I read, that alternate install version should install without a hitch on RAID disk... well, not for me :( My MB isn't that new, I bought it about 2 years ago, so my SATA controller should be supported...

---

### Post by llawwehttam on 2010-01-28
Hmm, are you using fake raid or a proper RAID card. Many on board raid adapters do NOT create a real raid. 

Ubuntu have a howto here: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by smk666 on 2010-01-28
Yeah, it is fake raid, and I've read this how-to, but installation from alternate isn't going as in there. Installer asks me if it should mount SATA RAID disks, when i choose yes, it shows only my first physical drive.

---

### Post by Rody on 2010-01-28
I have had the same problem... i finaly gave it up and will try again later.

---

### Post by smk666 on 2010-02-01
Any luck troubleshooting this issue? I think I tried everything, yet I'm unable to convince installer that I have two 500GB SATA disks in RAID 0 instead of a single 500GB drive...
So far I tried:
9.10-amd64-desktop and 9.10-amd64_alternate both from USB stick and CD. USB bootable disk was made either under windows and under Ubuntu 9.10 on my netbook.

---

### Post by thomasjj70 on 2010-02-10
I have the same issue with 9.10 several months ago upon its initial release, I recall there being a thread on this.. and it was a known bug in grub I think, I reinstalled 9.04 and it works fine... So much for bleeding edge.. If I find the link I will post it.  I found your post because I was curious to see if they fixed this.

---

### Post by thomasjj70 on 2010-02-10
OK, hopefully this helps:
[http://ubuntuforums.org/showthread.php?t=1305811]("http://ubuntuforums.org/showthread.php?t=1305811")

---

### Post by smk666 on 2010-02-11
But my problem isn't about grub. On the very beginning, partition manager sees only one disk. As I can't make 1TB backup and want to retain my win 7 installation, I didn't want to mess around with it...

---

### Post by thomasjj70 on 2010-02-11
Sorry smk666, helps if I read a little closer.. Do you have older versions of ubuntu lying around, wondering if this is not the case, lets say in Jaunty 9.04?

---

### Post by smk666 on 2010-02-14
Unfortunately, I don't have any by now, and downloading 700MB iso over GPRS isn't fun ;). I'll try to download older versions while at the university trough decent connection.

EDIT:
I tried 9.04 x64 with no luck...

---

### Post by smk666 on 2010-02-25
10.04 newest Alpha desktop-amd64-alternate have the same issue...

---

### Post by smk666 on 2010-02-27
I've installed fedora 12 amd64 with no problem, nor tweaking. However, i don't like this distro, so I'll try ubuntu 8.04 LTS, hope this will work...
As expected, 8.04 LTS alternate does'nt wor either. I think that the reason for this is lack of dmraid package, which is used by fedora.

---

### Post by smk666 on 2010-02-27
Anyone can guide me how to for example incorporate fedora's way of handling RAID into installation of Ubuntu? I'm in grave need of sorting this out...
In the meantime I'll try debian net install image if it could discover RAID properly.

Debian have the same issue as ubuntu...

---

### Post by smk666 on 2010-03-01
Wrapped up problem to a new tread:
[http://newyork.ubuntuforums.org/showthread.php?t=1418981](http://newyork.ubuntuforums.org/showthread.php?t=1418981)

---

