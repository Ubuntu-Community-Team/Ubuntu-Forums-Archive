---
title: "One OS per drive, please"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by Meekle on 2009-12-20
I have win7 running and want Ubuntu on 2nd physical drive.  Been reading the forums and haven't found anybody else with a similar situation which surprises me.  Everybody says 'partition, partition!'.  Some threads say use windows partitioning to shrink drive, others say to use GParted during install.  And another says that Grub2 is screwy in U9.1 so I should use 9.04 and make 5 partitions and copy Grub settings to a logical partition 0 blah blah blah... OK I'm lost and confused as hell and I didn't even want to do it that way to begin with.
I had win7 installed on one drive, then unplugged it and installed U9.1 - this is probably what ended up fouling my whole system anyway, but what's done is done and now it is undone.  I had to choose which drive to boot into during startup and all was well for a while.  I used Ubuntu for day to day activities, and used it for probably a month - updating, downloading software that I wanted to experiment with, etc.  So when I wanted to boot back into win7 to load up my recording software and make some music, I could no longer do so.  Even though I was choosing my win7 drive, Grub would start loading and I'd find myself back in Ubuntu.
I should probably mention that my win7 drive was originally a RAID0 config.  When the fail happened, I ran -fdisk and it looked like the first raid drive had been split into some weird chunks and the 2nd raid drive was being reported as having 180000Gi !?!
I dont know what the hell happened, but I dismantled the raid setup and am now using those drives separately.  I reinstalled win7 on 1st drive (they're both 250G Sata2.0) but I am nervous about doing the dual boot the way I did it before - I don't want to have to reinstall everything again next month.
I should probably also mention that I'm using 64bit versions of both OSes.

Now that raid is out of the picture, what should I do to get a stable 2boot setup?

Thank you all in advance, sorry for the rambling :)

---

### Post by darkod on 2009-12-20
To be honest, I lost you around after the second sentence. :)
Yes, dual booting with 2 drives is pretty common. And you will have a stable setup.
If I understood correctly you are not using raid any more and you already have win7 on one drive. And you want ubuntu on the other. So....
Set the ubuntu drive as first choice in boot order in BIOS (I'm talking about hdd priority, it needs to be first just between your both drives). But keep the cd-rom before hdd device to boot from cd first.
Boot with ubuntu cd, Install Ubuntu option, in step 4 of the installer tell it to Erase and use whole disk. Both your drives are 250GB so be very careful which disk you select as destination. And if they are from same manufacturer their model numbers might even be equal. In worst case, disconnect the windows drive to make sure it doesn't get selected as destination.
The abve mentioned option will install ubuntu taking all of your hdd. If you want more specific setup you will have to use manual partitioning in step 4 but you need more knowledge about the process. If you know how to do that, I always prefer manual partitioning.
And that's it. Boot ubuntu few times to make sure it's working fine. If the windows drive was disconnected, connect it and make sure the ubuntu drive is first boot option in BIOS (or you will boot your win7 directly).

---

### Post by falconindy on 2009-12-20
I have some experience with this recently. In case this helps, this is what I've discovered after installing Windows7 and Arch Linux side by side.

Windows7 will blindly install its boot loader to the first physical disk it finds, regardless of whether or not its the same as the drive you're installing the OS to. I found this out the fun way when I unplugged a drive and GRUB would no longer boot into Windows.

Unlike previous versions of Windows, the bootloader can coexist in the MBR with Grub. In fact, it **needs** to (like some sort of parasite). The whole "install Linux last" mantra that used to exist is no longer necessary.

Recovering the Win7 boot loader (if you ever need) is easy. Boot off the install CD and just follow the repair instructions. One catch: It may claim that it worked the first time and it won't have made a difference. Reboot off the CD and run the repair again.

Disclaimer: This was all done using Grub 0.97, and not Grub2. YMMV.

---

### Post by Meekle on 2009-12-20
Thanks, both of you.  I'll try again.  If no worky; I'll throw a new machine together and get a KVM...  There aren't any KVM issues with Ubuntu, are there? :D

---

### Post by PheonixAsh on 2009-12-20
Did this for a friend recently and the following has always worked for me.
I'm starting from a blank machine so bare with it.

1. Set desired windows drive as boot drive in bios.
2. Boot and install windows on this drive.
3. Set desired Linux drive as boot drive in bios.
4. Boot and install Linux, ensure you put the boot loader on that drive too. during install setup you could add mount information for windows drive if needed

pros of this solution are:
-grub knows of windows installation and should be able to boot it (not tried it for win7)
-windows boot-loader left in tact for jic(just in case) proposes.

---

### Post by Meekle on 2009-12-21
I got it all up and running and am now happily using firefox to post my reply.  Thanks again everyone, hopefully I won't have any more problems. Yeah, right.

---

