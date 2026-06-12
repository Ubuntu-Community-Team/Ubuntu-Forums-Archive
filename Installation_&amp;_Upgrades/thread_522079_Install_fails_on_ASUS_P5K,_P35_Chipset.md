---
title: "Install fails on ASUS P5K, P35 Chipset"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by andygrove on 2007-08-10
I've just purchased a new PC with ASUS P5K SE motherboard (P35 chipset), Intel Q6600 (4x2.4GHz), 2x250GB SATA II, GeForce 7200GS.

I'm trying to install Ubuntu 7.04 from a CD. The installer seems to start up fine - I get a screen showing the ubuntu logo and a progress bar animation. After a while the screen blanks and I get errors like this:

[   177.458592] Buffer I/O error on device fd0, logical block 0
[   189.639000] Buffer I/O error on device fd0, logical block 0
[   215.054764] Buffer I/O error on device fd0, logical block 0

I've also tried installing Fedora 7 and that boots into the installer fine but then fails to recognize the CD/DVD driver and I can only install over the network, and that keeps hanging after a while.

Windows Vista installs fine on the same machine so it doesn't appear to be a hardware problem.

Any suggestions would be appreciated!

Thanks,

[Andy Grove]("http://www.codesuccess.com/blog/").

---

### Post by andygrove on 2007-08-10
I just found this:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

The problem was that I have no floppy drive but it wasn't disabled in BIOS.

Hope that helps others.

[Andy Grove]("http://www.codesuccess.com/blog/").

---

### Post by rbmorse on 2007-08-10
Did you get a good install, otherwise?  

I'm looking at building a P35 box, but the early problems with the P965 chipset motherboards and support for their jMicron 363 PATA controllers remains a strong and painful memory.

---

### Post by fredj on 2007-08-11
there is nothing really wrong with the Jmicron software. Sata drives usually can be set to three
modes, IDE, RAID or AHCI. In the bios you can set your sata hdd mode.
What I have found is Windows XP will install and boot under IDE mode with no problems.
Ubuntu will install under IDE mode but is reluctant to boot in this mode.
The Live CD install will not always work under AHCI mode.
In the end to make a dual boot XP/Ubuntu computer I had to do the following. Set the sata hdd
to AHCI mode. Then to install XP you need a floppy with the sata drivers on it. Usually you can
make this using the motherboard driver CD.
Install Ubuntu from the Alternate install CD (the Live CD may not work). Ubuntu has built in drivers
for sata so after that you should have no problems.
However search for the post on these forums 'Is Ubuntu destroying your hdd' and read it
carefully because it contains a fix for problems with current version of the kernel.

---

### Post by arizonagroovejet on 2007-08-12
For reference, in case anyone finds it useful.

I just built a new system using an Asus P5K mobo and use Kubuntu 7.04. I'm using a SATA harddisk but IDE optical drive. (Plan to switch that to SATA though)
I also got the "Buffer I/O error on device fd0" errors until I disabled the floppy drive option in the BIOS. (I have no floppy drive attached.)

After getting rid of the fd0 errors I then kept getting sr0 errors. After finding this thread I downloaded the alternate CD and used the text based install. That worked fine. Still copying data over from my old machine but USB Firewire, networking and sound all work so seems all good.

Only thing that's bugging me is about the mobo BIOS. I had no option to switch the SATA harddisk to AHCI mode. The option is in the manual but in the BIOS there's only one option and that's IDE. There's another thread on where someone mentions switching to AHCI too.

---

### Post by FunkyRider on 2007-08-13
as far as I concerned, only motherboards equipped with ICH9R (not ICH9 plain) will support AHCI/RAID modes under the ICH9R connectors (i.e. not through the J-Micron ones). I'm using P5K-E Wifi-AP version and it shows three modes: IDE/AHCI/RAID and I'm using the AHCI mode without a problem. (Feisty 7.04) :popcorn:

---

### Post by nosebreaker on 2007-08-14
Has anyone gotten the RAID to work?  I have (4) 500GB drives in a RAID10 setup (should be 1TB), but ubuntu 7.04 only sees the drives as 4 normal 500GB SATA drives.

---

### Post by nosebreaker on 2007-08-16
I think I got it to work, but dmraid shows 2 separate volumes instead of 1 raid10 volume.  I was following the FakeRaidHowto

---

### Post by Dingo_aus on 2007-08-18
From my searching around the net it seems 2.6.18 of the kernel (in Feisty 7.04) doesn't have support for the Marvel controller.  There seems to be a patch for 2.6.20 onwards.

So at this stage I'm going to try a net install and then a recompiled kernel with the patch to get my DVD working again.

---

### Post by arizonagroovejet on 2007-08-18
> **Dingo_aus said:**
> From my searching around the net it seems 2.6.18 of the kernel (in Feisty 7.04) ....

You seem to be saying that Feisty uses kernel 2.6.18. But...


```
mike@continuity:~$ more /etc/issue
Ubuntu 7.04 \n \l

mike@continuity:~$ uname -a
Linux continuity 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
mike@continuity:~$
```

---

### Post by Left hand of Gaia on 2007-08-21
Evening all,

I'm having a similar issue on my new machine.  I've been trying to install anything onto it, but I keep getting the same problem:

1) CD boots normally
2) Run LiveCD/Text Installer (with all variations of "quiet splash nosplash noapic nolapic irqpoll")
3) a) LiveCD crashes,  /dev/sr0 errors (it can't find the CD-drive, as far as I can tell)
    b) Alt Installer detects hardware, tries to mount and read the install CD, can't find it, dies

Hardware:
  Intel Xeon x3220
  Asus P5K mobo
  Intel P35 chipset
  nVidia 8800 GTS
  LG DVD/CD RW
  SATA HD


I'll gladly entertain any suggestions that can help me.

Thanks in advance.

---

### Post by rbmorse on 2007-08-23
I was afraid of that.  Does your optical drive use an S-ATA or P-ATA interface?  

That sounds an awful lot like the jMicron 363 problem we had with the Intel 965 chipset boards.

---

### Post by Dark Star on 2007-08-23
1'st of all the Quad core is 2.4 ghz not 4x 2.4 it has 4 core not 4x speed :p btw Auss P54 is a new series board you will face problem. Hope all this get cleared in Gusty :D Cause I'll be upgrading soon :D

---

### Post by Left hand of Gaia on 2007-08-23
Ok, I've made some progress.

I can netboot off of a USB stick, and I can run the 7.10 Tribe 4 text install CD.

I have to load the atl1.ko module by hand, as is is not included in the default CDs.  I plan on trying to add it to the net boot initrd image tonight, to see if that can help there.

With the 7.10-T4 disk, I can see the network, install files, but I can't access a mirror to get updated files, nor can I install grub to /dev/sda.  I can chroot into the new filesystem, but can't boot off of it, nor can I install ubuntu-desktop.

Any ideas?  Can I loop-mount an iso as rw to add the device module (never played with isos that way before) and create an updated iso?

Regards,

LHoG

---

### Post by Dingo_aus on 2007-08-25
I can confirm that swapping over an IDE DVD-ROM for a SATA one is a fix to this issue.

---

### Post by andygrove on 2007-09-22
I just installed Fedora 8 Test 2 (uses 2.6.23 kernel) and this installed cleanly on my machine and I saw it load a marvell pata driver. 

[http://www.codesuccess.com/blog/2007/09/fedora-8-test-2-supports-asus-p5k-mobo.html](http://www.codesuccess.com/blog/2007/09/fedora-8-test-2-supports-asus-p5k-mobo.html)

Andy.

---

### Post by houstonbofh on 2007-09-29
> **Dark Star said:**
> 1'st of all the Quad core is 2.4 ghz not 4x 2.4 it has 4 core not 4x speed :p btw Auss P54 is a new series board you will face problem. Hope all this get cleared in Gusty :D Cause I'll be upgrading soon :D
For the record I am running Gutsy on a Gigabyte GA-P35-DS3L and I am very happy.  This is an odd issue with the nic, and sound, but both are covered on the forum.  It is very fast, and solid.  The Gutsy Live CD booted and installed fine.

---

