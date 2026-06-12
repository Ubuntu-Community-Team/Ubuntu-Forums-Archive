---
title: "MBR / bootsector detailed in GRUB in Dualboot-setups"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by perixx on 2008-01-04
Am I right, when assuming that Ubuntu just writes the first 4xx bytes (the bootloader) and not the full 512 bytes of the MBR (including the bootSECTOR for XP), when using the automated installation option, setting up Grub in the MBR?

Does Windows' recovery command 'fixboot' only write the first 4xx bytes respectively, or only the remaining bootsector-bytes?

Can someone please confirm/clarify this?

perixx

---

### Post by LaRoza on 2008-01-04
I don't know exactly what your issue is, but Grub is not really in the MBR, as it is too large. If you fixmbr with Windows, it will be overwritten and only Windows will boot.

---

### Post by perixx on 2008-01-04
I'm not currently having any issues, but I'm a seeker of knowledge ^^

I believe that there's only a part of the Grub bootloader residing in the MBR, or in the superblock - depending on where it's installed (Stage 1) - and this is chainloading the initrd.img in /boot/ (Stage 1.5), creating a virtual file system for the kernel and actual Grub files in /boot/grub... or some such thing, or maybe I've mixed it up here...

Anyway, I've read that the MBR is consisting of 3 or 4 parts, mainly the first 426 (?) Byte, containing the bootlaoder (nt-bootloader or Grub stage 1) and the rest is merely a pointer (bootsector) to the system files - at least for Windows, don't know if those are also used by Grub.

There's a difference in the Xp recovery's 'fixboot' and 'fixmbr' - but I'm not sure if it just refers to what's written into the MBR or if the first one only writes the system files (ntldr.com). I once had an incident where I couldn't recover the MBR for XP by any means (not via 'fixmbr' / 'fixboot') and fdisk /mbr or SGD - nothing would dispose of Grub, so I had to re-install Ubuntu, which was chaninloading XP in the first place. 

Now I want to figure out what's EXACTLY going on at the byte-level in the MBR... I mean, there's only 512 of them - should be possible to work it out I hope :]

perixx

---

### Post by Herman on 2008-01-04
An MBR is the first sector of every formatted hard disk and it isn't part of Windows at all. 
An MBR contains an area for some boot loader code to be written in and another are reserved for the partition table for the hard disk. It also contains a 2 byte disk signature.

The letters 'M.B.R.' stand for **'M**aster **B**oot** R**ecord'.  
There can only be one Master Boot Record in a hard disk, otherwise why call it the 'Master' boot record? 
Still, a lot of people get their terms mixed up and use the terms 'boot sector' and 'MBR' interchangeably. 
The MBR isn't part of any operating system's file system and therefore it is independent of any operating system.

The term 'boot sector', probably comes from the fact that Windows operating systems seem unable to boot without having a little boot loader code also in the first sector of the Windows partition, called a 'boot sector'.

The Windows partition can be located anywhere on the hard disk, and have any partition number, but It's simpler for most people to let Windows stay as the first partition both numerically and positionally.

Anyway, if you want to see for yourself, just do 'sudo fdisk -lu' and take a look,
```
sudo fdisk -lu
```In most cases you'll see that if you have Windows, it's first sector (boot sector), is most often located at sector 63. 

The first track (63 sectors) is empty except for the MBR, so the first partition never starts until sector number 63. (I suppose the MBR would be sector 0 then, I'm not sure).

When you install Ubuntu, Grub does install its stage1 code in the first 446 bytes of the MBR, overwriting whatever other boot loader's code may have been previously in there.
There are some other bits and pieces of code in the first 446 bytes that doesn't get over written, but it's quicker just to say that GRUB writes to the first 446 bytes and that's good enough for most people's purposes.
GRUB also installs its stage1_5 files in the next fifteen sectors of the empty first track.
Here's a link with a lot of detailed information about the standard MBR, An [Examination of the Standard MBR ( Master Boot Record )]("http://www.geocities.com/thestarman3/asm/mbr/STDMBR.htm")

Grub is actually installed in the Ubuntu file system, just as Windows boot loader (NTLDR), is in the Windows file system. The main parts of most boot loaders are far too big to actually fit inside something as small as a MBR.
They just write a little code in the MBR to direct the boot towards whichever boot loader it is you are installing.
When we say we are 'installing GRUB to MBR', or 'installing GRUB to the first sector of a Linux partition', we don't really mean _all _of GRUB.
It's just quicker to say that than it is to say we're installing the stage1 part of GRUB somewhere and possibly the stage1_5 as well.
>  There's a difference in the Xp recovery's 'fixboot' and 'fixmbr'  Windows XP's 'FIXMBR' restores the stage1 code for the boot loader NTLDR in the MBR, overwriting GRUB or whatever other boot loader was in the MBR already.
Windows 'FIXBOOT" is for restoring a corrupted Windows boot sector, the first sector of the Windows partition.

No boot loader should be touching a superblock, that's a term that has to do with file systems. I'm not quite sure I can explain that one really well, but I'll have a try. 
We have a super block at the start of our ext3 file system and it stores data about the rest of the file system. Since it is therefore very important, there's are a number of backup superblocks placed at regular intervals thoughout our file systems that can be used to restore the main superblock. 
If you want to take a look at your ext3 superblock, do
```
sudo dumpe2fs -h /dev/hda2 
```Where: your Ubuntu partition is partition number 2 in a PATA hard disk and it contains an ext3 or an ext2 file system. Otherwise please alter the command with something suitable for your particular set up.
>          I'm not currently having any issues, but I'm a seeker of knowledge ^^ Me too, I think it's good to try to understand all these terms and learn as much as I can. Maybe we can both help each other and get some of these technical terms ironed out.

 There are plenty of people around here who know a lot more then I do though, so if anyone can correct me or offer more information on these interesting matters, please join in, you are welcome. :)

Regards, Herman  :)

---

### Post by Herman on 2008-01-04
When we're booting an operating system with GRUB, there are three different ways we can do that.

We can 'chainload' the other operating system's boot loader by passing over control to it at the boot sector or the first sector of that operating system's partition. 

We can use GRUB's 'configfile' command, which reads the configuration file (/boot/grub/menu.lst usually), of another GRUB installation and uses the information from that to boot an operating system with.

Or we can boot the Linux kernel and initrd.img directly with GRUB.

Chainloading is good for when we need to boot an operating system that has a boot loader installed in the first sector of the partition. (I mean the stage1 part of a boot loader to be exact).
Windows systems always have a boot sector that can be chainloaded.
Linux operating systems don't usually have the boot loader installed in the first sector by default. It isn't necessary for Linux, we don't depend on the first sector. Linux boot loaders like GRUB can understand file systems, so they can find their own stage2 files wherever they are in the hard disk.
We can install a boot loader to the first sector of a Linux partition ourselves if we want to, and after that we will be able to chainload Linux.
That means we can boot with GRUB and if GRUB is in the first sector, it hands over the boot to another GRUB. If LiLo is in the boot sector (or rather the stage1 for LiLo), then GRUB will hand over the boot to LiLo. Syslinux is another boot loader that we can chainload to.

Configfile booting is an quick and easy way to boot another Linux with a similar version of GRUB. We don't need to install the other boot loader anywhere first, and we don't need to know the exact details of the other operating system such as the path and file name for the kernel and initrd.img because we're using GRUB to read the operating system's configuration file, (usually /boot/grub/menu.lst), and that configuration file should have that information in it.
Configfile booting only works when the other operating system has a similar version of GRUB, otherwise GRUB might not be able to understand some foreign configuration file or that confgiuration file might contain commands the version of GRUB we're starting with doesn't understand.  New versions of GRUB should be abel to boot older versions, but older versions of GRUB might not easily be able to use the menu.lst in a newer version of GRUB if there's commands in it it can't understand.

Both configfile and chainloader booting are good for multi booting another Linux, because when the other Linux has a kernel update, it's own boot loader's configuration file will probably updated to boot the new updated kernel.

Direct kernel booting is good when we know or can easily find out the exact path and name of our kernel and initrd. , or at least find symlinks to the kernel and initrd. 
When GRUB is installed in an operating system if direct boots the operating system it's installed in, and GRUB can also direct boot any other Linux operating system in the computer too. 
The 'stage2 part of GRUB which is located in a file systrem is the part that does the heavy lifting and loads the operating system's kernel into the computer's memory. The initrd.img is like a map or model of the file system that the kernel uses to help it get started. (I'm not sure about that part, but I think it's something like that, can anyone comment and correct me?)
Direct booting is the most reliable way to boot another Linux operating system when the other operating system might have a problem in the configuration file or doesn't have a boot loader installed in the first sector, or MBR.
GRUB can direct boot most if not all other Linuxes, and many other operating systems as well, but GRUB doesn't boot Windows.

I haven't had any formal education in computer science, I'm just learning as much as I can from reading other people's websites, books, and other people's posts here in Ubuntu Web forums and doing experiments myself. I hope everything I'm saying is correct or somewhere near correct.
Does anyone else have anything to add?

Regards, Herman :)

---

### Post by Herman on 2008-01-04
> I once had an incident where I couldn't recover the MBR for XP by any means (not via 'fixmbr' / 'fixboot') and fdisk /mbr or SGD - nothing would dispose of Grub, so I had to re-install Ubuntu, which was chaninloading XP in the first place. 

Now I want to figure out what's EXACTLY going on at the byte-level in the MBR... I mean, there's only 512 of them - should be possible to work it out I hope :]
If you install GRUB in your MBR and you want to uninstall Ubuntu, you should be able to restore your MBR with the FXMBR command in Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").
If that doesn't work for some reason and your computer onlt has one hard disk, then check in your BIOS settings and make sure the MBR antivirus or boot sector write protection is turned off. Also look in Windows and make sure you turn off any programs in Windows that might keep restoring your MBR, I'm not sure, but there are all kinds of programs around these days, anything is possible. 
More likely you have more than one hard disk, and the hard disk you're restoring the Windows loader to with Super Grub Disk and FIXMBR, isn't the hard disk your BIOS is booting. When people with SATA and PATA hard drives install Linux, often GRUB gets installed to the wrong hard disk's MBR. One easy way to solve that problem is to switch around the hard disk boot priority in the BIOS. If you did that and it was a long time ago you might have forgotten about it. Now if you want to make your computer boot Windows again, you might need to switch hard disks back again in your BIOS.
I'm only guessing of course, but those are a couple of ideas.
One more idea is to make sure you don't have a USB device or even a camera card in your computer when your try to restore the MBR, in case that's getting set up as the first hard disk and your boot loader is going to there instead of your real hard disk, but I don't think that's likely.

If you want to take a look at your MBR, you can.
Try this command,
```
sudo dd if=/dev/hda count=1 | hexdump -C
```Where: Your first hard disk is a PATA disk, if not, replace 'hda' with 'sda'.
That should give you a hexadecimal view of your MBR .
If you want to take a look at a boot sector, try
```
sudo dd if=/dev/hda1 count=1 | hexdump -C
```That would give you a view of your Windows boot sector if your Windows boot sector is 'hda1'.

Regards, Herman :)

---

### Post by perixx on 2008-01-05
WOW - thank you for all your info here Herman!
You sure put some effort in explaining things to me :-) 
thanks a lot! 
> An MBR is the first sector of every formatted hard disk and it isn't part of Windows at all.
An MBR contains an area for some boot loader code to be written in and another are reserved for the partition table for the hard disk.
That I was aware of ;) The term 'partition table' was the word I was searching for! Is this the area between the bytes 447 to 512 of sector 1 then?

> (I suppose the MBR would be sector 0 then, I'm not sure). -- from the link's site you provided to me:
>  This page examines the "standard" code (used by Microsoft prior to Windows 95B) that is written to Cylinder 0, Head 0, Sector 1 of your first Hard Drive  -- so it seems it's sector 1!

There are tools with which you can zero out either the MBR, the eMBR and/or one or all of the partition table entries - AFAIK, there are 4 of them (for each primary partition?). 
I think it was 'mbrworks' from Terabyte and 'MHDD'. Also, the 'dd' command can perform such actions, I've read somewhere. I haven't figured out what exactly the eMBR (enhanced MBR) is, yet. 

With the sticky-Grub-problem I described, I figured it might be possible to zero out the MBR (first 446 bytes), dispose of Grub Stage1 and leave the rest (of which I believe it's the partition table entry 1, that describes the beginning and end of the first partition) - if things are really as I think they are, please correct me if I'm wrong. After this step I could've retried to restore the nt-bootloader with 'fixmbr' (in the recovery console). I've read there's also a copy of the partition table stored somewhere, at least for the NTFS filesystem. 

**If I'm not mistaken, as long as the respective partition table to its partition is saved and can be restored (namely of Windows) you should be able to recover that partition in most other case than when it has been re-partitioned AND formatted?**

Btw., I actually had 2 drives of the setup you described, but disconnected the other (sda) one, while going through all the steps to restore the XP bootloader (also set partition active), so it should have worked and I don't think that Antivirus was turned on in BIOS. But this drive (PATA) was subject matter of a 33GB limitation problem I had to solve with 'HDAT2' and behaved a little weird ever since then, anyway.   

> In most cases you'll see that if you have Windows, it's first sector (boot sector), is most often located at sector 63. so this means, that if I do that
> Windows "FIXBOOT" (recovery console) is for restoring a corrupted Windows boot sector, the first sector of the Windows partition.... sector 63 is re-written?
Output from sudo fdisk -lu:
> Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          [COLOR="Blue"]63[/COLOR]    51263414    25631676    7  HPFS/NTFS


> If you want to take a look at a boot sector, try
**sudo dd if=/dev/hda1 count=1 | hexdump -C**
That would give you a view of your Windows boot sector if your Windows boot sector is 'hda1'. 
I'm no HEX-guru - do you know what this code does exactly?
If I'm 'reading' the output correctly, all it does is looking for the NTLDR file in C:\?

So do you mean, that generally the first 512 bytes of any other than the first partition is called (its) bootsector - or is there another space of 512 bytes (1 sector) before it, like the MBR in sector 1 of the HDD, containing the respective partition table? Or are all partition tables stored at the beginning of the HDD? 

When Grub refers to the superblock (speaks: when installing Grub to the superblock), does that mean installing Stage1 to the first or the second sector of the partition in question then?
Interesting: to compare the XP-bootsector with the Grub-bootsector...

**I'm using the nt-bootloader for chainloading Grub and Ubuntu in /hda5, for I've seen and experienced too much trouble with replacing the MBR code by Grub!**

Perhaps I've got to dig a little deeper into the MBR-page you've addressed me to :)

perixx

---

### Post by Herman on 2008-01-05
> That I was aware of :wink: The term 'partition table' was the word I was searching for! Is this the area between the bytes 447 to 512 of sector 1 then? Yes, basically, but it's only a little bit more complicated than that. 
One sector of a hard disk is 512 bytes and the first 446 bytes of the MBR contain some code for the boot loader  as well as one or two smaller but still important items. 
The next 64 bytes is the partition table. The partition table made up of four entries, one for each primary partition. 
Each partition table entry is sixteen bytes.
After that there's the 2 byte 55aa  disk signature.
446 + 64 + 2 = 512 bytes.

If you are going to use a 'dd' command on your MBR, then  I  would recommend limiting yourself to one like this,
```
sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1   
```That will make a backup of whatever bootloader code happens to be in your MBR at the time.

To restore it again,
```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1
``` That will restore a MBR (the boot loader code part only) from a previously made backup.

If you want to copy the entire MBR, (partition table and all),  you can. Just replace where it says 'bs=446' with 'bs=512'. 
However, I don't recommend that because if you save that and forget about it, you may make changes to your partitions. 
Then later some day you might come back and restore your whole MBR -*with the old partition table*-:(.
That could mean you might have a partition table that doesn't match up to where the current file systems actually are located in your hard disk. maybe partition 1 would be okay, but you might lose access to all your data in any other partitions in the hard disk, depending on what changes you made.
So don't make a backup of the entire 512 bytes. 
446 bytes is all you need.

---

### Post by Herman on 2008-01-05
> There are tools with which you can zero out either the MBR, the eMBR and/or one or all of the partition table entries - AFAIK, there are 4 of them (for each primary partition?). 
I think it was 'mbrworks' from Terabyte and 'MHDD'. Also, the 'dd' command can perform such actions, I've read somewhere. I haven't figured out what exactly the eMBR (enhanced MBR) is, yet. 

With the sticky-Grub-problem I described, I figured it might be possible to zero out the MBR (first 446 bytes), dispose of Grub Stage1 and leave the rest (of which I believe it's the partition table entry 1, that describes the beginning and end of the first partition) - if things are really as I think they are, please correct me if I'm wrong. After this step I could've retried to restore the nt-bootloader with 'fixmbr' (in the recovery console). I've read there's also a copy of the partition table stored somewhere, at least for the NTFS filesystem.  :) That shouldn't be necesary. 
There's no such thing as a 'sticky grub', it's a figment of the imagination and zeroing the boot loader area of your MBR would be a waste of time. You can try it if you want, but it won't be helpful.

The only thing you need to do to install a boot loader to MBR is to overwrite it with another boot loader.
There's no logical reason that I can think of to suppose that FIXMBR is able to detect the presence of GRUB and cares that GRUB's in your MBR and is too polite to overwrite GRUB. :)
Likewise, there's no logical reason that I can think of to suppose that GRUB has any special powers to resist being overwritten in the MBR. All we're talking about is some feilds of magnetic flux under the read and write heads on a hard disk platter. They're all the same.  GRUB's magnetic feilds are exactly the same strenght as the magnetic fields that represent all the rest of your data on the hard disk.

So the idea of  zeroing the MBR just doesn't make any sense to me.

You can try it if you really want to though. :)
I wouldn't pay money for a utility for that purpose though.

Regards, Herman :)

---

### Post by Herman on 2008-01-05
> If I'm not mistaken, as long as the respective partition table to its partition is saved and can be restored (namely of Windows) you should be able to recover that partition in most other case than when it has been re-partitioned AND formatted?:) Yes. As long as the important sectors at the beginning of a partition (boot sector and the file system blocks), don't get overwritten, then we have a Linux program called [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") that can scan your hard drive searching for anything that looks like the start of a partition and can bring those up to you for possible restoring to the partition table.

Here's a link with a diagram showing what the first few sectors of a partition are like, (schematically anyway), [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html"), scroll down to: 'Physical Structure', which is just a little below half way and take a look there. :)

I have used TestDisk myself a few times, once for real and a few times just for fun, or to demonstrate it to help others. I have a page about it here, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html") so you can see how it works without having to do it yourself. You can if you want to though, but I would leave well enough alone probably. :)
Unless you're like me and you're a little bit reckless. It's safer to practice on a hard disk that doesn't have important information on it until you get used to it. It doesn't take long to learn it.

---

### Post by Herman on 2008-01-05
> Btw., I actually had 2 drives of the setup you described, but disconnected the other (sda) one, while going through all the steps to restore the XP bootloader (also set partition active), so it should have worked and I don't think that Antivirus was turned on in BIOS. But this drive (PATA) was subject matter of a 33GB limitation problem I had to solve with 'HDAT2' and behaved a little weird ever since then, anyway. **AHA! **Now that might have something to do with it.
I'm reading some of [HDAT2's website]("http://www.hdat2.com/") for you now, but you'll have to give me some time.
I wonder if they set up a 'host protected area' for you that can stop the MBR from being written to? I will need more time to read thier FAQ and documentation.

---

### Post by Herman on 2008-01-05
>  so this means, that if I do that
     Quote:
                    Windows "FIXBOOT" (recovery console) is for restoring a corrupted Windows boot sector, the first sector of the Windows partition....            
 sector 63 is re-written?
Output from sudo fdisk -lu:
     Quote:
                                                 Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          [COLOR=Blue]63[/COLOR]    51263414    25631676    7  HPFS/NTFS                      
 Yes, normally that would be the case. 
That;s right. :)
At least the boot loader code in it would be, there might be other stuff in there as well.

---

### Post by Herman on 2008-01-05
>                               If you want to take a look at a boot sector, try
**sudo dd if=/dev/hda1 count=1 | hexdump -C**
That would give you a view of your Windows boot sector if your Windows boot sector is 'hda1'.                                 I'm no HEX-guru - do you know what this code does exactly?
If I'm 'reading' the output correctly, all it does is looking for the NTLDR file in C:\? That's right, it should give you a representation of your [COLOR=Red]first partition's boot sector[/COLOR] in hexadecimal code.

If you do,
[B]sudo dd if=/dev/hda count=1 | hexdump -C

[/B] and If you know what a MBR with Windows in it looks like and compare it with what one with Grub in it looks like, you will be able to recognize one from the other after that. So you can check.
Sometimes the FIXMBR command is working okay, but people don't know they are still booting off a different MBR maybe, or something else, and they think FIXMBR isn't working but it is. You can check with that command. :)
You don't even need to be able to read the code, you'll be able to find the word 'NTLDR' there somewhere, or 'LILO', or 'GRUB'.

EDITED thanks to perriix in post #19

---

### Post by Herman on 2008-01-05
> So do you mean, that generally the first 512 bytes of any other than the first partition is called (its) bootsector - or is there another space of 512 bytes (1 sector) before it, like the MBR in sector 1 of the HDD, containing the respective partition table? Or are all partition tables stored at the beginning of the HDD? The first sector of a hard drive is the Master Boot Record, and that has the partition table in it. (For the whole hard disk). That gives the details for the four primary partitions, or  three primary partitions and one logical.
I don't think these is a partition table in the boot sector of a primary partition, or if there is one then it doesn't seem to be important for anything. 
There are partition tables in the first sectors of logical partitions though, read here, [Minimal partition table specification ]("http://www.win.tue.nl/%7Eaeb/partitions/partition_tables.html")--> [Specification]("http://www.win.tue.nl/%7Eaeb/partitions/partition_tables-2.html") --> [2.4 Partition table structure]("http://www.win.tue.nl/%7Eaeb/partitions/partition_tables-2.html#ss2.4")

The first sector of every partition has a boot sector, but for Linux there is no boot loader code installed in it by default. You can install your own boot loader code there if you like. Linux doesn't depend on it for booting, 

Regards, Herman :)

---

### Post by Herman on 2008-01-05
> When Grub refers to the superblock (speaks: when installing Grub to the superblock), does that mean installing Stage1 to the first or the second sector of the partition in question then?
Interesting: to compare the XP-bootsector with the Grub-bootsector...That's a good question. :)
I think that's a mistake or a bad use of terms, but that's just my opinion.
Some of these terms are used interchangeably even by the experts, so it is confusing for us ordinary mortals.
I found a [Linux Dictionary]("http://tldp.org/LDP/Linux-Dictionary/html/"), but it doesn't have the word 'superblock' listed yet or I couldn't find it.

Referring again to this link: [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html"), if you scroll down to 'Physical Structure' again, and look at the same schematic diagram again, you'll see that there's a boot sector, followed by a series of 'block groups'.
Within each 'block group', there's a SuperBlock, File System descriptors, Block Bitmap, InodeBitmap, Inode Table, and Data Blocks.
That's what I think most people using the word 'superblock' usually mean. It's not the same thing as a boot sector at all. 
I googled it and all the pages I read seem to validate that use of the term.

So I think the source you are quoting is probably a bad example.

Regards, Herman :)

---

### Post by Herman on 2008-01-05
> **I'm using the nt-bootloader for chainloading Grub and Ubuntu in /hda5, for I've seen and experienced too much trouble with replacing the MBR code by Grub!**

Perhaps I've got to dig a little deeper into the MBR-page you've addressed me to :)
:) Well for most people, there's no problem with using GRUB as their boot loader , installed in MBR or wherever, and GRUB sets itself up automatically, and there's nothing you need to know. :)

Actually, it's trickier to get NTLDR to chainload GRUB than the other way around. 

Normally it's easy to restore the Windows boot loader to MBR or GRUB or LiLo or  do whatever you want with the MBR. :)

---

### Post by Herman on 2008-01-05
>  -- from the link's site you provided to me:
     Quote:
                    This page examines the "standard" code (used by Microsoft prior to Windows 95B) that is written to Cylinder 0, Head 0, Sector 1 of your first Hard Drive            
 -- so it seems it's sector 1!No, sector 0 !
This link, [2.4 Partition table structure]("http://www.win.tue.nl/%7Eaeb/partitions/partition_tables-2.html#ss2.4"), by Andries Brouwer,  says clearly that it's sector 0! :)

Regards, Herman :)

---

### Post by Herman on 2008-01-06
Hello again perixx,
Are you still there?  I just finished reading the HDA2 manual, it's available from that website in .pdf form, [HDAT2's website]("http://www.hdat2.com/") 
It is really, really interesting, I learned a lot of things I always wanted to know about hard disks, especailly about S.M.A.R.T., now I can read the output from my smartmontools software and understand it all a lot better! :)

Well I did find out something else interesting too. HDA2 is actually capable of 'offsetting' the MBR! 
When you have a 33 GB hard disk limit like you had, and you use HDA2 to make a 'host restricted area', (HRA) so the BIOS will only 'see' it as 33 GB, it can make the HRA  at either end of the hard disk.
If you select to have the HRA at the start of your hard disk, HDA2 software 'offsets' your MBR to one track before your user data area. 
Now I'm not sure if you made your HRA at the start of the disc or the end, but if you did make it at the start, then that explains why FIXMBR could not find your MBR. :)
Read page 74 of your HDA2 manual.

Oh, and according to the HDA2 documentation, the MBR is sector number1 of our hard disk, so I guess it depends on what we read or who we ask, :)
That's on page 138 of your HDA2 manual.

I am really happy I have that manual now, it has a lot of great info in it all about hard disks. It's interesting to me anyway, so I learned a lot from participating in this thread.

Regards, Herman :)

---

### Post by perixx on 2008-01-06
Hi again... so you're Mr. 'Hermanzone' ? :D
 Great page that is, and very helpful, especially with Grub errors! Thanks for stopping by and sharing your knowledge here in such a thorough way..!

> That could mean you might have a partition table that doesn't match up to where the current file systems actually are located in your hard disk. maybe partition 1 would be okay, but you might lose access to all your data in any other partitions in the hard disk, depending on what changes you made.
So don't make a backup of the entire 512 bytes.
446 bytes is all you need.
Hey! I think that's the reason why my 'bootsect.lnx' (I saved full 512 bytes) I used for the NT-chainloader-method ended up in a boot failure after I resized the Xubuntu partition on /hda5 (which was the location of the chainloaded grub) and therefore accessing a partition that suddenly had the wrong 'virtual partition table'...?

> I can think of to suppose that FIXMBR is able to detect the presence of GRUB and cares that GRUB's in your MBR and is too polite to overwrite GRUB. 
I don't think so :biggrin: But fact is, that Grub was staying persistent in spite of I've 'fixmbr'ed the MBR 2 or 3 times via the recovery console on that certain HDD.

> "If you want to take a look at a boot sector, try
sudo dd if=/dev/hda**[COLOR="Blue"]1[/COLOR]** count=1 | hexdump -C
That would give you a view of your Windows boot sector if your Windows boot sector is 'hda1'. I'm no HEX-guru - do you know what this code does exactly?
If I'm 'reading' the output correctly, all it does is looking for the NTLDR file in C:\?"
That should give you a representation of your Maser Boot Record in hexadecimal code. Sometimes the FIXMBR command is working okay, but people don't know they are still booting off a different MBR maybe, or something else, and they think FIXMBR isn't working but it is. You can check with that command.
Umm... I thought you wrote that ```
sudo dd if=/dev/hda count=1 | hexdump -C
``` is the corrct command for viewing the MBR itself, and /hda[COLOR="Blue"]**1**[/COLOR] for viewing the bootsector of partition1? They're showing different content, as to be expected. So, if I caught up with you and all, then 'fixmbr' won't affect the bootsector of partition1 at all, thus I'd have to use the command ```
sudo dd if=/dev/hda count=1 | hexdump -C
``` for checking the correct execution of 'fixmbr' (provided, that I used Grub for chainloading Ubuntu in something different than partition1)..?

> I just finished reading the HDA2 manual, it's available from that website in .pdf form, HDAT2's website
It is really, really interesting, I learned a lot of things I always wanted to know about hard disks, especailly about S.M.A.R.T. I am really happy I have that manual now, it has a lot of great info It's good to hear that I could contribute a small, humble part to increase your knowledge, even if only indirectly :]

> Now I'm not sure if you made your HRA at the start of the disc or the end, but if you did make it at the start, then that explains why FIXMBR could not find your MBR.
hehe... well, I just was in charge of recovering a friends messed up HDD - and quickly, for he was already low on patience when I arrived and was about to 'Nero' the drive :grin: So I had to fix up that little bug a.s.a.p. to prove what how good a technician I am and not to let him waste that otherwise nicely working HDD ^^ Hadn't done such a thing before and nearly stumbled over the 'small LBA' (8bit?) hurdle (t'was an 80 gig drive) that wouldn't work with 16bit-LBA setting naturally :-] 

perixx

---

### Post by Herman on 2008-01-06
:) Yes, I'm Herman from Hermazone. Nice to meet you, perixx :)
Sorry if I made a mistake or two there, I'll have a look back over what I typed in a minute and go back and fix any errors,

To clarify, you should be able to use FIXMBR to install the Windows boot loader to MBR and if you want to see if it worked for sure, (other than the obvious fact that Windows will normally boot), you could check with,
```
sudo dd if=/dev/hda count=1 | hexdump -C
```That's to look at the MBR. 
So if you think you installed NTLDR to MBR but then Windows still didn't boot, (Grub comes up again, or else you get some other error message), you can use that 'dd' command take a look to see what's going on, maybe your hard drives are switched somehow, by some other problem. (IDE cables, jumper settings, BIOS settings, or something).

... maybe FIXMBR is working but your BIOS is trying to boot a different hard drive, maybe FIXMBR is working but going to the wrong hard drive? You might need to take a look at your hardware or do some more troubleshooting to investigate.

For the boot sector, if Windows is partition number 1, then you can look with ```
sudo dd if=/dev/hda**1** count=1 | hexdump -C
``` to see if FIXBOOT worked or not. Normally it's easier just to try to boot Windows and you know it worked, but if for some reason Windows still doesn't boot and you're not sure if FIXMBR worked , then that's when the 'dd' command can be useful.
If you know what the output should look like when it's normal.

It's not very often that the Windows boot sector requires any attention, normally it's the MBR that most people are interested in.
Once in a while someone types a wrong command when they are trying to re-install GRUB to a partition and they install GRUB to the Windows partition by accident. Then you might need FIXBOOT.

> hehe... well, I just was in charge of recovering a friends messed up HDD - and quickly, for he was already low on patience when I arrived and was about to 'Nero' the drive :grin: So I had to fix up that little bug a.s.a.p. to prove what how good a technician I am and not to let him waste that otherwise nicely working HDD ^^ Hadn't done such a thing before and nearly stumbled over the 'small LBA' (8bit?) hurdle (t'was an 80 gig drive) that wouldn't work with 16bit-LBA setting naturally :-]  I know what it's like, I got caught with the 33 GB BIOS hard disk limit with my old PC Chips Book PC myself! I didn't know about HDAT2, probably it wasn't around yet then, it's still under development by the looks, still in beta. It seems like good software though, would be better if it was GNU/Linux. Anyhow, my solution was simple, I went and bought a 30.0 GB hard drive for the book pc and an USB external drive caddy for the 40.0 GB one. It cost me more money, but I have a useful USB external drive for making backups, so I haven't done too badly. I learned a  little about BIOS hard drive limitations before I gave up and bought the smaller drive though. :) He-he.

Regards, Herman :)

---

### Post by perixx on 2008-01-07
> maybe FIXMBR is working but going to the wrong hard drive?
That might be, perhaps! I am not sure if my friend maybe had the drive letter D:, or rather, that both drives were connected, I logged into the right disk/partition, but that one was labelled 'D:' - so there might have been a NT-bootloader, left with pointing to an empty Linux partition :) 

I'm glad that you made me understand the trick with the first 446 bytes and I'll try to just save that part of the bootsector next time - though I'm not perfectly sure if saving the smaller version of the bootsector of a Linux-partition (say: hda5) will make any difference along with my nt-bootloading. I don't know if it's Grub that is directly pointing to a 'hardcoded' point in hda5 then.
 
Should the Linux-partition really change in size and location, I suppose that Grub still looks up the partition table (being updated by the Grub-installer each time) as a reference and uses the information there to always automatically jump to the right location, no? 

Or am I perhaps mistaken here?

perixx

---

### Post by Herman on 2008-01-07
> That might be, perhaps! I am not sure if my friend maybe had the drive letter D:, or rather, that both drives were connected, I logged into the right disk/partition, but that one was labelled 'D:' - so there might have been a NT-bootloader, left with pointing to an empty Linux partition :) Well, that owuld be the most common reason for people with ordinary setups to think re-installing the boot loader isn't working, (if they have more than one hard disk), is because they're installing it to a MBR other than the one they are booting from.
You said you used a program to make a 'Host Protected Area' in the hard disk.
 I'm just guessing from the information you have provided and from my interpretation of the HDAT2 manual, but it seems possible that you could have used HDAT2  to offset the MBR to somewhere in the middle of that hard disk. There's no guarantee that FiXMBR can find it. It's fairly common for different programs to have slightly different ways of dealing with hard disk geometry. 
 I'm only guessing, but that seems to me to be a likely possibilty. :)

> I'm glad that you made me understand the trick with the first 446 bytes and I'll try to just save that part of the bootsector next time - though I'm not perfectly sure if saving the smaller version of the bootsector of a Linux-partition (say: hda5) will make any difference along with my nt-bootloading. I don't know if it's Grub that is directly pointing to a 'hardcoded' point in hda5 then.For that I still think you can use 512 bytes. If you experiment I think you will find out that if you move the Linux partition you'll lose the boot of Linux when you're booting with NTLDR, and you'll have set set everything up all over again anyway. 
> Should the Linux-partition really change in size and location, I suppose that Grub still looks up the partition table (being updated by the Grub-installer each time) as a reference and uses the information there to always automatically jump to the right location, no?  GRUB does look at the partition table, but GRUB contains quite a sophisticated collection of programs that can do all sorts of things more than that. GRUB can actually scan your hard disk and search for a file, that's one way GRUB can work. So it doesn't depend on hard disk geometry most of the time. 
If you want to, you can make your own GRUB floppy disk or CD and do a few experiments with GRUB to prove that, and lots of other amazing things as well. GRUB is almost a mini operating system by itself.
For instance, no matter if you boot up GRUB in a CD, floppy disk, CD or installed in a hard disk, you can use GRUB commands to find things in your hard drive.
You use GRUB to scan your hard disk and find a file with a certain name. You can use GRUB to open plain text files so you can read the information in the file too. That's because GRUB can understand file most file systems. (Well, it doesn't make any effort to understand NTFS,but it understands most other file systems). 
Here are a few links explaining some fun projects you can do, to learn a few of the tricks GRUB can do,  [Grub Grotto]("http://www.troubleshooters.com/linux/grub/index.htm") by Steve Litt, [GRUB tips and tricks]("http://www.freesoftwaremagazine.com/articles/grub_intro/") by Jeremy Turner, [Boot with GRUB]("http://www.linuxjournal.com/article/4622") by Wayne Marshall, Linux Journal.

Regards, Herman :)

---

### Post by perixx on 2008-01-08
Hi Herman!

Perhaps I'll have a look at those programs you spoke of  some other time, when I feel like it... there's so much to learn about Linux in general and booting systems is just a small part of it, though an important one I admit ;) 
Mostly I have to deal with booting if I change my system setup or re-install sth. or something is broken with my or acquaintances' systems.
 
In the meantime I always try to learn new things about Ubuntu, optimize my system or I have some work to attend do. Or do a little game even :-] 

The problem with Linux is, that running something special consumes so much time for each single step, for most things are still just so foreign about this OS to me. Many things are easily configurable once you get the hang of it - but the approach in ironing out specific problems is really time-consuming and awkwardly difficult in most cases, as you need to understand how the system really works and this tends to eat up too much time and effort compared to the outcome - 
I often feel like re-inventing the wheel every time over and over again ^^ 
Unfortunately, even if I succeed, it often turns out not to be rewarded with the performance I'm expecting (such as installing graphic drivers).
**EDIT:** **driver problem solved** OpenGL up and running again!

I know this is slightly off-topic here... just a bit frustrated currently with trying to refloat my graphic card's rather mediocre direct rendering capabilities (it's the driver, what else) :¬|

> re-installing the boot loader isn't working, (if they have more than one hard disk), is because they're installing it to a MBR other than the one they are booting from.
I don't think I installed the MBR (containing the NT-bootloader) to a different HDD - it was installed to the respective HDD's MBR on D:\ - 
I thought you meant that the MBR will be configured by the command 'fixmbr D:' in such a way as to look for Windows on drive D:\ (when 2 drives are connected during the process), even if I boot this drive as a single one (with the 'C:\'-drive disconnected) in the future, thus Windows actually being on 'C:' but the MBR is still pointing to 'D:' (like partition 2 / 'hda2)... or maybe I have something misunderstood here :]

> You said you used a program to make a 'Host Protected Area' in the hard disk. Ah, maybe you've been mystified by my words :) 
To be honest, I was confused by those things when I first used this program... as far as I can tell, there are HPA's (hidden protected areas) which are created by reducing the drive's native max. address 
(which was limited with this drive for some unknown reason - I fixed it by restoring the native max. address, using the 'LOW-LBA-bit'-mode, not 48-bit) 
and there are hidden partitions (like recovery partitions), but I'm not perfectly sure if those are not sth. different...

Btw., I was surprised that you can use Grub sort of like a command-line file manager, though I saw some commands like 'find' and such in its list of commands. But I never really figured out how to make use of those, for I lack the patience to work myself throught dozens of manual pages for something I consider only as a means to an end :^) 

perixx

---

