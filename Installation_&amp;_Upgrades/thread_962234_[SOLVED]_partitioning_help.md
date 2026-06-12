---
title: "[SOLVED] partitioning help"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by heman22union on 2008-10-29
Hello this is my first installation of Ubuntu. I have an 80gb hdd and I want to divide it up as follows 2 10gb partitions one for 8.04 Ubuntu Desktop and the other for Ubuntu Server, 59gb for Data, and 1gb for Swap. Here is what I had in the manual partition setup. [IMG]http://i292.photobucket.com/albums/mm17/heman22union/Ubuntu/IMG_1574.jpg[/IMG]

and this is the error it gives me. [IMG]http://i292.photobucket.com/albums/mm17/heman22union/Ubuntu/IMG_1575.jpg[/IMG]

any ideas?

Thanks
-heman

---

### Post by cyfur01 on 2008-10-29
If you're installing Ubuntu Desktop at the moment, change "/UbuntuDesktop" to "/". That way as far as the desktop installation is concerned, that partition is the root of the filesystem. 

This will be local to the Desktop installation. Thus, you can reconfigure the mount points of each partition when you do you Server installation, and it will have no effect on where the Desktop installation will mount things.

---

### Post by heman22union on 2008-10-29
ok i kind of understood what you said can you go into more detail using exactally what i should put. and another thing what about dual booting server/desktop what do i have to do to enable that?

---

### Post by cyfur01 on 2008-10-29
Going from your screenshot, when installing Ubuntu Desktop, the only thing you need to change is the mount point of "/dev/sda1". It should be changed from "/UbuntuDesktop" to "/". This way, when you launch Ubuntu Desktop, it will use /dev/sda1 for its filesystem, and will mount the server partition to "/UbuntuServer".

When you install Ubuntu Server, manually configure your partitions. For the first ext3 partition (which should be your Desktop installation), select it, the highlight "Use as:", then select "Ext3...", then highlight "mount point:", select "Enter manually" and set it to "/UbuntuDesktop". **Do not format this partition, or else you will delete your desktop installation!** Select the second ext3 partition (which should be your Server partition), and you will probably have to go through the same procedure, but select its mount point as "/" so that it will be the root directory for the Server installation. Also make sure to format the partition. For the third ext3 partition (which should be your Data partition), again modify it so that it will mount to "/Data". Finally, you may have to follow a similar procedure to set up the swap partition properly, although I think it's smart enough to use swap partitions as swap. 

When the server install gets a ways further with its installation, then it should tell you that it was able to recognize the Desktop installation and that it wants to set up grub with the MBR. Accept this, and it will set up the dual booting. Do note that this will set up the boot options in the "/boot" folder of the **Server** partition, not the Desktop partition. Thus, if you update the kernel headers of the desktop installation, you will manually have to change the corresponding entries in "/UbuntuServer/boot/grub/menu.lst". This is pretty simple to figure out (you usually just change a couple numbers), and if you're worried about breaking the file, first create a backup copy:```

sudo cp menu.lst menu.lst.old
```The alternative is to reset grub to boot from the Desktop partition after the server install is complete, which I'm not completely sure how to do.

After all is said and done, reboot and you should have the option of booting into either Ubuntu installation. If you run server, there should be a "/UbuntuDesktop" folder with the Ubuntu Desktop files in it, and vice versa for the Server installation.

---

### Post by heman22union on 2008-10-29
well i ended up installing 2 partitions one at 79gb and one 1gb swap. i can resize those to set up the server right? and should i have 2 swap files or just one?

---

### Post by heman22union on 2008-10-29
well i ended up installing 2 partitions one at 79gb and one 1gb swap. i can resize those to set up the server right? and should i have 2 swap files or just one?

---

### Post by fendres on 2008-10-29
One swap should suffice. You can resize. Resizing should be a safe operation, but you never know. And since failure is drastic (data loss if not backed up), I'd prefer to plan ahead.

---

### Post by heman22union on 2008-10-29
so would you guys recomend deleting all the partitions and then installing desktop then server...

---

### Post by cyfur01 on 2008-10-29
I've yet to have any issues with resizing.

If you've just installed Ubuntu and don't have any sensitive data, try resizing the partition. At worst, you'll just have to delete the partitions and restart.

---

### Post by heman22union on 2008-10-31
Well I ended up installing Kubuntu bacause I'm more familiar with kde because I am familiar knoppix. Here are the correct partitions setup.


[IMG]http://i292.photobucket.com/albums/mm17/heman22union/Ubuntu/IMG_1578.jpg[/IMG]

thanks for all your help.

---

