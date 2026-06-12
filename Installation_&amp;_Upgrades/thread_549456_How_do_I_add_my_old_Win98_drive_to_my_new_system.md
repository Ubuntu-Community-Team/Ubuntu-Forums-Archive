---
title: "How do I add my old Win98 drive to my new system?"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Seamless in Northampton on 2007-09-12
Hi all--

Just completed phase 1 of setting up a new machine. I have a dual boot system set up with WinXP and Ubuntu (which so far I absolutely love). I have a system partition and data partition for each OS on a single SATA drive. 

Now I need to add one of my old IDE drives to the mix (it contains massive amounts of audio from recording projects which cannot easily be transferred any other way). The old machine is dual boot WinXP and Win98 with PowerQuest Boot Magic, and contains WinXP on one IDE drive, Win98 and data partitions on a second IDE drive. I need to add the drive with Win98 and data to my new machine.

I am concerned that the Win98 partition may cause me some troubles. If I simply remove all the files and folders on my Win98 partition, will I be good to go into WinXP or Ubuntu and use that partition for data? Or will the 98 boot info remain on the partition and screw me up? I would try uninstalling Win98, but I have read repeatedly that doing so on a drive which has been repartitioned since initial install (mine has) usually results in total data loss, and data preservation is absolutely crucial.

Is there a better way to go about adding this drive? My goal is to retain the currently Win98 partition as merely a FAT32 data partition to share between Ubuntu and WinXP, while leaving the drive's other (NTFS) data partitions untouched.

Thanks!

---

### Post by Pumalite on 2007-09-12
I would do it as an external drive. But, that's my opinion and my taste. I''m sure there will be other ideas.

---

### Post by logos34 on 2007-09-12
All you have to do is hook it up to the primary IDE channel on your new machine,* perhaps change the jumper on the back to master (I'm guessing it was slave before), and format the windows98 system partition using either Gparted in linux or from within XP disk management (do a full, not quick, format).  You don't have to make it fat32 either: ext3 would actually be a better choice since [fs-driver]("http://www.fs-driver.org/") will provide read+write support for ext2/3 from within XP.

Then add an entry for it to fstab.

*if your new board has only one IDE channel and your cdrom is on it, then obviously it will have to go in as slave.

---

### Post by maybeway36 on 2007-09-12
I believe XP's boot loader is on the win98 drive.

---

### Post by logos34 on 2007-09-12
> **maybeway36 said:**
> I believe XP's boot loader is on the win98 drive.

Good point.  If that is the case then the OP will have to reinstall the windows boot loader from the recovery console on a XP install cd.

---

### Post by Seamless in Northampton on 2007-09-12
Thanks for the good suggestions so far. 

Pardon my newbiness, but how do I add an entry for it to fstab?

---

### Post by Seamless in Northampton on 2007-09-12
> **logos34 said:**
> Good point.  If that is the case then the OP will have to reinstall the windows boot loader from the recovery console on a XP install cd.

Would XP's boot loader be there because of using Boot Magic for the dual boot?

And logos34, I was with you except for "OP"-- what's that? :)

I'm wondering as well about a partial repeat of my method for achieving Ubuntu/XP dual boot--I partitioned the drive in XP using Partition Magic, and when I rebooted to install Ubuntu, all I had to do was edit the mount points. Perhaps I can use my old computer's XP to move the Win98 partition's data files I need, reformat the partition, and then plug into my new system.

---

### Post by logos34 on 2007-09-12
> **Seamless in Northampton said:**
> Would XP's boot loader be there because of using Boot Magic for the dual boot?

Never used it so can't say.  If you can't boot XP after removing the win98 drive you'll obviosuly have to rewrite some bootloader to the XP disk, whether boot magic, XP's own, or whatnot.  You may even have to run fixboot and fixbmr, as well as copy ntdetect.com and ntldr to XP partition, because if you installed it with the win98 drive connected at the time it may have detected the latter C: drive as the 'active' partition and put the boot files there.   Go to XP support for more info.

> 
And logos34, I was with you except for "OP"-- what's that? :)

'OP'= you! (shorthand for original poster)  :)

> I'm wondering as well about a partial repeat of my method for achieving Ubuntu/XP dual boot--I partitioned the drive in XP using Partition Magic, and when I rebooted to install Ubuntu, all I had to do was edit the mount points. Perhaps I can use my old computer's XP to move the Win98 partition's data files I need, reformat the partition, and then plug into my new system.

Either way...You can use linux to copy them off the partition, it doesn't really matter.  

Do you have NTFS-3G? If not, you really should get it.

But one thing about PM: I've heard it said in these forums that it doesn't mix well with GParted.  That may or may not be true, maybe it's in the documentation, not sure.  So you might want to just switch to gparted full time for all your formating needs, or else use windows own tools for making fat32 and ntfs partitions.  Just something to consider.

To edit fstab:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Seamless in Northampton on 2007-09-13
Thank you for all the very thorough help. I went back into my original XP install and reformatted the Win98 partition. So far, with the old IDE drive installed in my new machine, everything is working as I had hoped, and I have more partitions than you can shake several sticks at, and everything is booting as it should in Ubuntu. Now I'm off to see if XP works properly. I think I've got it solved!

---

### Post by Seamless in Northampton on 2007-09-13
My drive is now successfully in use, but I have one follow-up question. The new drive partitions first appear in the list of folders as something like "6.0G yadda yadda," then when I click on them, they become drive1, etc. and become visible on the main Ubuntu screen. This isn't particularly annoying, since I will seldom be using these partitions in Ubuntu, but is there something in need of fixing here?

thanks!

---

### Post by tech9 on 2007-09-13
win98 ... is that still around? :lolflag:

---

### Post by logos34 on 2007-09-13
> **Seamless in Northampton said:**
> The new drive partitions first appear in the list of folders as something like "6.0G yadda yadda," then when I click on them, they become drive1, etc. and become visible on the main Ubuntu screen. This isn't particularly annoying, since I will seldom be using these partitions in Ubuntu, but is there something in need of fixing here?

You need to add it to fstab.  See link bottom post #8.

---

### Post by Seamless in Northampton on 2007-09-13
OK--looks easy enough. Will this procedure leave my data untouched? Sounds like it, but I want to be sure, with such vital stuff sitting on one of the partitions!

thank you!

---

### Post by logos34 on 2007-09-13
> **Seamless in Northampton said:**
> OK--looks easy enough. Will this procedure leave my data untouched? Sounds like it, but I want to be sure, with such vital stuff sitting on one of the partitions!

thank you!

you could tack on a 'ro' option to the fstab entry so the partition mounts read-only.

more here
[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I can't imagine that mounting the partitions would, by itself, cause any data corruption

---

### Post by Seamless in Northampton on 2007-09-13
> **tech9 said:**
> win98 ... is that still around? :lolflag:

Only for those of us who insist on running incredibly modified old flight simulators like Red Baron 3D that don't do too well in a different OS! :D 

But Wine, here I come...

---

