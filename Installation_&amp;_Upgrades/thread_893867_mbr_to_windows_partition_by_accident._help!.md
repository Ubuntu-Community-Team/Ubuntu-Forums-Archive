---
title: "mbr to windows partition by accident. help!"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by reckless2k2 on 2008-08-18
setup:

sda1 - windows
sda2 - ubuntu 8.04

during the install, i goofed and installed the mbr to /dev/sda1. so now at the grub menu when i hit "windows" it puts me right back to the grub menu. 

i tried to boot off knoppix to at least access the drive but it won't let me. it gives me a ntfs partition mounting error. 

i tried to boot off a windows install disk thinking i could just run fixmbr and then fix everything but i keep getting BSOD just trying to load the disk. 

if i fix the mbr, i should be able to boot back into windows.

any help is appreciated.

---

### Post by wilbbe01 on 2008-08-18
Do you maybe have another windows disk to try?  fixmbr generally does the trick easily.  Also, I think supergrub might be of some help if you want to restore the windows bootloader.

---

### Post by caljohnsmith on 2008-08-18
If you installed Grub to sda1 and not sda like you say, then Grub was installed to the boot sector of your Windows partition. I don't think you want to use "fixmbr", because that will overwrite the master boot record (MBR) of your HDD with Windows XP MBR. If you do that you won't be able to boot anything, because your Windows partition will still be unbootable.

I believe what you really want to use is "fixboot", which will fix the boot sector of your Windows XP partition. Just boot up your Windows Install CD, go into the recover console, and run that command.

If you are getting a Grub menu at all on startup though like you alluded to, Grub should be in the MBR. So I'm assuming "fixboot" is all you need to solve your problem, but if you have problems getting your Grub menu, we can fix that too.

---

### Post by reckless2k2 on 2008-08-18
i'll try another windows boot disk but i think the issue is somehow bigger than that. i think the reason it won't boot from grub or able to access in knoppix is because the partition table is messed up. 

i'm pretty sure but even if i install grub to sda1 where windows is, it should've still booted. i'm not sure. well, now i'm thinking of it, probably not. 

anyway, knoppix can't access sda1 giving partition table errors. it sees that it's ntfs but won't mount it. grub will see it on boot but won't access it. 

i need some partition table repair help. i know the stuff is there but i can't access it anyhow. 

thanks for the quick response but i still need some help.
thanks.

---

### Post by caljohnsmith on 2008-08-18
Well first, please run that fixboot program so at least your Windows boot sector will be correct. So on startup are you able to boot into Ubuntu OK from Grub? If so, boot into Ubuntu, and if not, boot a Live CD and please post the output of:
```
sudo fdisk -lu
```
Also post the contents of your /boot/grub/menu.lst on the Ubuntu partition. And lastly, you could try doing a basic integrity check on the NTFS partition with the program "ntfsfix", which will help repair any basic NTFS problems. Just download and install:
```
sudo apt-get install ntfsprogs
```
Then run ntfsfix on your NTFS partition:
```
sudo ntfsfix /dev/sda1

```

---

### Post by reckless2k2 on 2008-08-18
i'm in knoppix now trying to run gparted. i ran 

```
sudo install-mbr
```

to whipe the mbr hoping that maybe a windows boot disk will work to run fixboot. at this point, it can't see anything. it won't mount sda1 because it's reporting a partition table error. 

erd commander won't see a windows partition which makes sense since it's messed up. 

here is the fdisk -lu

```
Disk /dev/sda: 255 heads, 63 sectors, 30401 cylinders
Units = sectors of 1 * 512 bytes

   Device Boot    Start       End    Blocks   Id  System
/dev/sda1   *        63 268001999 134000968+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary:
     phys=(1023, 239, 63) should be (1023, 254, 63)
/dev/sda2     365719725 484472204  59376240   83  Linux
/dev/sda4     484472205 488392064   1959930    5  Extended
Partition 4 does not end on cylinder boundary:
     phys=(1023, 14, 63) should be (1023, 254, 63)
/dev/sda5     484488270 488392064   1951897+  82  Linux swap

```
i'll try to see if i can run that other stuff from knoppix. 

i haven't booted or tried to even boot back into ubuntu at this point while gparted is running forever.

---

### Post by reckless2k2 on 2008-08-18
got a bigger issue kind of....gparted is not reporting sda1 as ntfs. ugh. so i can't use that to repair the partition table. ugh. how can i save my data? ugh. i'll try the other thing from 
 knoppix if it works

---

### Post by reckless2k2 on 2008-08-18
i'm getting a run chkdsk error with the ntfsfix gimmick.

---

