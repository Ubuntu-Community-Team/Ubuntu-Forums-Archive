---
title: "Dualboot struggles with GRUB"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by emrys1 on 2005-11-15
So I made a post about three days ago about this problem but no one responded and so I will try again with some new information.  

I install Ubuntu as a dual boot fine.  It works great until I boot into Windows.  Once I log in to Windows and then reboot the system, it goes into a continually rebooting loop.  

It appears that Windows is affecting the MBR somehow because if I don't log in and just reboot from the Windows login screen, the system reboots fine.  

I am able to use LILO fine.  Any ideas why GRUB and Windows are dueling it out?

---

### Post by aysiu on 2005-11-15
Maybe [reinstall Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113)?

---

### Post by emrys1 on 2005-11-15
Thank you for your reply.  

I am able to reinstall GRUB but that doesn't fix the problem.  It only allows me to boot up again.  This is a good solution until I want to go back into Windows---once I reboot from Windows, the problem re-manifests itself (I can then reinstall GRUB if I want but I will still encounter the same problem).

---

### Post by aysiu on 2005-11-15
It could be a Windows problem then that has nothing to do with the Master Boot Record. Is it possible that your boot.ini or some other Windows configuration file got corrupted somehow?

---

### Post by emrys1 on 2005-11-15
It is quite posisble that the boot.ini file in Windows has become corrupt.  We work with Altiris and sometimes when that pushes out an image, the boot.ini file gets corrupted and we have to push out a new boot.ini file.  

I am still interested in other responses but I will look into the corrupt boot.ini idea--thanks!

---

### Post by aysiu on 2005-11-15
I'm interested in other responses, too. I've never heard of this problem before.

---

### Post by emrys1 on 2005-11-16
Alright, I am able to repair the MBR using the Windows utilities on the install disk but it produces the same results as if I reinstall GRUB (except that it doesn't recognize the Linux partition).  Once I boot into windows using the new boot.ini that fixing the mbr produces, I am able to reboot as many times as I want without problem.  However, when I install GRUB, the problem returns.  Interesting.

---

### Post by vipzz on 2005-11-23
I have got the same problem here...

And as i can read on this forum quite a lot of people have this issue...

Unfortunately all threads about this issue have died...

Could anyone please give us an answer...
I have to reinstall grub every time i have booted into windows!!! That gets very annoying...

Grub does show up for a very short time...You can see a loading grub message...After that it's rebooting!

Please anyone..

Cheers..

---

### Post by yesplease on 2005-11-23
As a workaround it may help to put Grub on a USB stick or on floppy, you can use the method in this thread [http://help.ubuntu.com/starterguide/...html#id2521253](http://help.ubuntu.com/starterguide/...html#id2521253) . Your floppy is /dev/fd0.
In the BIOS bootup sequence you can put floppy first.

I am not sure if this works in the cases described above. This may help if windows does not interfere with the floppy. 

I boot from floppy and this setup automagically survived a dist-upgrade and kernel-upgrades.

---

### Post by Circleback on 2005-11-23
This also happened to me as well. I think if you boot up with the windows install CD you can issue the command "fixmbr" (forgot the actual command) and you can boot up to windows as normal. Not sure about the boot.ini file though. Seems like the best option with this distro would be to boot from floppy, USB or CD as stated above.

---

### Post by AgentZ86 on 2005-11-24
Please descibe your partition information please

how many drives and partitions and any extended or logical drives etc. ?
Please advise

Is your you windows installed on an ntfs file format or a fat32 ?

Is windows installed on partition 1(hda1) etc. 
Do you have any other windows installed or was your system already dualbooting with windows and another windows OS along side of it?

Please advise

I'll try to help if I can.

---

### Post by emrys1 on 2005-11-28
I think my problem is with the Altiris deployment solution that we use here at work.  I originally was working on an imaged machine and had been struggling with this problem over and over again on the images that I push out.  Someone recomended that I try a fresh install of windows and so I did--I haven't seen the problem since.  

I have windows on sda1 and Linux on sda2 and 3 (sda2 is Ubuntu, sda3 is swap).  

I am now able to dual boot with Ubuntu and Windows (though we'll see how well it works once I push out an image to all the lab machines).

---

### Post by yesplease on 2005-11-29
When Grub is not on the mbr of the windows disk, you can let windows determine what is on the mbr of the windows disk.

So when Altires rewrites the mbr of the windows disk it wont overwrite grub. 

(Perhaps Grub can handle that new situation. In case Grub doesnt understand the new mbr, all you have to do is take the floppy out and boot from the windows disk to get into windows, and rewrite grub on the floppy to handle the new situation.)

Did you try the workaround of writing Grub on another medium?

---

