---
title: "Installer boots from CD, then can't detect CD drive"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by vodsonic on 2010-02-21
I'm using the Ubuntu 9.10 alternate install CD in an external PATA USB CD drive to try to install Ubuntu on a ThinkPad X60.

The installer boots but then very quickly gets to a stage where it complains that, "No Common CD-ROM drive was detected". It asks you to point out the drive or load or select drivers, but there aren't any drives or drivers to choose. I brought up another console, and looked in /dev, but there isn't anything there that resembles a CD drive.

Apparently this has been a [[COLOR="Red"]known bug for about two years now[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614). A couple of [[COLOR="Red"]other[/COLOR]](http://ubuntuforums.org/showthread.php?t=964904) [[COLOR="Red"]threads[/COLOR]](http://ubuntuforums.org/showthread.php?t=1180234) here document the same problem and suggest all kinds of different fixes, none of which worked for me.

I tried 

$ modprobe ide-scsi

But it can't find the module.

I followed the instructions [[COLOR="Red"]here[/COLOR]](https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614/comments/8), found the drivers on a working system, and put them on a thumbdrive. However, when I mount it:

$ mkdir /tmp/drive
$ mount /dev/sdc1 /tmp/drive

Mount fails due to an "invalid argument," with two different USB drives that work just fine on other systems. When even mount doesn't work, I feel like I've got both hands tied behind my back.

Does anyone have any suggestions for how I can correctly implement the above command-line fixes? I'm not sure what I'm doing wrong. I've installed different Ubuntus probably a dozen times over the years, and haven't gotten stuck this badly since somewhere around version 4.

The other question I have is whether this problem is specifically related to the fact that my external USB CD drive has a PATA interface. If I go out and buy or borrow a SATA USB CD drive, is this problem likely to go away?

---

### Post by ajgreeny on 2010-02-21
Try
```
$ sudo mkdir /tmp/drive
$ sudo mount /dev/sdc1 /tmp/drive
```
If you were using a live CD you would need sudo; I'm not sure about the Alternate Install CD, but it's got to be worth trying.

---

### Post by vodsonic on 2010-02-22
> **ajgreeny said:**
> Try
```
$ sudo mkdir /tmp/drive
$ sudo mount /dev/sdc1 /tmp/drive
```
If you were using a live CD you would need sudo; I'm not sure about the Alternate Install CD, but it's got to be worth trying.

In the shell, using the alternate install CD:

```

~ $ sudo mkdir /tmp/drive
~/bin/sh: sudo: not found
```

Does anyone know if this bug is unique to USB PATA drives? I haven't run across any mention of it happening with a SATA drive. Might the problem evaporate if I was to get a USB CD drive with a SATA interface inside? 

I have a USB-SATA adapter, which I connected to a bare SATA CD drive, but I experienced spontaneous reboots before I ever got to the problem stage.

The live CD boots OK in the old PATA external CD drive. Unfortunately, I need some options which only the alternate install disc has.

What should I try next?

---

### Post by vodsonic on 2010-02-23
The problem with mount was that it wanted me to specify the filesystem type.

```

$ mount -t vfat /dev/sdb1 /tmp/sdb1
```

This successfully mounts the USB flash drive that contains the drivers I want to try to load.

```

$ insmod pata_opti.ko
```

This doesn't return any error messages, so I assume it's loaded the driver.

However, when I return to the installer, it still can't find a CD-ROM drive. There's nothing at /dev/sr0, like the [instructions I was following]("https://bugs.launchpad.net/ubuntu/+source/cdrom-detect/+bug/195614/comments/8") suggest.

Is there another driver I might go looking for on my working system that might support a USB PATA CD-ROM drive?

---

### Post by vodsonic on 2010-02-24
I have alternate install discs for Ubuntu 8.04.2 and 9.04. Neither of these have any trouble finding the CD drive with my current setup like the 9.10 alternate install disc does.

I compared the output of ```
modprobe -l
```

while running different installers, and found a couple of interesting things. 

The 8.04.2 installer includes these drivers:

/kernel/drivers/cdrom/cdrom.ko
/kernel/drivers/scsi/ide-scsi.ko

Neither of them appear in the modprobe list in the 9.10 installer.

However, still in the 9.10 installer, after I

```
insmod pata_opti.ko
```

with no error messages, the list I get from 

```
modprobe -l
```

*still* does not include the pata_opti.ko driver.

However, pata_opti.ko does not appear in the 8.04.2 driver list *either*, which makes me think it isn't the driver I need.

I think my next step is to get these drivers:

/cdrom/cdrom.ko
/scsi/ide-scsi.ko

from a working system, and insmod them while running the problematic 9.10 installer. 

Can anyone tell me how to make sure these drivers are really being inserted?

If I 

```
insmod ide-scsi.ko
```

and get no error messages, should
```

modprobe -l | grep ide-scsi
```

give me a positive hit?

---

### Post by billylcm on 2010-03-31
Hi vodsonic,

I have same problem as you which the installer couldn't detect any ide devices on my old laptop Toshiba 320CDS (over 10 years old), I'm not surprised, all newly release linux distribution (Fedora Core 12, Puppy Linux, CentOS...etc) with kernel newer than 2.6.20 don't support my laptop anymore and I couldn't figure out till I saw your post.

I must say thanks for your research and posting, I followed the steps you mentioned, it didn't work with either **pata_optidma.ko** nor** pata_opti.ko** modules, however when I load **pata_legacy.ko** module, it works.

So what I'm thinking is maybe you can load few more modules and check /dev see if any new block device has been added or issue a dmesg command. I don't have a live cd with me, I copied modules from a working Ubuntu 9.10 system, I think it should be the same with the live cd. Hope Ubuntu develope team can add these module, at least the alternate install cd, people usually install it on aged machine.

Good luck ;)

Key words: ide cannot detected no hda toshiba 320 cds kernel module recompile

---

### Post by jboris on 2011-01-04
Hi guys. I have the same issue with my HP DL 180. The desktop version of 10.04.1 LTS loads just fine so I tried to reinstall using the Server version (64 bit). Same issue. Loads from the CD but when it looks for the files it says "No Common CDROM detected" Under the desktop version the cdrom was mapped to /dev/sr0 but that doesn't get loaded. 
When you guys tried to do the install did you change any of the settings. I get a menu to choose from at the start with a bunch of install options if I hit f6 but I can't find out what any of these options mean.
 
Were you ever succesful in getting the system to install?
 
 
########
Solved.  Hit F6 at main install screen and selected options that caused the installer to search the entire SCSI and ATA bus for CD.

---

