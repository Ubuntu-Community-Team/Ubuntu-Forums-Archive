---
title: "Trying to install ubuntu or lubuntu off of new cds on old computers"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by Adrian_Moncloa on 2016-02-17
Hello, I am trying to install ubuntu 14.043 and lubuntu 14.04.3 on a dell dimension 2400 and a dell dimension 1100 both currently running xp pro 32 bit (both machines are almost 10 years old)

The problem is that the machines do not boot off the isos I made.  I think I need to burn the isos on older cd's and am not sure which kind to get.  Both machines boot off the Windows XP installation CD.  Also, both the Ubunto and Lubunto isos have worked on other machines.

Thanks for any help as which type of CD to get.

---

### Post by lisati on 2016-02-17
Some of the newer releases of Ubuntu won't fit onto a CD, you might need to make a bootable DVD instead.

---

### Post by Adrian_Moncloa on 2016-02-17
I do not care so much if I have an older version of ubuntu or lubuntu.  My concern is finding a cd that these old computers will boot from. If they do not boot off a CD I doubt they will boot off a DVD.

---

### Post by lisati on 2016-02-17
If you're going with regular Ubuntu 14.04, it won't fit on a CD, you will have to use a DVD. I'd recommend looking into a lighter weight version. 

The ISO for [Lubuntu 14.04]("http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/") *will* fit onto a CD and might work better with older hardware. 

There's also [Xubuntu]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/"), but the ISO for 14.04 won't fit on your typical CD.

---

### Post by grahammechanical on 2016-02-17
We are assuming that as those machines were running Windows 32bit XP you have downloaded 32bit ISO images. Now, it just maybe that they have a 64 bit CPU but it could also be that they have a 32 bit CPU. And that would be one reason why the ISO images do not boot.

Are there any error messages? Or, do the machines simply load into XP? As for which CD discs to use that all depends in the capabilities of the CD drives. another factor could be the method that you are using to create those Cds with Ubuntu on it. The ISO images need to be burnt on to the disc and not copied on to it.

Regards.

---

### Post by MAFoElffen on 2016-02-17
+1 with grahammechanical

Considering different versions what people consider as being "old."
Your 1100 has a pentium 4 2.8 GHz and came with 256MB of RAM. It maxes out at 1GB of RAM. It is a single core CPU with only a 32bit data width. CPU is PAE.
Your 2400 has a celeron 2.4 GHz and cam with 256MB of RAM, It maxes out at 1GB of RAM.  It is a single core CPU with only a 32bit data width. CPU is PAE.

So, if stock, it will both fail trying to boot even Lubuntu, until you up the memory. (They might boot Puppy LTS.) They both came stock with CDROM drives. They both will accept a DVD drive. They both are basically the same CPU (Intel Northwood builds). They both will only run a 32 bit OS.

>>> The Ubuntu Mini ISO is still small enough to fit on CD...But you really need to upgrade the RAM to enjoy it. Both will max out with 512MB x 2 chips (each machine)

---

### Post by sudodus on 2016-02-18
Your computers will probably boot from a USB pendrive. I have a 12 year old Dell desktop computer with similar specs, and it is willing to boot for example Lubuntu from USB. See this link and links from it.

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

But as MAFoElffen wrote, it is important to have enough RAM. Lubuntu needs at least 512 MB to work, and 1 GB to work well.

There are more details about old computers in the following links,

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640") and [General tips, that may help]("http://ubuntuforums.org/showthread.php?t=2130640&p=13311591#post13311591")

---

### Post by mörgæs on 2016-02-18
> **grahammechanical said:**
> We are assuming that as those machines were running Windows 32bit XP you have downloaded 32bit ISO images. Now, it just maybe that they have a 64 bit CPU but it could also be that they have a 32 bit CPU. And that would be one reason why the ISO images do not boot.



No, a 32 bit ISO will boot on both 32 and 64 bit processors.

---

### Post by Adrian_Moncloa on 2016-02-23
The Dell Dimension 1100 has 512 MB of Ram, 2.53 GHz Celeron so Lubuntu should work.  I just cannot get it to boot from the (tested) Lubuntu cd iso (32 bit).  I made a floppy disk that has PLOP to be able to boot from USB drive but the BIOS says  Floppy Device (not installed). Also there is no USB option listed in the BIOS.  I also bought a portable CD-ROM drive but the BIOS does not see it. There are no error messages. Any suggetions are welcome.

---

### Post by mörgæs on 2016-02-23
With only 512 MB of memory I recommend the alternate Lubuntu ISO.

---

### Post by sudodus on 2016-02-23
Sometimes a USB pendrive is not recognized as USB but as a disk among the hard disk drives. (Both are mass storage devices, and managed the same way).

See this link, that tries to describe how to do it in some computers,

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

particularly this sentence:
> Note: with some motherboards you have to select 'hard disk/USB-HDD0' to choose the USB flash disk. It may work like this because the system sees the USB drive 'a mass storage device' as a hard disk drive, and it should be at the top of the boot order list. 

---

