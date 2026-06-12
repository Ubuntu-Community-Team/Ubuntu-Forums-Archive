---
title: "Ubuntu 10.4 Installation on SATA 6Gb/s"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by babydanks on 2010-06-19
Hey guys,

Long time user of Ubuntu, but i've never had this problem. 

I just recently installed Ubuntu on my SSD partitioned with Win7. Everything worked fine. 

I decided to move my SSD from the SATA 3Gb/s port to the 6Gb/s port on my motherboard for better performance. Grub 2 is still recognized and Win7 boots properly. 

However Ubuntu will not boot after selecting it from Grub. I also tried to reinstall over the ext4 partition on my SSD with a live CD and it does not recognize my SSD, only my data drive.

I am lost. Is Ubuntu 10.4 not compatible with SATA 6Gb/s or am i just missing something?

Thanks.

---

### Post by ronparent on 2010-06-19
Is your ssd rated sata II or sata III?

---

### Post by babydanks on 2010-06-19
It is rated for SATA II. However, i know that plugging it into SATA III would not hurt anything. Grub 2 and Win7 still work...

I originally changed ports in the first place to avoid this annoying "HD not found" message from by bios because it always checked the SATA III ports before the SATA II.

I thought that SATA was all backwards compatible.

---

### Post by ronparent on 2010-06-19
The point is that you are gaining nothing else than avoiding the annoying message by plugging a sata II drive into a sata III port. SATA is backwards compatible in theory, but you may be encountering an unpredictable problem with timing or something. I would change the seek order in bios, if you can, to boot 1st from the slower port.

---

### Post by jr1400 on 2010-06-19
I am having the exact same problem as babydanks.  The only difference is that my harddrive is actually a SATA III drive and I am still having problems.  Windows XP x64 works perfectly, but Ubuntu requires me to plug my drive into a SATA II port on my motherboard.  It is somewhat upsetting.  I would appreciate any feedback and please explain most of your instructions as I am relatively new to linux.  Thank you.

---

### Post by ronparent on 2010-06-19
Just a thought. Try editing in 'rootdelay=90' to the grub menu boot line. If it is helpful you can make it permanent in /etc/default/grub.

---

### Post by jr1400 on 2010-06-20
please explain how this is done

---

### Post by babydanks on 2010-06-20
i believe you press "e" on the grub menu and edit the kernel line to say 'rootdelay=90' is that correct? i tried it. i still get the busy box saying that /dev/disk/by-uuid/# does not exist. and it gave up waiting on the device. same thing happened with 'rootdelay=1000'

---

### Post by jr1400 on 2010-06-21
It did not work for me either.  I got that busybox as well.

---

### Post by cinger on 2010-10-06
Had this problem also with 64bit 10.04, msi p55gd85 i7 870 and 6 g SATA hdd.

If anyone got it to work in their installation, post.

Related post: [http://ohioloco.ubuntuforums.org/showthread.php?t=1572830](http://ohioloco.ubuntuforums.org/showthread.php?t=1572830)
> **blueturtl said:**
> You have to understand that the interface speed  that is given (UDMA100, SATA 3 GB/s, SATA 6 GB/s) is just that, the  maximum speed the interface can transmit. The harsh truth is that in  hard drives the bottle necks lie in the mechanics rather than the  interface: you can't find a drive that can actually reach the maximum  speed of the interface. SATA 6 GB/s is futureproof I guess, but at this  point mostly just marketing. Two drives differing *only* in the interface will have equal performance.


---

### Post by isaacahloe on 2011-01-23
same deal here.. i couldn't even get ubuntu disk to see the drive to install, i had to hook up to the other ports to install.

Natty seems to work brilliantly with them though.

---

### Post by heronbas on 2011-09-02
I had the same problem as this after building a new computer a couple of months ago. 

I had installed a bluray drive instead of a DVD drive and had connected the bluray drive via the 6Gb/s Sata-3  sockets on the motherboard. Both Ubuntu and WindowsXP installation DVD's would not install with Ubuntu displaying the error message: 'unable to find a medium containing a live file system', but the Windows7 DVD installed OK. 

Ubuntu successfully installed from the DVD after changing the 'PCH Sata Control Mode' setting to 'AHCI' in the motherboard bios. (Note: you have to change a registry setting in Windows before changing this BIOS setting if you have Windows installed - see [http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html](http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html))

---

### Post by Quackers on 2011-09-02
What sata controller are you using? I know that at one time the Marvell controller was not supported.
I don't know if that's still the case.

---

### Post by Neilrahc on 2012-12-09
> **heronbas said:**
> I had the same problem as this after building a new computer a couple of months ago. 

I had installed a bluray drive instead of a DVD drive and had connected the bluray drive via the 6Gb/s Sata-3  sockets on the motherboard. Both Ubuntu and WindowsXP installation DVD's would not install with Ubuntu displaying the error message: 'unable to find a medium containing a live file system', but the Windows7 DVD installed OK. 

Ubuntu successfully installed from the DVD after changing the 'PCH Sata Control Mode' setting to 'AHCI' in the motherboard bios. (Note: you have to change a registry setting in Windows before changing this BIOS setting if you have Windows installed - see [http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html](http://www.sevenforums.com/tutorials/61869-ahci-enable-windows-7-vista.html))

Thanks, heronbas - I was glad to come across your note. Setting BIOS to AHCI also solved getting DOS to boot on a 6Gb/s Sata-3 drive.

---

