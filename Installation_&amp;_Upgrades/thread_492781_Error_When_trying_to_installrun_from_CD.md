---
title: "Error When trying to install/run from CD"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by kenevil on 2007-07-05
Hello All,

I downloaded the Ubuntu 7.04 iso and have tried booting from it on an XP PC. (IBM 8086, 3GHz P4, 1GB RAM, 40GB IDE HDD).

However, I always get the same error:

/bin/sh: can't access tty; job control turned off
(initramfs) _

Can anyone tell me what this means or how to get rid of it? I've booted from the same CD on another PC and it works fine so it's obviously nothing to do with the CD. I've also tried the alternate CD on the same box and I just get a lot of flickering on my monitor and no activity on the CD drive.

Help!

---

### Post by r0ck80y on 2007-07-05
This thread may help:
[http://ubuntuforums.org/showthread.php?t=279884](http://ubuntuforums.org/showthread.php?t=279884)

---

### Post by kenevil on 2007-07-05
Sorry, that doesn't help. Although that guy's getting the same error as me, he's already installed dapper. 

I've been unable to install anything.

---

### Post by lisati on 2007-07-05
> **kenevil said:**
> Hello All,

I downloaded the Ubuntu 7.04 iso and have tried booting from it on an XP PC. (IBM 8086, 3GHz P4, 1GB RAM, 40GB IDE HDD).

However, I always get the same error:

/bin/sh: can't access tty; job control turned off
(initramfs) _

Can anyone tell me what this means or how to get rid of it? I've booted from the same CD on another PC and it works fine so it's obviously nothing to do with the CD. I've also tried the alternate CD on the same box and I just get a lot of flickering on my monitor and no activity on the CD drive.

Help!

I'm not sure I understand having "8086" and P4 in the description of the one machine......

---

### Post by lisati on 2007-07-05
> **lisati said:**
> I'm not sure I understand having "8086" and P4 in the description of the one machine......

Please disregard........

---

### Post by r0ck80y on 2007-07-05
Can you install in safe graphics mode ?? Its also possible that the disk is damaged.

---

### Post by kenevil on 2007-07-05
I've already booted from the CD on another PC so it's definitely not the disk. I'll try the safe graphics mode now.

---

### Post by kenevil on 2007-07-05
I tried safe graphics mode and got the exact same error.

I also took the quiet and splash boot options off and while I don't get any errors, the process was hanging at the network card. I removed my network cable and it now hangs after the following:

[   35.409597] Uniform CD-ROM driver Revision: 3.20
[   35.409428] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.409516] sr 1:0:0:0: Attached scsi generic sg1 type 5

---

### Post by kenevil on 2007-07-05
Whacked a USB CD drive into the PC and booted off that no problem, installing now.

---

### Post by noob44 on 2007-07-10
I'm having the same issue. Is there an alternate to using an external USB CD drive to fix this problem? I have a new gateway pc with the following spec:
	Intel Core2 Quad Processor Q6600 (2.40 GHz)
	Intel (Schroeder Town) G33 Motherboard
	500 GB 7200 RPM SATA II/300 Hard Drive With 16 MB Cache 
	16X Double-Layer Super Multi-Format DVD Writer
	NVIDIA GeForce 8500GT VGA DVI Video Card
It seems weird that it freezes when loading hard drives??
Any feedback would be appreciated.
Thanks.

---

### Post by Pumalite on 2007-07-10
Have you guys tried the Alternate CD and install in Text Mode?

---

### Post by noob44 on 2007-07-11
Yes, I've tried the alternate CD (with full hope from what a few hardcore ubuntu users said) in text mode (also safe graphics) but the errors still the same and at the same point. Perhaps this is a problem with the SATA HDs and ubuntu 7.04 not being able to handle it properly. I hope they fix this soon. I need my linux on my new pc, I'm stuck with vista for now! :(

---

### Post by Pumalite on 2007-07-11
Deleted.-

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **kenevil said:**
> 
However, I always get the same error:

/bin/sh: can't access tty; job control turned off
(initramfs) _

Are you sure, you're using the cpu-correct version of the installer?

---

### Post by sneakyfox on 2007-07-11
Originally posted in 64-bit forum, but I tried the 32-bit image and got the same error.


I get the boot menu, select Install, and wait. The Ubuntu logo pops up with the progress bar. Suddenly the install exits and I'm left at a CLI with the following text: "cant access tty; job control turned off". 

Google told me this just means that booting failed. So I checked /casper.log and it says "mounting /dev/sda1 on /cdrom failed: no such device" over and over.

This also happens if select check CD from the boot menu.

The laptop is brand new with a Santa Rosa platform plus Nvidia 8600 GT graphics, SATA harddrive and PATA dvd-drive. More info about chipset: [http://www.intel.com/products/centri...sc_centrinoduo](http://www.intel.com/products/centri...sc_centrinoduo) (I asume i have the Mobile Intel® PM965 Express Chipset, since I have Nvidia graphics).

I have no idea what to do!

---

### Post by sneakyfox on 2007-07-11
Just tried installing with 32-bit text based installer, and it worked!

---

### Post by merco on 2007-07-11
I have exactly the same problem as noob44, the ubuntu installer has problem with sata and ide at the same time. I dont know how to fix this. Im going crazy of this for sure. But its not only ubuntu, i have tryied ubuntu,kubuntu,gentoo,mandriva,opensuse. I wasnt able to install just one of those. I have WD sata 400GB, ide dvd writer, intel core duo.

If there is anyone... pls help us. Thx, merco

---

### Post by Pumalite on 2007-07-11
Try a USB CD-DVD.

---

