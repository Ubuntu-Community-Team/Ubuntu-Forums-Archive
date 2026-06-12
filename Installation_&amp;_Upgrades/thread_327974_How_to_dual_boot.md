---
title: "How to dual boot"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by kost@s on 2006-12-30
Hello guys!

I m new in Ubuntu but it seems I wanted to go into deep right away :-)

My laptop had already WinXP installed, which I wanted to keep and at teh same time use Ubuntu. So, during Ubuntu installation I chose the option "resize IDE1master etc etc and use free space". Everyting OK, Ubuntu was installed but every time I boot my PC there is no dula boot option to choose between Win and Ubuntu. How can I see a dual boot screen? I guess the WinXP are still in there, right? Thnx a lot!

---

### Post by Sef on 2006-12-30
I think you might have installed Ubuntu as the only OS on your computer.   

To find out:

1) Open the terminal (Applications > Accessories > Terminal) and type in the command in #2.

2) ```
sudo fdisk -l
```

3) Copy and paste the results of it here.

4) Here is mine:

sef@jokat1:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.0 GB, 20060135424 bytes
255 heads, 63 sectors/track, 2438 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks        Id    System
/dev/hda1   *           1        1094     8787523+  83   Linux
/dev/hda2            1095        2310     9767520   83  Linux
/dev/hda3            2311        2438     1028160   82  Linux swap / Solaris

5) Yours should have an NTFS listed under System.  NTFS is Microsoft's propriatery file system.  If NTFS is not listed, then you overwrote Windows and would have to reinstall it.

---

### Post by rovernaut on 2006-12-30
When you did the install did you install Grub on the MBR?

---

### Post by Sef on 2006-12-30
> When you did the install did you install Grub on the MBR?

GRUB would have had to be installed in order to boot into Ubuntu.

---

### Post by kost@s on 2006-12-30
Thnx for you fast reply!! Here is mine

[PHP]kostas@kostas-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13999   112446936   83  Linux
/dev/sda2           14000       14593     4771305    5  Extended
/dev/sda5           14000       14593     4771273+  82  Linux swap / Solaris
[/PHP]

As you said, there are no Win inside! But was that supposed to happen since I choose the option for resizing the Win disk space and install Ubuntu on the rest of the disk?

Anyway, so, let's say I erase everything, I install Win again and then again Ubuntu! Which option should I take during the installation?

Thnx!

---

### Post by kost@s on 2006-12-30
Hmmm...I didnt install GRUB....Didnt know....I have no idea actually :S

---

### Post by DougS on 2006-12-30
I'm no expert but from my learner's knowledge

Use Fdisk to create a partition for Windows AND LEAVE FREE SPACE FOR UBUNTU etc.
Windows must be installed first (arrogant as assumes no other OSes exist!)
Then can install Ubuntu into free space using option on Live CD, Grub should also install and then you will have menu to select either system. Ubuntu will be default but that can be changed.

Also suggest you consider having separate partition for your data (FAT32 - accessible by Win & Ubuntu) so that you can work with both systems and apps in parallel to get used to them both.

NTFS partitions not as easy to access reliably?

Can anyone else confirm this strategy please...?

---

### Post by logos34 on 2006-12-30
yeah, a fat32 partition is a popular approach (max file size 4gb though), but if you just want to be able to read your linux partition from windows then get Explore2fs (works on x86 only).

Its probably best to do a full (vs. quick) format before installing winxp again.

I HIGHLY advise you to make a separate primary partition for /home so you can upgrade or reinstall more easily.

You might want to check these out:

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo](https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by kost@s on 2006-12-30
Thnx everybody for your input...
OK, so maybe it is better indeed to make a FAT32 partition as well....So, how many partitions should I make, if I make it manually? 1 NTFS for Win, one FAT32 and then one ext3 and one swap for my Ubuntu? Is the ext3 going to be my /root one?What about my /home one? Are they the same? My disk is 120GB, so how much should I allocate to each?
Too many questions I know :( But at least it starts being more clear now :) Thnx again....

---

### Post by logos34 on 2006-12-30
You can even write to ntfs partition with NTFS-3G 

[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

but I think it's still considered half-baked at this point (what DougS was referring to).  

there's a howto somewhere in the ubuntu wiki that talks about it if i'm not mistaken

---

### Post by Bartender on 2006-12-30
I'm thinking download the GParted LiveCD (GPLCD), burn to a bootable CD, use it to wipe out the existing partitions, then build one primary partition as ntfs, one primary partition as ext3, and one extended partition with swap and perhaps a FAT32 and maybe even /home inside the extended.
Toss in the Windows CD and tell it to install in the primary NTFS partition.

Wouldn't that work?

kost, I really like GPLCD because it gives you a graphical map of what you're doing.  Very reassuring.  Watch for my PM.

---

### Post by logos34 on 2006-12-30
you can have up to four primary partititons, one of which should be an extended partition which you can then subdivide into as many logical partitions as you desire (put the /swap inside that like bartender says...that's the typical setup).  you might also consider a small partition for /boot.
But having your /home as a primary or inside an extended partition separate from you system files means that when you do a fresh install of, say, feisty fawn then you can format your ext3 /root partition and put it there and not have to worry about backing up your /home directory because your documents and personal settings are saved on another partition.

---

