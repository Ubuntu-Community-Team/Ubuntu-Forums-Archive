---
title: "Grub Installation failed on external hard disk"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by nightwolf2k5 on 2009-12-12
Hi everybody,

Due to a lot of complications on my current hard drive I have on my laptop, I wanted to install Ubuntu on my external hard disk.
While I did try use the make startup USB disk creation option, I found that ubuntu was a lot more unstable when it ran with that option.

So I tried to go ahead and install ubuntu on my external hard drive.
I set that the bootloader be installed on my external disc sdb.
The installation went on fine till about 92%. When it tried to install the grub, it quit with a fatal error.
Is it possible for me to manually install grub on my external hard disk and use Ubuntu as an installed OS in my external disk?

Thanks in advance.

---

### Post by wilee-nilee on 2009-12-12
You can install on a external Hd but it will run slow the transfer rate is not real high. You can also do a full install on a thumb with the live CD just make sure that grub is installed on the thumb by hitting the advanced button on the final install gui. You have to also choose the manual install option, and you would need a thumb of 8 gigs to get the best use. 

When you tried the install on the HD did you point the bootloader with the last gui at the HD?

---

### Post by nightwolf2k5 on 2009-12-12
I actually did the steps you mentioned..
I selected the external disc (sdb in my case) to install the bootloader (using the advanced tab on the gui)..
The installation then proceeds to about 92% and a fatal error occurs when the grub is being installed.. :(

---

### Post by wilee-nilee on 2009-12-12
I am wondering if you aren't having hardware problems, if the internal HD is having problems are you sure that is the culprit, and have you done any memory checks from the grub boot when you had a distro installed? Can you just use the live CD and get a normal testing setup?

---

### Post by Bartender on 2009-12-12
Do you have another HDD or a test PC you can play with?  

I'm wondering if the CD is corrupt.  Did you burn it really fast?  Is it a good quality CD-R?  If the disc works just fine to install Ubuntu on another PC, or on your PC with a test HDD temporarily plugged in, then we'll know it's not the disc.  But I have a vague recollection that I've read more than one thread over the years that described failure at 92% and it's been a faulty CD.

Another thing to try is the alternate install CD.  The main advantage of the LiveCD is the ability to "test-drive" Linux.  If you know you're going to install, many folks have said the alt-install CD is more reliable than the LiveCD.  You end up with the same product, it's just the alt-install CD uses less resources to install Ubuntu.  The interface isn't quite as shiny as the Live, but it's not a command-line warzone either.  I've used the alt-install CD plenty of times and I'm no genius.

Try booting from your existing CD again, and use the "Check Disc for Errors" option and see what happens.  This isn't 100% foolproof, but it's usually a good check to see if the disc is good.

---

### Post by nightwolf2k5 on 2009-12-12
well.. the real complication with the internal hdd is that it has an "official windows installation" thats meant for my work.. now.. they have strict guidelines against modifying anything on that hdd..
so.. I figured I could use an external disc..

As for the issue of it being a problem with the live cd.. well.. I am certain that it isn't..
I had installed ubuntu on my pendrive.. and it worked..
but.. my pendrive is slow and also ran out of space (after a few updates).. so i figured it would be better to run ubuntu on the faster hdd (external) and set up a nice big partition so that I can update it as much as I want :)

but.. I think i'll try again with another cd just to be sure..

on the other hand.. is it possible to install the bootloader manually?

---

### Post by darkod on 2009-12-12
> **nightwolf2k5 said:**
> well.. the real complication with the internal hdd is that it has an "official windows installation" thats meant for my work.. now.. they have strict guidelines against modifying anything on that hdd..
so.. I figured I could use an external disc..

As for the issue of it being a problem with the live cd.. well.. I am certain that it isn't..
I had installed ubuntu on my pendrive.. and it worked..
but.. my pendrive is slow and also ran out of space (after a few updates).. so i figured it would be better to run ubuntu on the faster hdd (external) and set up a nice big partition so that I can update it as much as I want :)

but.. I think i'll try again with another cd just to be sure..

on the other hand.. is it possible to install the bootloader manually?

Depending how far it got the first time. You could use the same instructions like for restoring grub2 but that is just restore function and relies on the cofig files to already exist on the hdd. In your case the config files might not have been created at all, but you can give it a shot.
There are some instructions here which also include commands to execute if your grub.cfg file doesn't exist, which is probably your case. Look under 2) Using Ubuntu 9.10 liveCD:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by nightwolf2k5 on 2009-12-12
thank you darkod..
I tried to follow your steps but the behaviour i got for each of the commands was all weird..
I did check some other threads on the grub and while running one of those commands, I am not sure which, I saw that the external disk (sdb) was recognised as hd1..
So I figured that I would just go ahead and try the installation again, but this time the difference between my previous modes of installation were:
1) I did not manually set the partitions. I used gparted before and went ahead and partioned a fat32 section of 280gb and left 10gb as unallocated (free space).
2) Selected my external hdd during the installation and chose the install on the largest free space option.
3) Using the GUI, I chose the option to install the bootloader in HD1 (instead of using the dropdown to select sdb).

Now, I leave it up to the ubuntu gurus to figure out which of the above solved my problem... 
I would leave a suggestion to the folks at ubuntu to make installation of the grub on an external device more reliable. I find it absolutely amazing that now, I can basically use ubuntu on all my computers/laptops.
The best part is that I can do it, not as a live user but as a full fledged user.

With this, I am sure a lot more people will try Ubuntu on their external hard disks.

---

### Post by darkod on 2009-12-12
> **nightwolf2k5 said:**
> thank you darkod..
I tried to follow your steps but the behaviour i got for each of the commands was all weird..
I did check some other threads on the grub and while running one of those commands, I am not sure which, I saw that the external disk (sdb) was recognised as hd1..
So I figured that I would just go ahead and try the installation again, but this time the difference between my previous modes of installation were:
1) I did not manually set the partitions. I used gparted before and went ahead and partioned a fat32 section of 280gb and left 10gb as unallocated (free space).
2) Selected my external hdd during the installation and chose the install on the largest free space option.
3) Using the GUI, I chose the option to install the bootloader in HD1 (instead of using the dropdown to select sdb).

Now, I leave it up to the ubuntu gurus to figure out which of the above solved my problem... 
I would leave a suggestion to the folks at ubuntu to make installation of the grub on an external device more reliable. I find it absolutely amazing that now, I can basically use ubuntu on all my computers/laptops.
The best part is that I can do it, not as a live user but as a full fledged user.

With this, I am sure a lot more people will try Ubuntu on their external hard disks.

I'm glad you got it sorted out. I didn't quite understand the part about the 280GB FAT32 you created and the 10GB unallocated space. If you planned to use 280GB + 10GB and use the Largest Free Space option, do NOT create any partitions in advance. Especially not NTFS/FAT32. That option will use just the unallocated space. Space belonging to any type of partition, even with no data in it, is not considered unallocated.
I am saying this mostly for other people reading this thread.

---

### Post by Bartender on 2009-12-12
I also was thrown by the part about formatting almost the entire external as NTFS.

Is that what you really wanted?  

If your intent was to use most of the external as a data partition that both OS'es could access, then I guess you did OK, although I woulda set aside at least 25GB or thereabouts for Ubuntu...

---

