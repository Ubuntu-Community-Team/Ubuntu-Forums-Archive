---
title: "Dual Boot issues with Grub"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by Fraktyl on 2008-01-12
Ok, been beating my head against the wall for about two days now.  Reading threads, searching google.  Trying all sorts of different things.

Here's the problem.  I have 2 Sata Drives.  The first (sda) has XP installed.  I installed Ubuntu on the second (sdb).  During the install I created a /boot partition of 100 megs as the first partition.  It's a habit I picked up a long time ago with older versions of LILO.  I also told the install to install Grub in (hd1).

After the installation was complete, I used the Bios boot menu to boot from the second drive.  Grub hung, so inside the Grub menu I changed it from root (hd 1,0) to root (hd 0,0) since the Bios modified the drive order.  Not a big issue.  System booted into Ubuntu.

So I tried to copy the MBR using the dd if=/dev/sdb1 of=/media/sda1/ubuntu.bin bs=512 count=1.   Went back over to XP and edited the boot.ini file to use the ubuntu.bin MBR.

When I choose that option from the XP boot loader, it attempts to run Grub, but all I get is GRUB in the top right corner, and a flashing cursor.  Have to hit the reset button to get my system back.

I've tried reinstalling Grub, recopying the mbr from sdb.  All sorts of combinations.  Nothing seems to work.  Like I mentioned, if I boot from that drive using the Bios menu it'll load if I edit the line that tells it where root is.

Any ideas, or places I can look.  I'm running out of ideas.

Thanks.

---

### Post by PmDematagoda on 2008-01-12
You said that you instructed the BIOS to boot from the second drive, yet you said that you installed GRUB to the first drive, so did you try telling the BIOS to boot from the first drive?

---

### Post by Fraktyl on 2008-01-12
Just reread what I wrote.  Made a mistake... 

sda - XP
sdb - Ubuntu

Told Grub to install on sdb not the first hard drive.  When I use the boot menu from my bios (Asus MB hit f8 to pick which device you want to boot), and tell it to boot off the second SATA drive which is sdb Grub loads all the way.  I have to edit the root command so it shows root (hd0,0) and it will boot all the way.

If I just let the system boot normally, which would have the hard drives in the correct order, and boot into windows.  If I use the NT boot.ini file it comes up into windows ok.  When I choose Linux, it starts to boot grub, then locks up.  All I see on the screen is GRUB and a flashing cursor, so I don't think it's even trying to load the stage_1.5 file.

---

### Post by logos34 on 2008-01-13
I've run into this problem.

It's not enough that Grub is on the MBR of sdb--remember the dd command is copying the **bootsector of the (separate) linux /boot partition**, so it's probably coming up empy (a hex editor will show this).

So write grub to /boot first and then do the dd command and the rest like before:

-boot into ubuntu and do:
[B]
sudo grub-install --root-directory=/boot /dev/sdb[COLOR="Red"]1[/COLOR][/B]

or 

sudo grub

find /grub/stage1
(should show /boot partition, 'hd0,0')
root (hd0,0)
setup (hd0**,0**)  (-->not hd0, the mbr, it's already there)
quit

---

### Post by Fraktyl on 2008-01-13
Tried that logos, still no dice.

Since I hadn't really done anything with the system I decided to just reinstall, and removed the /boot partition.  Told grub to install on the mbr of sdb.

Rebooted, still no good.  Used the bios menu to boot off the second hard drive, and am able to get into the system.

So, I tried the following:
sudo grub
find /boot/grub/stage1     responded with (hd1,0)
root (hd1,0)
setup (hd1,0)

got this output:
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

Quit out of grub.  Ran this command
sudo dd if=/dev/sdb1 of=/media/sda1/ubuntu.bin bs=512 count=1

The contents of my boot.ini file from xp
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer
C:\ubuntu.bin="Linux"

Rebooted... still no good.  All I get is the word GRUB and a flashing cursor.  Any other ideas or places to research would be greatly appreciated.  Thanks for the help so far.

---

### Post by logos34 on 2008-01-13
That's odd...I just did this a week ago and had the same problem until I installed grub to the bootsector of my ubuntu root partition.  Then I ran the dd command and linux boots fine from boot.ini.  Granted, I did this on single-disk dual boot setup.  So my guess is the location of your second disk containing ubuntu is throwing grub for a loop--it can't find it to pull up the menu.lst.  Why I don't know, because it's second in the Bios order and the root line is set for '(hd1,0)'.  Maybe it needs to be (hd0,0), dunno..and then (re)install grub to the bootsector, etc. etc. (More [here]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why"))

But why are you trying to boot ubuntu from windows and not the other way around?  I guess I should have asked you this in the first place, because the better way to do it is to use grub to chainload windows on a non-first hard disk--you need to [add 'map commands' to the windows entry in menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") to fool it into thinking it's the boot disk.  

Reboot.  Change the Bios hard disk boot priority so the ubuntu disk is first.

Use the 'e' key to edit the ubuntu menu.lst entry to (hd**0**,0) so it boots.

Once you boot into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

change the 'groot' line and ubuntu root lines to (hd0,0).  

Edit windows entry as described in the link above.

gksudo gedit /boot/grub/device.map

change to reflect new order

---

### Post by Fraktyl on 2008-01-13
Well, tried to set up grub using the map commands.  Now I get ntldr not found.  *sigh*

So, I physically swapped the drives, so sda is now the Ubuntu drive, sdb is the XP drive.  Still getting the ntldr not found.  If I choose the drive from the Boot menu it loads xp fine, so the MBR isn't gone.

Here's the output of fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03140314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       18959   103458600   83  Linux
/dev/sda3           18960       19457     4000185   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01140114

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sdb2            3825       14278    83971755    7  HPFS/NTFS
/dev/sdb3           14279       19457    41600317+   7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc7b95a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18079   145219536    7  HPFS/NTFS

Disk /dev/sdd: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

sdc and sdd are an Nvidia Raid stripe.  That's set up fine with dmraid.

Here's my menu.lst
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=db16284b-baa7-4817-8951-a0c3f7e80e18 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=db16284b-baa7-4817-8951-a0c3f7e80e18 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader     +1

groot is set to (hd0,0)

Here's device.map
(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd

I've also done the following:
sudo grub
find /ntldr
(hd1,0)
fine /boot/grub/stage1
(hd0,0)

So the hard drive list in device.map is correct from everything I've read.

I'd really like to not have to remember to hit F8 if I want to boot into XP.  It works that way, but I'd prefer not to have to do it.  Appreciate the help, I'm about ready to just install Lilo but I don't like admitting defeat.

---

### Post by logos34 on 2008-01-13
> Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3824 30716248+ c W95 FAT32 (LBA)
/dev/sdb2 3825 14278 83971755 7 HPFS/NTFS
/dev/sdb3 14279 19457 41600317+ 7 HPFS/NTFS

are you sure the first partition is XP system drive (c: )? Or is it sdb2?  (which would make more sense because it's ntfs).

---

### Post by Fraktyl on 2008-01-13
It's definitely the first partition.  I usually leave the boot drive fat32 since finding drivers to access ntfs from dos is still sketchy (at least last time I looked around).

---

### Post by logos34 on 2008-01-13
ok, I see.

Hmm, why is nothing working?  And you can boot XP directly with it's own bootloader fine!
What could it be?

---

### Post by logos34 on 2008-01-13
I can't figure it out--usually one of the two approaches will work.  Try Lilo.

There is [this method]("http://users.bigpond.net.au/hermanzone/p9.html") to boot ubuntu from windows you can try (if you're still alive!).

---

### Post by bartgrefte on 2008-03-10
I have éxactly the same problem with XP64 and Kubuntu 7.10 x64.
Well, one difference. GRUB with the flashing cursor is on the topleft, not topright.

Still no sollution here.

Specs: [http://tweakers.net/gallery/sys/15529](http://tweakers.net/gallery/sys/15529)

---

