---
title: "Vista Dual Boot Issues (Assistance greatly appreciated)"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Atlae on 2007-06-07
Hi All,
I'm having issues getting Vista to run again on my Sony Vaio laptop after installing Ubuntu.
Right now I'm hoping to get it to run as it should in a dual boot, or, if I can't, to get ubuntu to read my NTFS Vista partition and copy off my data.

The whole story:

I installed Ubuntu using the live CD and following the instructions on:[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first"]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first").
Everything went fine, the boot loader came up, and the only difference between their boot manager and mine was that there were two instances of Vista. Ubuntu loads fine.

Then things got strange.

When I first clicked one of the two instances of Vista, it "loaded" by going to microsoft system update, installing an update (as it does if one shuts down in vista), and then shutting down. Now, instance 2 goes to an error message: "Error 13: Invalid or unsupported executable format"  and instance 1 goes to the Windows loading bar animation for a while, then a black screen, and then the VAIO Recovery Center. However, it can't find my hard drive, so it can't do anything but reformat. If you exit, you get an error message saying "unable to find operating system."

Most of the people who have posted with this problem have gotten it to work by putting in their Vista cd. Sony doesn't send copies of Vista install discs because they've installed it in the BIOS settings and say you can start the install from there. Trusting them, I installed the dual boot without a cd, and of course I can't get it to run from the BIOS.

I tried the tips listed in: [http://ubuntuforums.org/showthread.php?t=398122]("Fix Vista After Ubuntu Install"), but when I try to run ntfsfix, I get a "volume is corrupt, you should run chkdsk" error.

I'm not completely sure, but I think the whole problem stems from windows looking for Vista in the Ubuntu partition, and I don't know how to change that.
I can copy over my boot manager.lst, exact error messages, or anything else that might help me get vista to load or ntfsfix to fix things etc.

I'm not yet ready to reformat. Any help is extremely appreciated.

---

### Post by confused57 on 2007-06-08
Open a terminal in Ubuntu(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

and

```
gedit /boot/grub/menu.lst
```

---

### Post by Atlae on 2007-06-08
**sudo fdisk -l output:**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         843     6769664   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         843       13888   104784672    7  HPFS/NTFS
/dev/sda3           13889       14593     5662912+   5  Extended
/dev/sda5           14011       14593     4682947+  83  Linux
/dev/sda6           13889       14009      971869+  82  Linux swap / Solaris

Partition table entries are not in disk order

[B]
boot manager list (minus the defaults, hope that's okay):[/B]

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4e44f103-f7d6-44e8-95c5-b2ccff481e60 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4e44f103-f7d6-44e8-95c5-b2ccff481e60 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e44f103-f7d6-44e8-95c5-b2ccff481e60 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4e44f103-f7d6-44e8-95c5-b2ccff481e60 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1



the ubuntus for 2.16 appeared after doing the update manager. however, i did all the ntfsprogs things in 2.15. 
Thank you for your quick response

---

### Post by confused57 on 2007-06-08
Your menu.lst looks like it should boot your Vista, you might try rootnoverify instead of root:
```
title Windows Vista/Longhorn (loader)
rootnoverify (hd0,1)
makeactive
chainloader +1
```

To edit your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
quit & save

You might want to download & burn a copy of  the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it may not be able to boot Vista, but probably worth a shot

If you want to mount your Vista partition to backup data:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

Read the link, but it would be something like this:
```
sudo mkdir /media/Vista
sudo mount /dev/sda2 /media/Vista -t ntfs -o nls=utf8,umask=0222
```
then you should be able to open nautilus, navigate to your filesystem, media directory, & open Vista directory...if it mounts ok you should be able to drag & drop to a removable backup media(USB or cd).

To unmount your Vista partition:
```
sudo umount /media/Vista
```

---

### Post by Atlae on 2007-06-08
thank you again for responding so quickly

with super grub disk i couldn't boot windows or fix boot windows, but through some menu I was able to get it to open a "please insert windows cd" dialogue. however since i have no install cd, i couldn't go further. the other thing that seemed hopeful was the install boot partitioner, but the only options were for fat, ntfs is unsupported as of yet. 

mounting was successful and unsuccessful. when i try to mount the hard drive, i get this error: lesley@lesley-laptop:~$ sudo mount /dev/sda2 /media/vista -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

in media it has both sda1 and sda2 folders, sda1 has the autorun files for the vaio recovery that i don't know what to do with, and sda2 is blank =\

is there any way i can install another windows (maybe xp, i have the disc) and access my vista partition from the other windows? or if i downloaded another copy of vista? or is that too complicated when there may be more options

---

### Post by Atlae on 2007-06-08
also, could this be causing any problems:

Device Boot Start End Blocks Id System
/dev/sda1 1 843 6769664 27 Unknown
**Partition 1 does not end on cylinder boundary.**
/dev/sda2 * 843 13888 104784672 7 HPFS/NTFS
/dev/sda3 13889 14593 5662912+ 5 Extended
/dev/sda5 14011 14593 4682947+ 83 Linux
/dev/sda6 13889 14009 971869+ 82 Linux swap / Solaris

even if it's not the problem, is there any way to fix it?

---

### Post by confused57 on 2007-06-08
I don't know if it'll help, but you might be able to run a chkdsk from your Window's XP install cd:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_chkdsk.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_chkdsk.mspx)

I've never done so myself, you may have to press "r" for recovery console & enter the command.

I don't know about installing Windows XP on another partition, it might work?

When you're trying to mount your Vista partition from Ubuntu...I saw you had /media/vista...if you did "mkdir /media/Vista, it wouldn't work...Linux is case sensitive & commands have to be typed exactly right(that's why copy & paste is preferred, if possible).

You might want to contact Sony & request a Vista install disk...I've read that they are required to send you one upon request.

---

### Post by Atlae on 2007-06-09
When I called them on a related issue, i had requested one, but they said it should be installed/protected so it would boot from BIOS if something ever went wrong and that they didn't need to send one >.<. however, it seems that isn't the case. I'm definitely going to try and appeal, especially if they're required to send one.

When i created the directory i made it lower case as well, it's a just a habit, but they do match.

I'll try to get a copy of Vista and try chkdsk from the XP cd in the meantime. Thanks again for all the help, I definitely like Ubuntu even if I've had some problems trying to get it to agree with my copy of Vista.

---

### Post by merlinus on 2007-06-09
> 
I definitely like Ubuntu even if I've had some problems trying to get it to agree with my copy of Vista.


You are mistaken.  It is vista that has a problem peacefully co-existing with ubuntu!

:D

-merlin

---

### Post by Atlae on 2007-06-10
To keep things updated: I talked to Sony Support, and they say that they can't send me a copy of Vista because it was supposed to have created recovery DVDs in the original install process. On top of that, they say because I've installed something other than the OEM Vista that it came with, it's out of their jurisdiction to help me and that all support would have to be from the other OS. They also said that the VAIO Recovery software would not work with anything other than their Vista, so I'm wary to install another copy even if I have my genuine serial.

I tried to use the Vista Live CD I found at [http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/](http://usbtools.wordpress.com/2007/05/24/portable-windows-vista-live-cd/) thinking that since it would load in NTFS, i might have  chance at getting my files.  However, when I navigate to the shadow "my computer", C: is there (at least its a start), but it says C: must be reformatted before I can use it. I'm starting to get really scared that I lost my data, though I followed the normal dual-boot instructions, so I don't know what went wrong.  There is a mbr manager that also is on the live CD, and when I look at my partitions, it sees my partition as (0,1) but says the partition is not active. However, when I try to activate it, though it says "successful" but still lists as not active. =\ With everything I do I feel so close to finding the answer,  if I could just change back the  Vista mbr (which I assume GRUB corrupted) or change the active partition or diskID or something. Any Ideas?

---

### Post by confused57 on 2007-06-10
You might try hiding your (hd0,0) recovery partition in your Vista entry, something like this:
```
title     Windows Vista
hide      (hd0,0)
unhide    (hd0,1)
root      (hd0,1)
savedefault
makeactive
chainloader +1

title      Windows Vista 2
unhide     (hd0,1)
hide       (hd0,0)
root       (hd0,1)
savedefault
makeactive
chainloader +1
``` 

If this doesn't work, you might want to download & burn a copy of Knoppix...mounting a partition is just a matter of clicking on the partition icon & selecting mount...I think the newest Knoppix allows writing to NTFS.
[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)

Install ktorrent in Ubuntu, if you decide to use bittorrent download...ktorrent works better for me.

---

### Post by Atlae on 2007-06-11
>.< I promise I'm not trying to be difficult, I just seem to have that type of luck. I hid the recovery partition as shown, but then I get an "Error 13" when I try either Vista. I changed them back and then tried knoppix 5.1, and the cd would boot, but then when i clicked to load, the screen would go black and nothing would ever come up.

I think I'm going to have to uninstall Ubuntu, and if that doesn't bring back Vista then it's off to the nearest Sony Support Center. I'm definitely not finished with Linux, though. Thanks again for all the time and assistance.

---

### Post by HunkirDowne on 2007-06-11
At the risk of boring you to tears or telling you what you already know, I had some thoughts.

Does Grub still work?  If it does, what happens when you boot from /dev/sda2?  This should be your normal Vista partition.  The partition /dev/sda1 looks like some sort of recovery thingy.  Odd layout, but I've never had a Sony computer.

The first partition, /dev/sda1, has id=27 which, according to my fdisk (Ubuntu 7.04) is not listed (hence your fdisk calling it "Unknown", most likely).  I'm guessing this is some proprietary Sony thing and they are making it difficult to do anything crazy, like install Linux.  OTOH, it could be a Vista thing for all I know, not having any experience with it.

Can you get your hands on another copy of Windows or DOS?  If you have it laying around, you could try a DOS boot disk with FDISK on it.  I can't remember if MS-DOS 5.0 had the FDISK /MBR function but I know MS-DOS 6.22 did.  If you don't, there's something called Ultimate Boot Disk that has some utilities on it, at least one of which has an FDISK with an /MBR repair tool.

In the future (and I should practice what I preach) you might want to investigate the Linux "dd" command and make a backup of your MBR on a floppy or USB stick.

My thinking at this point would be to use FDISK /MBR to restore your master boot record and Vista might then boot.  Linux wouldn't go away, exactly, but you won't be able to get to it without further maintenance.  If Vista uses the NTLDR, there's a HOWTO page about modifying the NTLDR to boot either Windows or Grub (or, Windows or LILO, if that's your preference).  Grub (or LILO, or for that matter, loadlin) could then be used to boot your Linux.  OR, you could just boot Vista off the hard disk and use the Super Grub Disk (I presume) to boot into Linux.

I can provide actual references if any of this strikes your interest.  I'm being lazy today.

---

