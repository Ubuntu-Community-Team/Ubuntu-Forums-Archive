---
title: "Installing 10.4, 64bit,  and multiple 9.10s/re-partitioning"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Todd in Berlin on 2010-04-22
Hi,

I just installed 9.10, and... unfortunately by mistake, also a second time because there was a problem with the first password.  

I want to install 10.4 side by side with Windows (Vista/7) which came pre-installed on this new computer, which has Pentium Dual-Core 2.2Ghz, 64 bit.

Running 10.4 64bit off the Live CD... ran a command, this is what my hard drive looks like right now:

Disk /dev/sda: 320.1 GB, 320072933376 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12582912   27  Unknown
/dev/sda2   *        1567        1580      102400    7  HPFS/NTFS
/dev/sda3            1580       13150    92936072+   7  HPFS/NTFS
/dev/sda4           13151       38913   206941297+   5  Extended
/dev/sda5           21739       38210   132311308+  83  Linux
/dev/sda6           38211       38913     5646816   82  Linux swap / Solaris
/dev/sda7           13151       21382    66123477   83  Linux
/dev/sda8           21383       21738     2859538+  82  Linux swap / Solaris

So, during the installation process, I pick "Specify partitions manually", and I want to decide what to delete (including both 9.10s), whilst only keeping the Windows apps.

I think sda5 to 8 should get deleted, but I dont understand what sda3 is, or if there is anything else involved.

***

Also, whilst running Live CD the screen very occasionally does get a momentary flash of noise, which reminds me of what happens when using a Windows app on a computer with an OS incompatibility, but which still permits an install of the app.

Cheers!

---

### Post by zvacet on 2010-04-22
Delete all Ubuntu partitions and you will have just sda4 witch is extended.Install Lucid but if I can suggest,make separate home partition.You will have 3 partitions

1. root=10GB     ext4                  mountpoint /
2.swap=2GB
3.home= rest of free space    ext4     mountoint /home

This way your files&settings will be on home partition so you will be able to upgrade,reinstall,fresh install... without losing files/settings.
Don't touch sda3 if you don't know what is on that partition.

---

### Post by brc816 on 2010-04-22
Todd, you didn't specify the model/make of your laptop (and normally you wouldn't have needed to), but my suspicion is that you have either an HP/Compaq box or a Dell box. Both suppliers, AFAIK - I can personally vouch for HP - like to put a spare copy of the Windows installation kit on another partition on the primary drive. That way, if your "real" Windows installation gets fouled up, you can boot off of the other one which will permit you to analyze and repair the problems.

So, that may answer why you have two Windows/NTFS partitions.

When you install Linux, you will likely end up overwriting the Windows boot block so that you will always be booting off of GRUB (or GRUB2 depending on your Linux distribution and its age), and that's OK because when you install Linux, most of the major distributions (including Ubuntu) will sniff out the Windows installation and put it in the boot menu; Ubuntu and GRUB2 are especially good at that, but Fedora, OpenSUSE and Mandriva also do a good job from what I've personally seen.

After that, it's a matter of adjusting the Grub configuration to specify which OS you want to boot as your default.

---

### Post by Todd in Berlin on 2010-04-22
Hi. Thanks... I have a few suggestions now which seems similar... I have a brand new Acer Excenta 5635Z with Pentium 4400 Dual Core 2.2 Ghz, 4GB memory, 320gb hd. Windows was pre-installed and no start up disks etc came in the box, and there is some special protocol for a big system problem but I am not sure how it works...

---

