---
title: "Booting Vista after Gutsy installation"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by bayowar on 2007-08-26
I recently installed the latest Gutsy on my Vista machine to check out all the new features. Once 
installed, grub didn't show a windows entry. No big deal, I thought, and manually added it to the 
menu.lst:

```
title           Windows Vista
root            (sd0,6)
makeactive
chainloader     +1
```

Here's the fdisk -l output, for reference (sda7 is the windows partition, hda7 is gutsy):

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ec5652f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sda5               2       17226   138359781    7  HPFS/NTFS
/dev/sda6           17227       27724    84325153+   7  HPFS/NTFS
/dev/sda7           27725       30401    21502971    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe961e961

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/hda5            2464        9729    58364113+   7  HPFS/NTFS
/dev/hda6            1148        1390     1951834+  82  Linux swap / Solaris
/dev/hda7               1        1147     9213183   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec70ec6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS
```

The entry shows up in grub, however it keeps giving me an error 23 when I try to boot it. To make things
worse not even the startup repair tool on the Vista disk seems to recognize the previous installation.

In ubuntu all seems well, the drive shows up in /media (named "sda7", it should be called "Vista") and
still contains all the files.

At one stage I installed gparted and added a boot flag, which resulted in a crash. After a few failed 
attempts at booting I removed the flag, again cuasing a gparted crash. Could that be the reason why
it's acting up?

Is there any other way to boot Vista? Right now I wouldn't mind losing gutsy and going back to the 
original bootmanager, if that's what it takes.

---

### Post by ddrichardson on 2007-08-27
First off, seeing as you can access the drives from Ubuntu - I'd back up your Vista stuff. You can use [System Rescue CD]("http://www.sysresccd.org/Main_Page") (man, I'm forever pluggin this distro) to image the drives, before you cause any other problems ;-)

The bootable flag isn't needed when the bootloader is on the MBR, only if it isn't.


After backup, [Super Grub Disk]("http://supergrub.forjamari.linex.org/") may be a good place to start.

Just a quick one - is Windows always sda7? I only ask becasue I have seen problems with sda and hda configs in the past. There is a bios option relating to how SATA is handled that often makes Windows think there is no drive available on SATA at installation.

---

### Post by davidjmayo on 2007-08-27
> I recently installed the latest Gutsy on my Vista machine to check out all the new features. Once installed, grub didn't show a windows entry. 
Same here with W2K and Gutsy
my thread [http://ubuntuforums.org/showthread.php?t=535456](http://ubuntuforums.org/showthread.php?t=535456)
I haven't had any replies (but it's not an issue for me) but now it isn't a one off

Could you give me info as I may end up reporting this
I used Gutsy Tribe5 Alternate CD
What about you?
Any errors? For me it just didn't pick up W2K during the Grub install but found Kubuntu
7.04.

Sorry, I can't help 
Anyone else seen this?
Let me know in my thread
Thanks

BTW Gutsy Tribe4 DIDN'T have this problem

---

### Post by Gremlinzzz on 2007-08-27
Tribe releases are for developers and testers only, do not use them if you need a stable system
[http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html](http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html)

---

### Post by logos34 on 2007-08-27
> **bayowar said:**
> 
```
title           Windows Vista
root            (**[COLOR="Red"]s[/COLOR]**d0,6)
makeactive
chainloader     +1
```
...

Is there any other way to boot Vista? Right now I wouldn't mind losing gutsy and going back to the 
original bootmanager, if that's what it takes.

The letter in red above may be the problem--grub uses **'hd_' **for all disks, sata, pata, usb...

Try

**root (hd0,6)**

or
[B]
rootnoverify (hd0,6)[/B]

---

### Post by MQMike on 2007-08-27
Agree.
sda7 = (hd0,6).

With Vista, best to use the rootnoverify form:

rootnoverify (hd0,6)

just as the poster before me has said.

---

### Post by Pumalite on 2007-08-27
With Vista and any kind of chainload.

---

