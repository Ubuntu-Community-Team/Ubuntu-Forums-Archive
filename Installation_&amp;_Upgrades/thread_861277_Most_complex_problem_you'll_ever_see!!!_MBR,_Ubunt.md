---
title: "Most complex problem you'll ever see!!! MBR, Ubuntu, XP"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by renegaide on 2008-07-16
First of all, I'm a complete noob. I've always been able to figure out how to get out of the messes I got myself into through posts on this forum, but this time I have a feeling I'm in deep ****, so I really need you guys' help!

I started out quite successful in my dual ubuntu/XP installation endeavor, so at some point I decided to install Fedora just for the kicks. That didn't work out well, so I ended up having to use that evil FIXMBR + FIXBOOT combo. I was able to get into XP, BUT, I was never able to successfully reinstall ubuntu and XP.

As a matter of fact, I might have done so many [FIXMBR + FIXBOOT] at this point, that my BIOS does recognize all of my HDs, but during the Windows installation only my IDE drive is detected (I also have 2 SATAs), and whenever I try to install ubuntu, I'm getting errors on those drives that say they are unmountable. I'm figuring I must have done something really nasty to the partition table or MBR, as I did play quite a lot with the SuperGrub disk too.

Therefore, at this point I only have my XP installed and not being able to recognize my other 2 HDs, a Ubuntu Live CD I can use to get into the Ubuntu environment, and the willingness to get those two bad boys working side by side once again. 

If you could help me I would be most grateful! (and I bet this thread will help lots of people in the future, as it probably involves solving few different issues) :D

---

### Post by Pumalite on 2008-07-16
Post:
sudo fdisk -lu

---

### Post by renegaide on 2008-07-16
Thank you bunches for the prompt help, Pumalite! I'll be following your replies closely. Here it goes then:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6e7a6e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2           16065   156280319    78132127+   5  Extended
/dev/sda5           16128    51199154    25591513+   7  HPFS/NTFS
/dev/sda6        51199218   156280319    52540551    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81930d21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sdc2        61432560   390700799   164634120    f  W95 Ext'd (LBA)
/dev/sdc5        61432623   390700799   164634088+   7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-07-16
I see your 3 drives fine. but I don't see a Linux system anywhere. You have an extended partition in sda2. ???

---

### Post by renegaide on 2008-07-16
Sorry for the extended silence, but I was working on reinstalling Ubuntu. Here were my findings: whenever I received the error message stating one of the drives couldn't be mounted, I clicked to see the "Details", and that's when I found out that I needed to insert that drive in my external HD case, plug it into Windows, and then click to allow its removal from USB devices.

That done, I was able to access it in Ubuntu, along with the other missing drive! Now there's still one problem remaining: whenever I try to boot into Windows from the Grub menu, I get "Error 12: Invalid device requested".

I found out that if I switch the startup drive in the BIOS to the one holding the XP partition, XP will boot without a problem.

Could you help me fix that error 12? (I'm afraid I might destroy everything again if I try solving it on my own). :)

Thanks bunches for the help so far!

---

### Post by renegaide on 2008-07-16
Oh, and here's my current fdisk -lu status:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6e7a6e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    47279294    23639616   83  Linux
/dev/sda2        47279295   156280319    54500512+   5  Extended
/dev/sda5        51199218   156280319    52540551    7  HPFS/NTFS
/dev/sda6        47295423    51199154     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81930d21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sdc2        61432560   390700799   164634120    f  W95 Ext'd (LBA)
/dev/sdc5        61432623   390700799   164634088+   7  HPFS/NTFS

```

---

### Post by Pumalite on 2008-07-16
You are trying to boot Windows from a logical partition. Windows needs a primary partition; preferably sda1.

---

### Post by renegaide on 2008-07-16
Assuming I have sda1 and sdc1 partitions to install Ubuntu and XP, and given that XP (and its installation CD) is not recognizing sda or sdb, do I actually have any options, as far as having them fully functional through dual booting?

And, would you be able to help me figure out why my BIOS and Ubuntu 'see' my SATA disks but NOT XP?

---

### Post by Pumalite on 2008-07-16
I don't know about Windows,but Ubuntu sees all your drives. Your problem is that you have Windows inside of an extended partition. Maybe you need to redo that drive, and put XP in sda1.

---

### Post by renegaide on 2008-07-16
Perhaps my question should be instead: what exactly would you do if you were in my situation, in concrete terms (i.e. use certain software to redo this specific drive, and then..., etc). 

I'm completely up for anything, including reinstalling both OSs if necessary. Thanks, Puma (who indeed delivers FAST answers!).

---

### Post by Pumalite on 2008-07-16
Save your data. Get Gparted Live CD and delete everything in that drive. Make 2 partitions: the first (sda1)(at the beginning os the drive) format ntfs. The 2nd ( at the end) format ext3. Install XP in sda1 first. Then install Ubuntu and let Grub install to MBR (by default)

---

### Post by renegaide on 2008-07-16
I'll do that and post my results! Many thanks!!! :-o

---

### Post by renegaide on 2008-07-18
Pumalite, I completely erased all partitions from what was the sdc drive, and with the Supergrub disk made the drive into hd0. I then proceeded to create a 30GB NTFS partition for the XP, followed by a 2GB swap partition at the very end of the HD, and a 30GB ext3 partition right behind it. I then created a FAT32 logical partition with the remaining 130GB.

Installed XP and it went fine, this time with all of the SATA drives being recognized. The problem is, when I installed Ubuntu and it restarted, it would continue going straight into XP (no Grub kicking in). I then tried to "activate" the Ubuntu partition using the SuperGrub disk, and then nothing worked (I then quickly activated the XP partition again).

Some curious things I also noted: whenever I formatted the HD using the Gparted CD it was being recognized as hda, and not as the previous sdc. It also became clear to me that the Supergrub nomenclature hd0, hd1, has no connection with the sda, sdb nomenclature. Is there anyway I can swap sdas for sdbs and sdcs? 

Or, what's even more important: what went wrong this time, why, and how can I fix it!??

---

### Post by Pumalite on 2008-07-18
Post>
sudo fdisk -lu

---

### Post by upchucky on 2008-07-18
when it booted and nothing worked this was the point to get stage 1 working for grub, after stage 1 starts working and goes busy box then need to get stage 2 working on ubuntu grub menu.lst

since you have supergrub you can create both stages, there is also posted here a quick way to create both stages from the CLI, but i dont remember where they are listed.

---

