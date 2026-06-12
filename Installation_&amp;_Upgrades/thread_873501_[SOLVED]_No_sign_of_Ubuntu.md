---
title: "[SOLVED] No sign of Ubuntu"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by jeepers on 2008-07-29
Hi all,

I installed ubuntu 8.04 on a HDD of its own, the install went O.K. ( I selected the whole drive option, then selected the appropiate drive). I have Vista Ultimate installed on a seperate drive.

When Ubuntu had finished installing it re-booted, and went straight into Vista (like normal) with no option of a boot menu to select Ubuntu.

My BIOS recognises that the drive is there (Obviously vista doesnt)  so how am i supposed to boot into Ubuntu.

I just selected all the defaults when installing.

My specs:

C2D 6600
Palit GT7300 Sonic
Samsung 203B
120Gb IDE HDD (Vista)
250Gb SATA (Movie)
80Gb IDE (Ubuntu)
Vista Ultimate
2Gb DDR 667

cheers

---

### Post by PmDematagoda on 2008-07-29
Perhaps the Master Boot Record(MBR) is being protected by the BIOS, in which case Ubuntu couldn't install GRUB onto it, try entering the BIOS and see if such an option is there, if so, disable it. After disabling it, try and use the [Super GRUB Disc]("http://forjamari.linex.org/frs/download.php/1014/super_grub_disk_0.9730.iso") to try and install GRUB onto the MBR and see if you can boot Ubuntu then.

---

### Post by jeepers on 2008-07-29
O.K. I fixed the problem, When i chose all the defaults during the install, Grub was put on the wrong partition, i went to the advance section and found where Vistas bootloader was and installed grub there.

Cheers

---

### Post by jeepers on 2008-07-29
> **jeepers said:**
> O.K. I fixed the problem, When i chose all the defaults during the install, Grub was put on the wrong partition, i went to the advance section and found where Vistas bootloader was and installed grub there.

Cheers

I jumped the gun...i can boot ubuntu but not Vista, so i guess i shouldn't have put Grub where vistas bootloader is.

Can someone give me a hint as to where i should put the Grub boot file so it picks up both Vista and ubuntu.

cheers

---

### Post by karatekid on 2008-07-29
i think you have installed grub on your vista partition.so you have wiped out vista bootmanager.
as far i understand can you should first restore your vista bootloader back to your vista partition (using the vista DVD) and then install grub on the MBR and the linux drive(dont install grub on your vista partition).

---

### Post by jeepers on 2008-07-29
i'm now using the Super GRUB disc to boot, at least its not overwriting my Vista bootloader. this is the output from fdisk -l

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2a533ffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7b89488

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris


I really want to use GRUB to boot and not a disc, so where do i install GRUB so that i can boot both Vista and ubuntu.

cheers

---

### Post by PmDematagoda on 2008-07-29
When you said that you couldn't boot Vista, was it that Vista wouldn't boot at all even though there was an entry for it, or was it that there wasn't an entry for Vista in the GRUB menu at all?

---

### Post by jeepers on 2008-07-30
Yes there was an entry for it...but when i selected it i got the "Bootmgr missing" dialogue, so i'm guessing GRUB overwrote the vista Bootmgr...from memory GRUB was installed on hd0.

heres the menu.1st entries

# ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5da5bc25-127c-4cd2-ba6d-553533320186 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5da5bc25-127c-4cd2-ba6d-553533320186 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5da5bc25-127c-4cd2-ba6d-553533320186 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=5da5bc25-127c-4cd2-ba6d-553533320186 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


cheers

---

### Post by karatekid on 2008-07-30
as already pointed out you will have to first restore vista bootmanager.
use vista DVD or the vista recovery disc.
Google it to find out the steps, there are plenty of tutorials on the net.
once you are through this you can easily restore GRUB.

---

### Post by jeepers on 2008-07-30
I have already restored the Vista bootmgr..if i reinstall GRUB it will just overwrite the Vista bootmgr again. i need to know where to put GRUB so it doesn't overwrite vistas bootmgr. because it looks like the default one in menu.1st is the one doing the damage so to speak.

cheers

---

### Post by karatekid on 2008-07-30
so now your vista installation is working just fine???

you have to install your grub in the MBR and ubuntu partition.
```

grub
root (hd2,0)
setup(hd0)
quit
exit

```
this should work

---

### Post by jeepers on 2008-07-30
O.K. I got a Terminal and did sudo grub, then the root (hd2,0) hit enter, did the setup (hdo) hit enter and got "error 17 cannot mount selected partition"

cheers

---

### Post by karatekid on 2008-07-30
are you able to access all your hard disks through ubuntu??
i mean are they all mounted???

---

### Post by jeepers on 2008-07-30
Yes i can see and access all my drive I.E. my Vista drive and my Downloads drive, all are seperate drives.

Jeez if i can get this GRUB working, then i'll be a happy camper, as i have got my sound working and both my printers are working, i can even scan using Xsane.

cheers

---

### Post by karatekid on 2008-07-30
this should help
[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

---

### Post by jeepers on 2008-07-30
Well after reading about error 17 and looking at some of the links there, There was one link to a program called EasyBCD, so i downloaded and installed it. 

Ran the program, it has an Linux option, so i added the option Neo-Linux (default) and ticked the "Grub is not installed to the MBR" and bingo I'm dual booting both Vista and Ubuntu from the Vista Boot manager.

I would suggest if anyone else is having problems with Grub  to try this application. It is the simplest method of Dual-Booting that i have yet seen.

cheers

---

### Post by karatekid on 2008-07-31
EasyBCD was always an option, but you seemed to be keen on using GRUB as your default bootloader so i didnt mention it.

---

