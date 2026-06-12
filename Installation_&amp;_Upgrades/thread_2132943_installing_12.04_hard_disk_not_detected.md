---
title: "installing 12.04 hard disk not detected"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Philip Marlowe on 2013-04-06
[COLOR=#101010][FONT=Ubuntu]i'm trying to install 12.04 on my brand new pc[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]hard disk info: [/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]WESTERN DIGITAL CAVIAR BLUE 500 GB 3.5'' 720RPM 16MB SATA3 WD5000AAKX[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]created usb with ubuntu iso:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]boot ok, [/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]i choose "try ubuntu": everything's ok, desktop appears etc...[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]then choose "install ubuntu": no way... it says no enough space in the disk[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]typing on terminal: sudo fdisk -l gives me just the usb drive information, hard disk like it doesn't exist![/FONT][/COLOR]

[FONT=Ubuntu, 'Lucida Grande', 'Trebuchet MS', Verdana, Helvetica, Arial, sans-serif][COLOR=#101010]while BIOS can see hard disk for sure: it's in the boot option list like PO: WDC500AAKX-0BERMA0 (476940MB) it's him![/COLOR][/FONT]

[COLOR=#101010][FONT=Ubuntu]other hardware infos:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]CPU: AMD A4 5300 2-CORE 3.4GHZ SOCKET FM2 1MB HD7480D 65W BOXED[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]MOTHERBOARD: ASUS F2A85-M LE SOCKET FM2 AMD A85X DDR3 SATA3 USB3 MATX[/FONT][/COLOR]

[FONT=Ubuntu, 'Lucida Grande', 'Trebuchet MS', Verdana, Helvetica, Arial, sans-serif][COLOR=#101010]any suggestion??? thanks[/COLOR][/FONT]

---

### Post by darkod on 2013-04-06
Try another port, or another sata cable, just in case.

If the disk never had partition table on it, not sure if you need to write one first. What does parted output in live mode:
```
sudo parted -l
```

---

### Post by Philip Marlowe on 2013-04-06
other port, other table: 
i don't fell like open pc case, i'm not expert, hope to solve other way, but if you think it's a good try i'll do it.
sudo parted -l
gives me info of the flash disk i used for booting
1 partition of 4037MB
/dev/sda

---

### Post by Bashing-om on 2013-04-06
Philip Marlowe;
> [COLOR=#101010][FONT=Ubuntu]i'm trying to install 12.04 on my brand new pc[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]
Pops to mind - as we see a lot of it here - , is UEFI enabled in bios ??

[/FONT][/COLOR][INDENT=2][COLOR=#101010][FONT=Ubuntu]just a thought

[/FONT][/COLOR]
[/INDENT]

---

### Post by darkod on 2013-04-06
When you say brand new, is it a computer you assembled yourself or you bought it? If you bought it, does it have windows preinstalled?

If there is no OS on it right now, go into BIOS and double check whether the SATA Mode setting is set to AHCI. Also, disable UEFI boot if there is an option for that.

Even though bios shows the disk it doesn't seem detected by ubuntu at all. Sometimes boards have sata ports from two different controllers and it can work on some ports but not on other, depending which controller is connected to which sata ports.

It's not even reported as device. Either the disk is bad/faulty, or the controller is not recognized which would be very rare.

---

### Post by grahammechanical on 2013-04-06
If the disk has Microsoft Windows on it and the installer says > [COLOR=#101010][FONT=Ubuntu]it says no enough space in the disk[/FONT][/COLOR] then there could be a couple of possible reasons. Windows is using up the 4 primary partitions allowed or Windows is using the disk as Dynamic disks which the installer cannot read. If it is Windows 8 that you have then you will need Ubuntu 12.04.2 or 12.10 or 13.04. These versions will install on a machine with secured boot enabled but 12.04 and 12.4.1 will not. You need to disable secure boot and also fast boot for good measure.

Regards.

---

### Post by darkod on 2013-04-06
But that still doesn't explain why fdisk or parted in live mode don't show the disk as present. The installer might also ignore a disk with raid meta data on it, but at least Gparted and parted in live mode can see it.

Regardless how many partitions you have or free space, it should at least show it in live mode. It's another thing whether it will allow you to install on it, but it has to show it.

---

### Post by Philip Marlowe on 2013-04-07
hi guys thank you everybody, i'm not so expert (and a bit lazy too...) to easily check all you say. i'm starting to follow [this ehow]("http://www.ehow.com/how_6008732_create-bootable-usb-fdisk.html") to solve my problem, i'll let you know!

---

### Post by Philip Marlowe on 2013-04-07
but i can easily answer to this: components are brand new and assembled by the eshop where i bought it, absolutely no windows installed.

---

### Post by darkod on 2013-04-07
Sounds like you will need to take it back under warranty so they can check it out. Or ask them for advice first.

The disk has to be shown. Otherwise there is something wrong with the machine.

---

### Post by Philip Marlowe on 2013-04-08
i tried with gparted: nothing...
i tried with a widows 8 installation: nothing...
only BIOS can see that disk, i'll contact the guys who sold me the assembled pc...

---

### Post by Philip Marlowe on 2013-04-12
onow hd is ok: my uncle changed something on the bios settng. something i'm not able to explain. ubuntu does bad.... it often crashes,apps crashano, system out of service when you go to audio setting... is this normal?

---

### Post by darkod on 2013-04-13
Of course it's not normal. You have some issues but I'm not sure it will be easy to detect. Like the problem with the disk, I don't understand what it was and what option in the bios is changed now. It might be hardware related.

Did the installation of ubuntu go fine, without any errors?

You can also try making a new cd on low speed, if you haven't done that so far. The cd for installing an OS should never be burned at high speed, not more than 8x or 10x. Butning at high speed leave small errors even if it says the burn has been verified.

---

### Post by Philip Marlowe on 2013-04-13
problem soved changing bios setting!!!

---

### Post by sriny1512 on 2013-04-30
I too have the same problem. When installing Ubuntu 12.04.1 LTS via CD. The installer cannot find the 80GB SATA Hard disk I have in my dekstop. I tried several ways to make the installer detect the hard drive, 
1. Used GPARTED and deleted the partitions on the hard drive before installing, No luck. 
2. Using GPARTED, created ext4 root partition and swap partition. After this I came back to install 12.04.1. The installer cannot mount the hard disk at the "Installation Type" window though it finds the har disk as "/dev/sda" in "Device for bootloader installation".

I have a doubt. Is the installer directly jumping to "boot loader installation option. 
Anyone, please help to solve the problem. 

For reference, the output of "fdisk -l" command is 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f289.

---

