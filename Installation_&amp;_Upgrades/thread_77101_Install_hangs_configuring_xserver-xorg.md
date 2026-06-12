---
title: "Install hangs configuring xserver-xorg"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by timlg98 on 2005-10-16
Trying to install v5.10 on AMD 800, 256MB RAM & 30GB HD. Initial install seems to work, then PC is rebooted and the next stage of the install proceeds. The progress bar gets to 71% done and shows "configuring xserver-xorg". The install hangs there and must power pc off and back on. The graphics adapter is an old 16MB TNT2 card. Any ideas???

---

### Post by windynorkan on 2005-10-27
I'm having the same problem. :(

---

### Post by jfr on 2005-10-28
I have a similar problem only mine hangs after 68% of the installation on ttf-opensymbol on both hoary and breezy. Its pretty weird because i installed hoary a while ago without problems but now i cant install either. :confused: 

I have no problem running windows but i tried running repair with the windows xp cd, to clear grub from mbr, but it hangs aswell. Dont know if theres a connection. Havent been able to get some information about this though.

please help

---

### Post by Endwin on 2005-11-24
I had this problem, and I am now dealing with it again. I got it fixed before, on horay, by having the boot install be 'linux noapic nolapic noacpi acpi=off' However, this is not working now in Breezy. Still trying though very very stange problem.

---

### Post by zaczuwodny on 2005-12-13
My installation of Breezy also hangs when configuring xserver-xorg.  I have a PCI video card: S3 Virge/DX; the chip is 86C375.

I replaced that video card with an ancient ISA Cirrus Logic card and that solved the problem for me.

Anybody know which program in the xserver-xorg package is causing the problem?

Zac.

---

### Post by NotJustANewbie on 2005-12-13
This did not happen to me. Have you all checked your md5sums of the install form the official Ubuntu site?!?

If you try typing "server" and _then_ pressing enter (without the quotation marks) when you put the install CD in instead of just pressing enter without typing anything.

After the install (I think it will leave out xserver-xorg [I THINK]), do:
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /usr/sbin/gdm start
sudo reboot

```

Please not that I am an Ubuntu n00b but not a Linux n00b.

---

### Post by c4pp4 on 2005-12-28
[QUOTE=timlg98]The progress bar gets to 71% done and shows "configuring xserver-xorg". The install hangs there and must power pc off and back on.[/QUOTE]
the same problem on:
Asus P2L97
Pentium II 233
S3 Virge VX ( Diamond Stealth 3D 3000 XL 4MB )
320MB RAM
6+3GB HDD
default installation of 5.10

...after hangs, restart, reboot and login, try to type:
```
**sudo dpkg --configure -a**
```
it worked for me...

---

### Post by Sid Steward on 2006-01-06
Same problem. My motherboard has an onboard video controller. I was trying to use a PCI video card, instead. After I ran into this problem I removed the card and used the onboard video controller. I also changed the BIOS to 'Plug and Play OS: No' based on a tip elsewhere. Now the installation is proceeding fine (sudo dpkg --configure -a).

---

### Post by Ptero-4 on 2006-01-06
> the same problem on:
Asus P2L97
Pentium II 233
S3 Virge VX ( Diamond Stealth 3D 3000 XL 4MB )
320MB RAM
6+3MB HDD
default installation of 5.10


Isn't it 6+3GB HDD?

---

### Post by lkean on 2006-01-08
Same problem, hanged at 71%. I have the following setting:
- Abit bp6 MB + dual celeron 366 cpu
- 256mb memory
- Diamond Stealth 3d 2000 PCI graphics card (my Creative AGP card went bad)
- 2 Western Digital ATA66 HDD (10GB + 40GB)

Tried 'sudo dpkg --configure -a' and it seems to have worked for me. I am just started getting back into Linux and Ubuntu seems to be the hot Linux now. This small problem is nothing compared to the pain I went through trying to install Slackware (even Redhat) on this same machine 8 years ago. Linux has come a long way... I like it very much so far.

---

### Post by c4pp4 on 2006-02-18
[QUOTE=Ptero-4]Isn't it 6+3GB HDD?[/QUOTE]
lol... yes, you are right, thanks...

---

### Post by JamesLavin on 2006-04-11
Same problem, hung at 71%. Happened twice.

I believe I have the following config:
- Soyo SY-K7V Dragon Plus! motherboard
- 1GHz Athlon Thunderbird Sock A
- 1GB memory
- 250GB Western Digital ATA100 HDD
- Diamond ViperII Z200 32MB AGP video card

---

### Post by white_tiger_daniel on 2006-04-24
AAAAAARGGHHHH! Same prob for me on:
Intel Celeron 500
256 MB RAM
10GB + 4GB hard drives
S3 Virge Trio VGA Card

](*,) Help!](*,)

D

---

### Post by Packman5280 on 2006-04-25
Had the same problem.  Abit NF8, NVidia Nforce3 250GB, AMD sempron 2800+, 512 ram, S3 video card, not sure exact specs on it since I found it in my closet.  Tried this

sudo dpkg --configure -a

from the terminal, and it loaded a bunch of fonts for a few minutes, then I got the GUI.  Still low resolution (800x600), but it works.  Might just try a different video card, I have a few.  Maybe try the vesa driver first.

---

### Post by theking2 on 2006-05-04
sudo dkpg --configure -a seems to do the trick for a S3 Virge video card. Wonder why this is not available in the standard instalation.

---

### Post by dion on 2006-05-05
I have been experiencing the same problem on a pentium 2 with 256 mb ram.  I actually posted a thread about 2 days ago regarding this.  The strange thing though was that both previous versions of ubuntu 4.10 and 5.04, install and run fine, I wanted to upgrade to 5.10 but this version just refuses to work. I will try some of the suggestions in this thread and hopefully the installation will complete sucessfully.  I also have a S3 Virge Graphics card as mentioned in one of the previous posts, maybe it is an issue with the graphics card.

---

### Post by dananimal on 2006-05-06
Same problem occured at 71% installing on:
Aopen AX6B mother board
S3 Virge

Solved by:
```
sudo dpfg --configure -a
```

---

