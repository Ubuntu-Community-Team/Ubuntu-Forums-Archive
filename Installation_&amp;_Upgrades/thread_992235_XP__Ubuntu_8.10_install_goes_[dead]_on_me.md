---
title: "XP / Ubuntu 8.10 install goes [dead] on me"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by Inspector Gadget on 2008-11-24
downloaded 8.10 ok, managed to create the cd, ran ubuntu from the cd,a feat for me! loved the clean feel to it, decided to install it on a spare 500gb drive and really started to enjoy the experience. On Saturday fired up with my new found pc knowledge, I managed to get my 750gb drive which has been playing up for some working nicely with XP and after reading a few positive posts regarding dual XP/8.10 same HD installs went for it full of confidence... a big cockup resulted, nothing would boot.. neither XP or 8.10, having swapped my drives around, the 500gb will run ubuntu and i can see my bigger drive in the places menu and am able to run media files from it so what have I done wrong? I know people who don't know what they are doing should leave well alone, and I have commited GBH to many a poor innocent pc in the past but unintentionally honestly... is there hope for my install yet? is it salvageable? searching for similar mishaps in the forum posts I'm beginning to believe there is, so for starters here goes...

les@les-desktop:~$ sudo fdisk -lu
[sudo] password for les: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf01af01a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   964638989   482319463+  83  Linux
/dev/sda2       964638990   976768064     6064537+   5  Extended
/dev/sda5       964639053   976768064     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29075016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   839331989   419665963+   7  HPFS/NTFS
/dev/sdb2       839331990  1465144064   312906037+   5  Extended
/dev/sdb5       839332053  1453014989   306841468+  83  Linux
/dev/sdb6      1453015053  1465144064     6064506   82  Linux swap / Solaris
les@les-desktop:~$ 
 
does that make sense to anyone and what is my next step?

gadget

---

### Post by lemming465 on 2008-11-25
Lots of hope, yes.  I'm not sure how much you know about the XP & Grub boot process, so let's recap that first.  Slightly oversimplified:

1. BIOS loads sector 0 off the first hard drive (sda).  This contains 446 bytes of Master Boot Record "MBR" boot program followed by a DOS-style partition table.  
2. The MBR loads sector 1 from the first primary partition flagged "active".
3. The first sector of said partitions loads as much as it please of sectors 2-62, the so-called secondary boot loader.  This is why the first data sector in a partition is typically 63.  
4. The secondary boot loader (e.g. grub stage 1.5) reads the _real_ boot loader off an actual data partition file system.  In the XP case the real bootloader is "ntldr"; in the grub case it's the "stage 2" file.  
5. The real boot loader offers a menu of boot options, loads the  kernel of the users choice, and ...
6. away you go.  Note that the file system the OS is loaded off of doesn't have to be the ultimate root (unix) or system volume (windows), though often that is the case.  Given your disk layout, it looks like is the case for you; good, that makes things easier.

The obvious things that can go wrong as you swap disks around are
* no MBR boot code
* no secondary boot code
* inability to find the disk partition with the OS kernel on it

I'm assuming you installed XP with the '750 disk as the primary, or maybe only disk. If so, to make it happy you will need to swap drive cables around so that the '750 is primary (sda in linux) and the '500 is secondary (sdb in linux).   Also, you currently seem to have two Linux installs, one using the entire '500, and using 300 GB on the '750 disk.  It's OK to have more than one, but you will probably have a preferred one.  I'll assume it's the new one sharing the '750 with XP. 

Without knowing the trajectory of your installs, I have no idea whats currently on the MBR of the '750, the secondary boot sectors of its partition 1, and the secondary boot sectors of partition 5.  Let's assume complete garbage there, but that the file system data is intact.  Also, we have to pick which OS is going to own the MBR.  Each OS gets its own secondary boot stage and in-filesystem "real" bootloader, but only one OS gets to own the MBR.  With any scenario not involving TPM chips and Vista Bitlocker, I find it easiest to let Linux control the MBR.  I'll assume you are willing to do the same.  So, our goal is:

primary disk - '750
-----------
MBR - grub
sda1 - XP secondary boot loader + XP system partition
sda5 - grub secondary boot loader + Linux root partition

secondary disk - '500
---------------
MBR - don't care (currently grub)
sdb1 - don't care about boot loade + another Linux root partition

To get from crud to there, we need an XP boot recovery disk and a Linux boot recovery disk.  This is where things get a little sticky, as I don't know what media you have access to.  

If you have an XP install disk, you can boot that in recovery mode and [tell it to fix the MBR & boot loader]("http://http://articles.techrepublic.com.com/5100-10878_11-6031733.html") using "fixboot" and "fixmbr".  Since sda1 is marked as the active partition, it will fix that disk up with fresh MBR code and sectors 1-62 with the secondary XP boot code, and at that point XP should boot again.  Linux won't; but we'll tackle that next.  The boot repair process won't tamper with the partition table or filesystem contents (other than perhaps refreshing C:\ntldr and C:\ntdedect).

If you don't have an XP install disk, you may have an OEM recovery disk, which may or may not have a similar boot repair options.  If your computer vendor didn't supply a recovery disk, you may have access to a BartPE or Windows PE disk.  Failing any of those, try burning a [system rescue CD]("http://www.sysresccd.org/") and use the testdisk utility off that. 

If you don't care what is on the sda5 partition, just reinstall Ubuntu, let it put Grub on the MBR of the '750 disk, and everything should be fine.  The Ubuntu installer will notice the XP partition and make a boot entry for it automatically.

If you do care what's on the sda5 partition, no problem, we just do a Linux boot repair.  Boot the Ubuntu Live CD you installed from, open up an Application -> Accessories -> terminal window, and do:```
sudu -i
umount /dev/sda5
mkdir /media/sda5
mount /dev/sda5 /media/sda5
grub-install --root-directory=/media/sda5/boot /dev/sda
```

That will put a grub stage 1 MBR on sda sector 0, and a grub ext3 stage 1.5 secondary boot loader on sda5.  At this point, if you are lucky, the hard disk will
show the original Ubuntu boot menu, and it will include an XP boot option, and life will be good.

Now, you may have problems with your sda5 boot/grub/menu.lst file, depending on its history.  If you can't boot the sda5 Linux, and there is no entry for booting
XP either, we need to resort to plan C. Follow the same process with mkdir and mount as above, and make a backup copy of the current file```
cp /media/sda5/boot/grub/menu.lst /media/sda5/boot/grub/menu.old
``` Post the output from ```
sudo blkid
ls /media/sda5/boot
cat /media/sda5/boot/grub/menu.lst
```
With that information, we'll be able to offer you more specific advice.  In the meantime, while you are waiting for us to analyze the contents of that file, a minimalist menu.lst file which can boot all 3 of XP on sda1, Linux on sda5, and the other linux on sdb1, might look like this:```
default 1
timeout 30

title 750 GB XP
root            (hd0,0)
chainloader     +1

title 750 GB linux on sda5
root            (hd0,4)
kernel          /vmlinuz root=/dev/sda5 ro
initrd          /initrd.img
boot

title 500 GB linux on sdb1
root            (hd1,0)
kernel          /vmlinuz root=/dev/sdb1 ro
initrd          /initrd.img
boot
```

Use your favorite text editor, such as nano (command line) or gedit (GUI).

---

### Post by caljohnsmith on 2008-11-26
How about before doing any changes to your system, please post the following so we see if Grub is installed to the MBR (Master Boot Record) of your 750 GB drive, and if it is, which partition it points to for its boot files:
```

sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```

---

### Post by caljohnsmith on 2008-11-26
> **lemming465 said:**
> Lots of hope, yes.  I'm not sure how much you know about the XP & Grub boot process, so let's recap that first.  Slightly oversimplified:

1. BIOS loads sector 0 off the first hard drive (sda).  This contains 446 bytes of Master Boot Record "MBR" boot program followed by a DOS-style partition table.  
2. The MBR loads sector 1 from the first primary partition flagged "active".
3. The first sector of said partitions loads as much as it please of sectors 2-62, the so-called secondary boot loader.  This is why the first data sector in a partition is typically 63.  
4. The secondary boot loader (e.g. grub stage 1.5) reads the _real_ boot loader off an actual data partition file system.  In the XP case the real bootloader is "ntldr"; in the grub case it's the "stage 2" file.  
5. The real boot loader offers a menu of boot options, loads the  kernel of the users choice, and ...
6. away you go.  Note that the file system the OS is loaded off of doesn't have to be the ultimate root (unix) or system volume (windows), though often that is the case.  Given your disk layout, it looks like is the case for you; good, that makes things easier.

That's not entirely true :); if you have a Windows type MBR that simply boots the primary partition that is marked active, and if you have Grub installed to the boot sector of the active partition, then you boot Grub's stage1 file in the partition boot sector. But Grub does not embed its stage1.5 file in the sectors immediately following the partition boot sector, because those sectors are not always available. Instead, the stage1 file points directly to the physical location of the stage2 file, so the stage1.5 is skipped.

If instead Grub is installed to the MBR, then it does not boot the partition marked as active by default; it will load the stage1.5 file which is embedded in the sectors immediately after the MBR if the stage1.5 file was installed (the normal case), or the stage1 file can point directly to the stage2 file if Grub was specially installed to omit the stage1.5 file. But in both cases the stage2 file will get booted, and then stage2 loads the menu.lst.

---

### Post by Inspector Gadget on 2008-11-30
first off, thanks to all the replies to my problem... a friend currently has my 750gb drive and is in the process of transfering the important files he is able to (?) and I'm hoping that when I get the drive back I can try some of the above to resolve my issues.. thanks guys

Anyway yesterday I purchased a second 500gb drive and that will be exclusively for XP until I am able to locate printer drivers for my Canon i9950 which I use for A3 prints of my water colours.. we have a daughter that needs access to the printer for her homework and I may be able to get a workaround by finding a print server to run off my BT home hub that she can use the printer without having to start my pc up, until then I need to be able to boot from start-up into either the XP or Linux OS, anyone able to tell me in simplespeak how to edit the grub loader if I make my Linux HD the primary drive? I shall continue my searching of the forums as I'm sure that must be one of the most asked newbie topics..:)

once again thanks for the advice, I just wish I was 45 years younger

Gadget

---

### Post by caljohnsmith on 2008-11-30
So are you booting the Linux 500 GB sda drive on start up that you listed in your first post? Since you've added a new 500 GB drive to the picture, how about posting the new output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by Inspector Gadget on 2008-11-30
les@les-desktop:~$ sudo fdisk -lu
[sudo] password for les: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf01af01a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   964638989   482319463+  83  Linux
/dev/sda2       964638990   976768064     6064537+   5  Extended
/dev/sda5       964639053   976768064     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb45db45d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976751999   488375968+   7  HPFS/NTFS
les@les-desktop:~$ 

so far so good

les@les-desktop:~$ sudo xxd  -l  2 -p /dev/sda
eb48
les@les-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
00ff
les@les-desktop:~$

les@les-desktop:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
0000
les@les-desktop:~$

---

### Post by caljohnsmith on 2008-11-30
OK, it looks almost certain that you are booting the Ubuntu sda drive on start up, so to boot Windows from your Grub menu, first open it with:
```
gksudo gedit /boot/grub/menu.lst
```
And then at the very bottom add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try select Windows from the Grub menu, and let me know exactly what happens.

---

### Post by Inspector Gadget on 2008-11-30
caljohnsmith  	

Thank you, working menu and everything....

will report on the 750 as and when I get any news.... have a years worth of photography on there gone walkabouts..:(

regards

and am enjoying the Ubuntu environment immensely 

Gadget

---

