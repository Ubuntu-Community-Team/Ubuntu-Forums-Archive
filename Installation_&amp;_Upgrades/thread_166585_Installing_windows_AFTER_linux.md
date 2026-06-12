---
title: "Installing windows AFTER linux"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by blakeivey on 2006-04-26
I have ubuntu installed on a 160gb hard drive, and I want to install windows on my other 120gb hard drive. I have searched and searched but all i can find is people saying to install windows first. I really don't want to do that since it would require a lot of backing up. There has to be a way to do this, does anyone know?

I try installing windows and I get an error saying the second hard drive doesnt have a compatible windows xp partition. 

Could someone please walk me through on how to install windows XP AFTER Ubuntu? 

Thanks, 
Blake Ivey
[http://korea.blakeivey.com](http://korea.blakeivey.com)

---

### Post by sinkxdie on 2006-04-26
Format your 2nd HD's partition to NTFS

---

### Post by jpkotta on 2006-04-26
You didn't search very hard.  I searched "install windows" in the wiki, and found this: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

You can just install Windows as normal.  When it complains about the other hard drive being unreadable, it's just being stupid and you can ignore it (make sure you never tell it that it's OK to format your Linux partitions).  When it wants to format the drive that it will be going on, that's fine, format away.  After installing Windows, your MBR is mangled (because operating systems other than Windows are inferior and there is no reason to dual boot).  Use the wiki page to recover.

In any event, the only way to lose your Linux installation is to format the partitions.  Overwriting the MBR does not destroy Ubuntu (it just means you can't boot it until you fix it).

---

### Post by zgerrz on 2006-05-09
I am having the same issue as the thread starter while trying to install windows on my second hard drive.

How can I let windows "ignore" this error? I can't find a way to get around this part. Windows keeps complaining about it not being a windows compatible partition.

---

### Post by confused57 on 2006-05-09
I'm not sure,  these threads may help(note the instructions by "lha"):

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)
[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

---

### Post by zgerrz on 2006-05-09
So it seems like I MUST have windows installed to hda? I have been trying to install it first on hdb, and just now on my sda (recognized as my 3rd drive). Both options didn't work for me.

It's strange because about 8 months ago I was in the same situation and I'm fairly sure I was able to install windows to a drive other than my first one.

So is it possible to install windows to a second or third drive?

---

### Post by confused57 on 2006-05-09
Did you try just having your 2nd hd connected as the master drive when installing windows?  After installing windows, switch the cable to Ubuntu as master, windows as slave, then make the grub entry for windows on the Ubuntu drive as suggested in the threads.

---

### Post by zgerrz on 2006-05-09
OK, I'll try that whole thing tomorrow.

I was initially thinking of doing a swap like that, actually. I didn't go through with  it because I thought it may mess up my Ubuntu installation as well. Anyway, I'll post back tomorrow with my results. Thanks for your help this far.

---

### Post by zgerrz on 2006-05-10
OK, everything worked out great. I can dual boot Linux and Windows correctly now. Thanks for your help.

---

