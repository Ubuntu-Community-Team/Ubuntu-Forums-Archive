---
title: "Moving Ubuntu Install to new HDD"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by ffxr on 2007-02-09
My Problem.

I want to move Ubuntu to a different HDD..

Does anyone know of any tips/tricks i can use to ease this process...  installing a fresh ubuntu build on the other disk is an option, but to install all the progams/packages & updating configuration is gonna take  ages.. i am just wondering if anyone can think of any ideas for me to speed this up..?

i have 3 HDD , all have one partition each (except the xubuntu one which has two - the default swap disk)

30gb NTFS (win xp & win media centre ) -saving anything on this drive is unimportant
11gb ext3 (xubuntu) - want to keep data
160gb NTFS-3g (filestore) - NEED to keep the data

what i want to do is:

format my 30gb drive in ext3 & install/move my current ubuntu build to it
format 11gb drive in NTFS and install Win Media Centre on it (just for emergencies)
convert my 160gb NTFS-3g drive to ext3 

any suggestions at all?

thanks!

---

### Post by ffxr on 2007-02-10
just one bump to see if ANYONE is interested in making ANY comment at all?

---

### Post by Patrick K on 2007-02-10
Here is my thread on a similar plan. [http://www.ubuntuforums.org/showthread.php?t=354095](http://www.ubuntuforums.org/showthread.php?t=354095)
While I was doing something a bit different the results are very close to what you want.
Notice the problems I had with GRUB. When you use gparted it may rename the partitions and effect grub. 

I would leave the 11gb drive to last and format the 30gb first. Make a compressed backup of the 11gb drive (your current Ubuntu installation) and decompress it on the 30gb drive after formatting it as EXT3. At this point you are still running on the 11gb. 
Where you will run into problems (along with probably others I can't foresee) is booting to the 30gb. Grub will need to be made aware ot it. You could replace the Win boot option with the new Ubuntu boot data in  /boot/grub/menu.lst (be sure to observe the way grub addresses different boot partitions (HD0,0 and hda,1 are the same partition. Both forms are used by grub. Study menu.lst to see where they are used). This way you can boot to it and get it running before deleting the old installation. So at this point you could boot to Ubuntu old or Ubuntu new. The Win option would be gone.

Once you are satisfied that the new install is working right, I'd backup the data off the 160GB drive then format it to EXT3 and restore data. 

Lastly, after making sure grub will boot the new install, I'd edit menu.lst to remove the 11gb drive so at this point only the new install is on it. Then pull the the 30 and 160 drive out, actually just unplug the power to them, and install Media Center on the 11gb drive. Once that is installed, I'm not sure what will happen when all drives are plugged in. I think Grub may freak out so you'll likely need to boot to the livecd and run gparted to get the partition names. Then, hopefully, you can edit menu.lst from the livecd. However, I don't know that this will work. It all depends on what the 11gb drive is named and if it changed any other names. On the other hand, Grub may boot to you new installation just fine.

Once you are back in linux, you can edit menu.lst to include the Media Center partition. How it will run, I cannot guess, I run W98 and have never used XP or any of it's derivatives. 

Anyway, that's how i would approach it. More than likely making adjustments as needed along the way. Hope this help, even if it only encourages someone with more experience to correct it with a better way.

---

