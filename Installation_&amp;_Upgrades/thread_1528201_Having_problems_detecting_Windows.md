---
title: "Having problems detecting Windows"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by HBAndrew on 2010-07-10
Hey guys, been a long time Windows user, I finally want to give Linux a proper go on my main rig see what it's capable of.

Anyway, I am currently running Windows 7 x64, simple setup, used the Windows setup to wipe drive, create a partition using all space and install. I also have a second drive used for storage, games etc.

I have shrunk the Windows partition using disk management in Windows and made 48gb of unallocated space and have burnt ubuntu x86 to CD, it boots up fine and everything works, but when I go to install, on the partitioning screen I think it is showing my storage drive and not my Windows drive so it says no operating systems detected.

I have tried going into bios and disabling my storage drive (Windows drive shown connected to SATA1, storage shown as SATA2), yet when I load up ubuntu, I can still access all the data on it and the setup still comes up with my storage drive.

Is there something I am missing for when there's more than one SATA drive? Should I just unplug my storage drive, install, then reconnect when done?

Specs
ASUS P5Q Mobo
Intel Core 2 Quad Q6600
ASUS ATI Radeon HD 4850 512mb
Corsair 4GB DDR2 800MHz/PC2-6400 Dual Channel
300GB Maxtor DiamondMax Plus10 SATA2 (Windows drive)
Seagate ST31000528AS 1TB Hard Drive (Storage drive)

Also here are some screens of the partition during install, and some warning gparted is giving on my NTFS partitions.

[Partition screen]("http://i26.tinypic.com/2vluqrm.jpg")
[gparted main window]("http://i27.tinypic.com/2w50rpu.jpg")
[gparted warning]("http://i32.tinypic.com/2ywcm6r.jpg")

Any help appreciated, I really wanna give Linux a try, but don't want to ditch Windows to do it.

---

### Post by dino99 on 2010-07-10
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Pumalite on 2010-07-10
Leave averything as it is and at the time of installation; in step 7 ( I believe), go to 'Advanced' and make sure that Grub installs to 'dev/sda'

---

### Post by HBAndrew on 2010-07-10
Thanks I will give that a try, however I am still curious as to why the installer isn't automatically detecting my Windows partition and why gparted is showing warnings for my windows partition.

I disconnected my storage drive leaving just my Windows one, and the install doesn't detect any data on it at all and just wants to format the entire thing.

EDIT: Thanks Pumalite, I will give it a try before downloading another ISO, I have an Acronis image of my drive if things go wrong anyway.

Does that mean I choose partitions manually, use the unallocated space, and when at step 7, just install grub to dev/sda? But if gparted and the setup can't detect my Windows install properly, how will it properly install grub onto that partition?

---

### Post by HBAndrew on 2010-07-10
Ok this time it seemed to detect the Windows loader, and when selecting to automatically use largest free space it went onto installing, but it quickly came up with an error saying "The ext4 file system creation in partition #5 of Serial ATA RAID nvidia_hjabaajg (linear) failed." Though I don't know why it's called nvidia_hjabaajg, googling that shows up nothing.

I then went to try creating the partitions manually (it also doesn't detect the Windows loader again), making / primary and ext4, swap, and /home at the beginning as ext4, but on the installing screen gave me the same error.

[This]("http://i30.tinypic.com/ht5gmw.jpg") is when I get to the partitioning part and select largest continous free space.
[This]("http://i28.tinypic.com/1rdjqa.jpg") is the confirmation of tasks.
[This]("http://i30.tinypic.com/25a6vyv.jpg") is when it errors.
[This]("http://i32.tinypic.com/2yzjznn.jpg") is the resulting partitions when I then go back and choose to create partitions manually, don't get why it tried to create an ntfs partition.

Think I will have to go ahead and download an alternate ISO as mentioned in dino99's post and do it that way :/ just don't get why I am having so much trouble.

---

### Post by mikewhatever on 2010-07-10
Have you tried running a file system check on your Windows/NTFS partitions? It's advisable to do it before resizing. Also, make sure you shut down Windows properly (don't suspend to disk or anything like that).

---

### Post by Pumalite on 2010-07-10
Are you sure you don't have a Raid System?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by HBAndrew on 2010-07-11
Thanks, didn't know I had fakeraid and no way to disable it it seems.

I used the alternate copy, got the message "One or more drives containing Serial ATA RAID configurations have been  found.  Do you wish to activate these RAID devices?" and selected yes, however after selecting my partitions and setting them to / swap and /home, it gave the same error as before "The ext4 file system creation in partition #3 of Serial ATA RAID  nvidia_hjabaajg (linear) failed." 3 is /, 4 is extended, 5 is swap and 6 is /home.

I set / as a primary partition and bootable, made an extended, and put swap and /home in there as logical ext4 (not sure if that's the right way to do it). I have read people have gotten ubuntu and vista dual boots working with this troublesome motherboard, but no specific guide on how.

---

### Post by HBAndrew on 2010-07-13
Ok I figured it out, used PartedMagic to create an extended with all the free space, made a 2gb swap and used rest for ext4 logical, then booted from LiveCD, mounted ext4 as / and set grub to install to dev/wrapper/nvidia_hjabaajg and it installed fine.

Everything seems to be good except graphics drivers, installed fglrx using Hardware Drivers, but it seems I don't have 3D acceleration installed/enabled as playonlinux keeps telling me (yet I got all the compiz effects working fine) and can't find why. Even got latest ATI drivers from their site and installed them but no change. Ubuntu just doesn't like my computer heh.

Thanks for all the help, at least it's up and running now, though unusable for me without 3D acceleration.

---

