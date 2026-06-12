---
title: "Altering MBR to recogize another Drive"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by lanark on 2008-10-21
I have Ubuntu installed with Vista and dual boot. I want to add my old IDE drive with w2k on it and boot to either w2k, vista or ubunta. When I connect the drive and boot the computer the only OS available to me is w2k.  I have tried Supergrub, but it doesn't work allow me to boot to Vista.

---

### Post by Fire_Chief on 2008-10-21
Is the drive with Vista and Ubuntu an IDE drive also or is it something else (SATA/SCSI)?

You should check the boot order if it is a SCSI or SATA to make sure that it is looked at first for booting.

If it is also an IDE drive, then make sure it is the master and not the slave on the IDE bus (look at the jumpers on each drive and set accordingly).

That should make the computer boot from the MBR on the Vista/Ubuntu drive first. Then you can change Grub or BCD to boot the W2K installation on the second drive.

On a side note, was that W2K install from this computer or was it on another computer? I ask because you may run into some hardware changes that the Windows install has trouble with if it is from a different PC.

Cheers!

---

### Post by caljohnsmith on 2008-10-21
So before you boot your W2K drive, can you successfully boot your Vista + Ubuntu drive, and do you get a Grub menu on start up to select between either Vista or Ubuntu? If yes, then probably the easiest solution for your situation is to make sure your BIOS is set so that the Vista + Ubuntu drive is booted before the W2K drive; i.e. your Vista + Ubuntu drive boots on start up regardless of whether the W2K drive is attached. Then you can simply add an entry in your Grub menu to boot the W2K drive. 

If you would like to do that, please first post:
```
sudo fdisk -lu
```
And also confirm whether you can boot your Vista + Ubuntu drive even if the W2K drive is attached. :)

---

### Post by lanark on 2008-10-21
The old drive I am adding is an IDE, the other drive is a SATA...with the IDE drive installed, the computer will only boot to the IDE. I get an error 6 message if I ask it to boot to the SATA. If I remove the IDE drive , Ubuntu or Vista will boot fine. I have tried telling the CMOS to boot to the SATA drives first but no go.

---

### Post by lanark on 2008-10-21
Have set the ubunta sata drive t oboot 1st  but with the ide drive installed, the boot loader won't work, I get an error 6 message and stops booting...w2k will boot fine if I set the ide with w2k on it to boot 1st but, I can't then get to vista or ubunta

---

### Post by Fire_Chief on 2008-10-22
I suspect that since the IDE drive is being recognized first, it's now being assigned the /dev/sda position and the SATA drive is now at /dev/sdb. This is creating a problem for the bootloader where it is trying to reference partitions on /dev/sda that are not present.

You probably need to redo the bootloader (assuming GRUB) configuration to reference the drives properly. I would boot the system off of the Ubuntu CD with both drives installed and edit the /boot/grub/menu.lst file. Change the references for the Ubuntu and Vista selections to look at hd(1,*) instead of hd(0,*). You could also add the boot entry for the W2K system so it will appear in the boot menu as well.

The entry for W2K will look something like this```
title  Microsoft Windows 2000 #An entry for a Windows installation
root   (hd0,0)
makeactive
chainloader +1
```

Be sure to make a backup of the file before making changes just in case you need to revert back.

You'll need to re-run grub install to change the MBR on the IDE disk.```
grub-install /dev/sda
``` It should detect the configuration and adjust the MBR for you.

Cheers!

---

### Post by lanark on 2008-10-23
I have now messed up things completely. I can't boot to Vista or Ubuntu. I get an error 17 message  cannot mount selected partition when I ask for linux and errot 13 message Invalid or unsupported executable format when i ask for Vista. At terminal( I am using a live CD) if I type command:  sudo gedit /boot/grub/menu.lst   I get a blank menu.lst page. Help

---

### Post by lanark on 2008-10-23
sudo fdisk yeilds this:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb479828d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   605056094   302528016    7  HPFS/NTFS
/dev/sda2       605056095   625137344    10040625    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7a12df6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     9767519     4883728+  83  Linux
/dev/sdb2   *     9767520    10747484      489982+  82  Linux swap / Solaris
/dev/sdb3        10747485   625137344   307194930   83  Linux

I can't seem to find a menu.lst except when I ask for sudo  gedit /root/grub/menu.lst I jsu get a blank page.

---

### Post by Fire_Chief on 2008-10-23
Based on the fdisk listing you posted...did you already have 2 hard drives when booting both Ubuntu and Vista? Did adding the IDE drive mean you now have 3 separate drives in the system? 

If so, then I'm sorry to have steered you wrong with the previous instructions.

So that we can get a good understanding of the drives and which one has what OS, please put the W2K drive in the system with the Ubuntu and Vista drive(s). Then repost the fdisk info for all drives seen by the live cd like you did before.

Cheers!

---

### Post by lanark on 2008-10-23
> **Fire_Chief said:**
> Based on the fdisk listing you posted...did you already have 2 hard drives when booting both Ubuntu and Vista? Did adding the IDE drive mean you now have 3 separate drives in the system? 

If so, then I'm sorry to have steered you wrong with the previous instructions.

So that we can get a good understanding of the drives and which one has what OS, please put the W2K drive in the system with the Ubuntu and Vista drive(s). Then repost the fdisk info for all drives seen by the live cd like you did before.

Cheers!
This is the fdisk report with the ide drive installed. Yes, there are 3 drives in the computer
2 sata drives and 1 ide
Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *          63    58621184    29310561    c  W95 FAT32 (LBA)



Disk /dev/sda: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xb479828d



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   605056094   302528016    7  HPFS/NTFS

/dev/sda2       605056095   625137344    10040625    7  HPFS/NTFS



Disk /dev/sdb: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x7a12df6c



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *          63     9767519     4883728+  83  Linux

/dev/sdb2         9767520    10747484      489982+  82  Linux swap / Solaris

/dev/sdb3        10747485   625137344   307194930   83  Linux

ubuntu@ubuntu:~$

---

### Post by Fire_Chief on 2008-10-24
Ok, so here is what the grub menu.lst *should* look like...

```
title	Windows 2000
**root		(hd0,0)**
savedefault
makeactive
chainloader +1

title           Windows Vista 
**rootnoverify    (hd1,0)**
savedefault
makeactive
chainloader +1

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd2,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=*whatever your UUID is...should alreay be present* ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
**root		(hd2,0)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=*whatever your UUID is...should alreay be present* ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
**root		(hd2,0)**
kernel		/boot/memtest86+.bin
quiet
```

A few of the details on the Linux entries will be different but that's okay.

After editing the menu.lst you'll need to reinstall GRUB to the MBR of the IDE drive
```
sudo grub-install /dev/hda
```That should spit out all the recognized boot entries in a list with an asterisk by the default selection. If that looks good, then reboot and hopefully see the boot menu!

Here is a very thorough page on GRUB configuration and installation.
[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

Cheers!

---

