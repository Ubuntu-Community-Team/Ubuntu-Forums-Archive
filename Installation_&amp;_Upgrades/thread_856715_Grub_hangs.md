---
title: "Grub hangs"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Noccy on 2008-07-11
Hi!

I just tried installing Ubuntu 8.04 on my desktop system. It's a mixed PATA/SATA setup, so the drives are arranged in a funny way. My Windows C: drive is /dev/sdd, while my F: where I installed Ubuntu is /dev/sda. /dev/sdd is the SATA drive, and the other (sda, sdb, sdc) are PATA drives.

After installing Ubuntu as /dev/sda2 (2nd partition on F:), and selecting to install the bootloader on /dev/sda, the Windows bootloader jumped in and fired up my XP install. So, I went back and re-did the installation (time shortage, googling command lines didn't fit my schedule) and this time explicitly set the bootloader to be written to /dev/sdd.

After installing and rebooting, all I got out was the text "GRUB", nothing more. No boot menu or anything.

The only solution here was to boot the recovery console from my XP cd and issue the FIXMBR command, so now I have a unbootable Linux install on my F: drive, and working Windows install on my C:.

How do I get around this? Is there any alternative boot loaders I can use? Can I configure GRUB in any special way from the Live CD without trashing anything? Is it possible to boot Ubuntu using the Windows NT boot loader?

Please help :) Windows is getting on my nerves more and more, especially since I spent 48 hours with the Live CD, and I really want to be able to boot Ubuntu.

Best regards,
Chris

---

### Post by Herman on 2008-07-11
Just try booting into your BIOS and switching your hard drives around in your BIOS so that the hard drive Ubuntu has first installed GRUB in, (the hard drive Windows is in), will be the first hard drive.
Then switch the remaining three hard drives around until you find a combination where everything will work properly.
That seems to be the easiest way to sort this type of problem out.
People who have tried this method out report that it's the easiest way and no editing of Window's boot.ini or Ubuntu's /boot/grub/menu.lst is needed.

EDIT: I realize your BIOS is probably a lot different to mine, but here's a link with illustrations about how I do that in the BIOS of one of my computers just to make sure you understand what I mean, [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").

If you still have trouble, check your hard drive cables and jumper settings for your IDE drives including your CD/DVD drive(s) and make sure those are cabled, plugged in and jumpered correctly.

If you need more help, please post the output from 'sudo fdisk -lu',
```
sudo fdisk -lu
```and also [FONT=Bitstream Vera Sans Mono]'sudo lshw -C disk'
[/FONT]```
sudo lshw -C disk
```Regards, Herman :)

---

### Post by Noccy on 2008-07-12
Thanks for your quick reply :) Thought I'd make some clarifications before I dive back into the Live CD.

The drive refered to as /dev/sdd is in fact the first boot device in my BIOS. All jumpers are proper etc, and the system has been running well on XP for quite a while now :) 

I also googled quite a bit, and found some pretty interesting pages explaining how to use NT's bootloader to fire up grub4dos or an actual extracted boot sector. Would this be possible in your opinion?

1. Reinstalling Ubuntu, and properly installing the boot sector on the drive refered to by windows as F: (i.e. /dev/sda) to ensure that future updates will update the boot sector on that drive
2. Using DD to extract the boot sector (dd if=/dev/sda of=ubuntu.mbr bs=512 count=1) and placing that file in the C:\ root of my Windows drive.
3. Adding the line "C:\ubuntu.mbr"="Ubuntu (GRUB)" to my boot.ini in order to have it call the boot loader.

Would it in this case be able to find the proper partitions etc as they are currently configured? :)

(EDIT: Optionally, would it be able to use XOSL and tell it to boot ubuntu from the bootsector on a drive other than C: (/dev/sdd)?)

I'll get back to you with the FDisk output

Best regards,
Chris

---

### Post by Xeekder on 2008-07-12
I have a doubt, is there any posibility to reinstall the GRUB (from the ubuntu live cd, by reinstalling Ubunthu) and then make the GRUB boot from the partitions (due to the fact that the partition are still intact)???? i have a similar problem with gusty gibbon server, (grub error 17), i´ve done the "fixmbr" thing and now i´m not able to boot to my ubuntu server (just to windows),... will reinstall the grub work??:-({|=

---

### Post by Herman on 2008-07-12
@ noccy,
> The drive refered to as /dev/sdd is in fact the first boot device in my BIOS. All jumpers are proper etc, and the system has been running well on XP for quite a while now :) Okay, but there's  a difference of opinions here as to which hard drive is actually your first hard drive. 
Your BIOS obviously considers the SATA drive you have Windows installed in as your first hard drive, but Linux calls that one '/dev/sdd', which would normally indicate the fourth hard drive.
That's probably why your computer still booted Windows after your first install, because GRUB was probably installed to /dev/sda, which Linux thnks is your first hard drive.
That means probably your /boot/grub/menu.lst has Ubuntu as (hd0,1), and Windows would be in (hd3.0), with a pair of 'map' commands.
If you simply switch the SATA disk to fourth hard disk in your BIOS, that would probably bring the BIOS into agreement with Linux and GRUB, and everything should work fine, as Ubuntu is most likely already configured as if that were the situation. 
This should avoids the need to go re-installing GRUB to different MBRs and editing files like we used to do when people had this type of problem.
> I also googled quite a bit, and found some pretty interesting pages explaining how to use NT's bootloader to fire up grub4dos or an actual extracted boot sector. Would this be possible in your opinion?Sure, anything is possible, there are all kinds of options, but using GRUB is normally the best and easiest.
Here's my WinGRUB Page, (grub4dos), [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").
There's also GAG Boot Manager as well, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm").
I do know how to get the NTloader to work but I don't recommend it. I haven't tried it on more than one hard disk, probably it would work, but if you are smart enough to be able to figure that out and willing to take the risk of fiddling with the Windows system and editing boot.ini by hand you should be smart enough to be able to figure out how to boot with GRUB. 
Why drive a model T when you can drive a Rolls Royce?

Regards, Herman  :)

---

### Post by Herman on 2008-07-12
@Xeekder,
> I have a doubt, is there any posibility to reinstall the GRUB (from the ubuntu live cd, by reinstalling Ubunthu) and then make the GRUB boot from the partitions (due to the fact that the partition are still intact)???? i have a similar problem with gusty gibbon server, (grub error 17), i´ve done the "fixmbr" thing and now i´m not able to boot to my ubuntu server (just to windows),... will reinstall the grub work??:-({|=If you have [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17") when trying to boot Linux, but Windows boots okay, and your computer has only one hard disk, it could be caused by:

[LIST]
[*]Your Ubuntu file system is corrupted, probably it can be fixed by [Running a filesystem check]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")
[*]Your partition numbers have changed because you might have used a foreign partition editor that likes to number your partitions in disc order instead of leaving them alone. If that's the trouble then you probably need to open your /boot/grub/menu.lst and edit it with the new partition numbers.
[/LIST]
Probably you'll need the output from 'sudo fdisk -lu' to help you find out what numbers you need to edit your /boot/grub/menu.lst with.
```
sudo fdisk -lu
``````
gksudo gedit /boot/grub/menu.lst
```You can boot Ubuntu with [Super Grub Disk]("http://www.supergrubdisk.org/"), and then fix it, or you can use your Hardy Heron Live CD to rescue your hard disk installed Ubuntu system and then boot it.  [Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

You'll be able to use your Super Grub Disk to re-install GRUB, or you can [re-install GRUB from your Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

If you need specific help, please post a copy of your fdisk -lu output here along with a copy of the bottom half of your /boot/grub/menu.lst file. 

Regards, Herman :)

---

### Post by Xeekder on 2008-07-13
hello, thx a lot for such a great answer,

yep the second thing actually happend, i've created a backup partition for windows (unfotunatelly using "manange disk" from win), 

# fdisk-lu

Disk /dev/sda: 1021 MB, 1021313024 bytes
15 heads, 46 sectors/track, 2890 cylinders, total 1994752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             240     1994751      997256    6  FAT16

# my media/disk-1/boot/grub

title		Ubuntu 7.10, kernel 2.6.22-14-server
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=74733f12-471b-41f9-abae-a6833f35b406 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-server
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-server (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-server root=UUID=74733f12-471b-41f9-abae-a6833f35b406 ro single
initrd		/boot/initrd.img-2.6.22-14-server

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# unfortunatelly now if i try to reinstall the GRUB from my gusty gibbon live cd it didn't show me any partition, are my partitions gone? i don't think so because i can acces my volume (gusty gibbon mounts it, and i'm able to see the partitions in disk manangement in win)  is there a way to retrain the grub in order to boot linux and win as it used to?,,, now im in gusty but, my win boots ok 'cause the 'fixmbr' has 'killed' the GRUB, so the mbr is using the win boot loader... yep i have 1 hdd. do you recomend another boot loader like the dude from the upper post? 

tnx,

---

### Post by Herman on 2008-07-14
```
Disk /dev/sda: 1021 MB, 1021313024 bytes
15 heads, 46 sectors/track, 2890 cylinders, total 1994752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

   Device______Boot______Start______End______Blocks______Id______System
/dev/sda1_______________240__1994751_____997256_______6______FAT16
```:confused: A 1.0 GB hard disk? 
This looks to me more like your flash memory stick. What's going on here?

My guess is that Windows Partition Manager has written such garbage to your hard disk's MBR that the hard drive isn't even being read by fdisk.
> unfortunatelly now if i try to reinstall the GRUB from my gusty gibbon live cd it didn't show me any partition, are my partitions gone? It seems that as far as Linux based partitioners are concerned, the information in your partition table is corrupted and they're not going to touch it, or have anything to do with it.
>  i don't think so because i can acces my volume (gusty gibbon mounts it, and i'm able to see the partitions in disk manangement in win)  Well, that's good.
> is there a way to retrain the grub in order to boot linux and win as it used to?,,, now im in gusty but, my win boots ok 'cause the 'fixmbr' has 'killed' the GRUB, so the mbr is using the win boot loader... yep i have 1 hdd. do you recomend another boot loader like the dude from the upper post? No, using another boot loader won't help you in this situation. 
If I were you I'd first make a backup of all important files (if you haven't already done so), and then use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to write you a new partition table, (one that will be compatible with both Windows and Linux).
You can install TestDisk temporarily in your Ubuntu Live CD, (it will last as long as the CD is booted), or you can use TestDisk already installed in [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"), or _[GParted -- LiveCD]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fgparted.sourceforge.net%2Flivecd.php&ei=BwZ7SNvPBYGWsAOqtJWUDw&usg=AFQjCNGWyivxbJE-tRN5Pe2km0nGTmRBvw&sig2=DkwHAbv9H_JWFu7ehLFp9w")_, or [System Rescue CD]("http://www.sysresccd.org/Main_Page"), or [Knoppix]("http://www.knoppix.net/").
To install TestDisk in your Ubuntu Live CD for one session, 'sudo apt-get install testdisk'
```
sudo apt-get install testdisk
```TestDisk is very easy to use, but it's like most things, the first time you might not know what to do, so I made a web-page giving a couple of examples of what it's like, here, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html"). Please refer to the official TestDisk site's instructions too, they have very good instructions of their own now. [COLOR=#C0C0C0][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk") the official homepage for TestDisk[/COLOR]

After you restore your partition table you'll probably still want to re-install GRUB again, here's my link about how re-install GRUB to MBR with the Live CD, [Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").
 
I also recommend [Super Grub Disk]("http://www.supergrubdisk.org/") for helping you to boot either Linux or Windows in case of boot loader problems. (It works for most boot loader problems).

Regards, Herman :)

---

