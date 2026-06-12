---
title: "Switching distros on duel-boot"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-07-06
Okay, this is a possibility. Nothing else. I am very happy with fedora core 4, and I have spent plenty of time configuring it to my needs.

I am currently duel-booting Windows XP and Fedora Core 4 ( as seen here: [http://img290.echo.cx/img290/8150/screenshothardwarebrowser7bj.png](http://img290.echo.cx/img290/8150/screenshothardwarebrowser7bj.png) ).

I ordered my Ubuntu CD ( is that pronounced Oo-buhn-too? ), and I am considering switching. A lot of research would go with this, becuase when I initially tried duel-booting, Windows  XP failed on me ( and I had to bother a sysadmin friend who normally charges about $100/hour to work on my PC for about 4 hours to fix it free of charge ).

After that expirience, I am under the impression that "if it ain't broken, don't fix it ".

**Is there an easy way that I could switch to ubuntu and still duel-boot with windows?**

Thanks in advance for all your help. :)

---

### Post by Xian on 2005-07-06
From the [Official Ubuntu Install Guide](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en):

[i]"6.3.4. Making Your System Bootable

If you are installing a diskless workstation, obviously, booting off the local disk isn't a meaningful option, and this step will be skipped. 

Note that multiple operating systems booting on a single machine is still something of a black art. You should see your boot manager's documentation for more information. 

6.3.4.1. Detecting other operating systems

Before a boot loader is installed, the installer will attempt to probe for other operating systems which are installed on the machine. If it finds a supported operating system, you will be informed of this during the boot loader installation step, and the computer will be configured to boot this other operating system in addition to Ubuntu. 

Note that multiple operating systems booting on a single machine is still something of a black art. The automatic support for detecting and setting up boot loaders to boot other operating systems varies by architecture and even by subarchitecture. If it does not work you should consult your boot manager's documentation for more information. 
Note

The installer may fail to detect other operating systems if the partitions on which they reside are mounted when the detection takes place. This may occur if you select a mountpoint (e.g. /win) for a partition containing another operating system in partman, or if you have mounted partitions manually from a console."[/i]

---

### Post by Jessehk on 2005-07-06
Okay...

What exactly did that accomplish?

I would be interested to dump Fedora core 4 for Ubuntu while still keeping my Windows partition. 

If I was to pursue this further, how easily would it be done?

I am a linux "newbie", and simply saying that something is quote: "a black art" does not aid me.

Is there a guide that you could link to to help me in switching distros ( if I wanted to )?

Not to be rude, but I am kind of frusterated. :)

---

### Post by Xian on 2005-07-09
Well, if you want the short answer it is fairly obvious. I thought that quoted portion of the Install Guide did an excellent job at describing what the installer attempts to accomplish and configure, and your role during that procedure, as well as some very important disclaimers; but it really is no more complicated than using the Ubuntu InstallCD to reformat your Fedora partition(s), mount them for Ubuntu, and then allow the CD to hopefully autodetect your winxp and add it to the bootloader. This does not always occur for the reasons described above, but it did work fine on my system and most people do not encounter any issues.

It would be advisable to review the entire [Install Guide](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/).

---

### Post by eeried on 2005-07-25
Ubuntu works very well with winxp: no fear it will dual-boot all right.

What I don't know haven't tried yet is installing another Linux distro after ubuntu -- the last should deal with the bootloader -- but ?

---

### Post by FM1 on 2005-07-25
I have XP/Mandriva/Ubuntu. The first time I installed it, I did XP first, then Mandriva (skipped bootloader) then Unbuntu and everything went just fine--Grub got them all. The second time (bought a new drive), I installed XP, Ubuntu and then Mandriva, but all Lilo got was Mandriva and XP; I had to manually edit lilo.conf to add Ubuntu. Works fine now, though.

---

