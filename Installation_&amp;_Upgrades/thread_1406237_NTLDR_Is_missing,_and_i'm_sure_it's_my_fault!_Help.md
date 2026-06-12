---
title: "NTLDR Is missing, and i'm sure it's my fault! Help!"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by SoSoLost on 2010-02-13
So i WAS running windows xp, sp2, and just simply ran wubi to install ubuntu 9.10 on my laptop. Everything went fine as far as i could tell, although i did the install because xp took up some 25 gigs of my 30 gig hard drive, and i'd read that linux runs on WAY less memory. well, everything went well, was able to recover the necessary files to the ubuntu partition (only 5 gigs), and so i TRIED TO CLEAR UP SOME SPACE AND DELETE THE FILES FROM THE WINDOWS PARTITION, INCLUDING THE OPERATING SYSTEM! Upon reboot, i get the "ntldr is missing, press ctrl+alt+delete to restart" message. So i used someone else's computer to make a damn small linux live usb, which is what i'm using now, but anything i do to try and get at the grub which was installed fails. to put it very simply, how do i get my ubuntu back, and delete windows (which blows in my opinion)? Oh, and i don't have access to a cd burner to run a live ubuntu cd, my usb drive is only 1 gig, so i can't run a live usb, and my "minus" button isn't working either...

---

### Post by darkod on 2010-02-13
If you used wubi you probably don't have grub on the MBR of your hdd. So you wouldn't be able to boot it.
Does Damn Small Linux have the fdisk command? If it does run:

fdisk -l

to show you your partitions, if all are ntfs then wubi is inside windows. Also, I think you should be able to create ubuntu bootable usb on 1GB stick, the ubuntu image is only 690MB.
Look on google for XP repair cd, that might help you get ntldr back. Or if you have XP cd just repair the boot process, instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by SoSoLost on 2010-02-13
ok i managed to boot off of the live usb, works great. now we have another problem. I still have about 10 gigs of music and documents, some of which are in the old windows file system, some were moved into the ubuntu filesystem from the install. The ones from the ubuntu install are not visible from the live usb, the ones still in windows are. is there a way for me to create a partition of some of the free space (about 17 gigs), dump the files and ubuntu install in there, then go back and delete the partition that had windows? When i look in gparted it shows just one big fat ntfs partition.

---

### Post by darkod on 2010-02-13
I'm not sure, I don't know much about wubi. It is installed inside windows in sort of image, the root disk is actually one big file C:\ubuntu\disks\root.disk and I have no idea if you can look inside at all.
As you noticed yourself you can easily copy the files from windows, but not from inside wubi. That's why I don't recommend it and never use it personally. If you used dedicated partition you could copy what you need from there.

But you could try to repair the XP boot and hopefully get the old boot menu back which can allow you to boot wubi (ubuntu) and you can copy what you need.

---

### Post by oldfred on 2010-02-14
You can mount the root.disk from Ubuntu liveCD if you want to recover data.

** 	 How-to: Recover files from Wubi install with LiveCD  **
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

---

