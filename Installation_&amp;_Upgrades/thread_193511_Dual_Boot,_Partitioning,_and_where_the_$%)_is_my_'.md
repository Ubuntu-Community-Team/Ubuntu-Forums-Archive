---
title: "Dual Boot, Partitioning, and where the $%*) is my 'Share Partition?'"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Dorv on 2006-06-10
Ok, so I'm a recent (i.e., today) ubuntu convert.  Well, maybe not so much of a convert as a test the water with my big toe kind of guy.

I wanted to try Dual Booting for a while on my HP laptop.  I already had my HD partitioned such that there was a bunch of extra space, and I wanted to leave a FAT32 partition for sharing stuff back and forth.

I setup everything correctly, as far as I can tell, and have access to the drive...  

But, I have some questions...

First off, my Windows XP drive has an Icon on the Desktop, and is available in 'Places' (and thus, easily accessable from programs like RhythmBox). 

*  How do I get that Windows XP drive off of of the Desktop
*  How do I get that "Share" partition available in all of the places that the other drive is?

Here is, if it helps, the revelvant line in /etc/fstab

/dev/hda4       /mnt/osshare     vfat    user,iocharset=utf8,umask=000 0 0

Thanks in advance for helping out this Linux noob...

---

### Post by Herman on 2006-06-10
>  * How do I get that "Share" partition available in all of the places that the other drive is?Hello, Dorv, You might need to create a new directory in /media to mount your FAT32 data partition in. Diretories in /media with mounted filesystems tend to automatically have an icon on the desktop.
```
sudo mkdir /media/osshare
``` The edit /etc/fstab with the new directory:
```
 /dev/hda4       [COLOR=Orange]/media/osshare[/COLOR]     vfat    user,iocharset=utf8,umask=000 0 0
``` That should at least give you the icon on the desktop. You might have to reboot for it to appear. 

>  * How do I get that Windows XP drive off of of the DesktopYou could make a new directory for it in /mnt and then alter your /etc/fstab entry accordingly as you did for your FAT32 partition and remove the directory called 'hda1' (usually) afterwards. Filesystems mounted in directories in /mnt aren't given desktop icons. 
It is also possible to make a new directory (folder) for any partition inside your /home/username directory and edit /etc/fstab to mount the filesystem in that instead. That's a good idea, your desktop will be nice and tidy, and you'll still have easy access to the partition and all it's files.
Please post agian if there's anything there you want more help with, but I'm going to sleep for a few hours now. I'll check later to see if you're okay.
Regards, Herman :D

---

### Post by Dorv on 2006-06-12
That nailed it...  For the most part.

Until my whole laptop choose to crash last night.  Can't get the WinXP to boot at all, and the Ubuntu boots and runs slow, with several 'port failures' and other mean sounding things going on the screen. 

I think its most likely my HDD failed, or the memory is bad...  Either way, I'm thanking my stars I actually paid for the extended warranty for a change.

---

### Post by Herman on 2006-06-12
Dorv, I'm sorry to read you have more problems. You might like to try the [memtest86+]("http://users.bigpond.net.au/hermanzone/p15.htm#Memtest86") from your GRUB menu to see if anything's wrong with your RAM modules.
Also try checking 'PC Health Status' in your BIOS, like in fig5, [this link ]("http://www.users.bigpond.net.au/hermanzone/p1.htm")( And scroll to the bottom)  I had the power supply go on my old 'Book PC' and I found the problem with that. Really it could be anything I guess.
I hope you can fix it easily. Maybe it just needs a good clean-out.

Try running a Live CD and run the command 
```
sudo badblocks /dev/hda
``` if you get a list of bad blocks it could mean your hard drive is on the way out. No results means OK. Here's a link to a good thread on that. [*click here*]("http://www.ubuntuforums.org/showthread.php?t=124774&highlight=sudo+badblocks").

 Regards, Herman.

---

