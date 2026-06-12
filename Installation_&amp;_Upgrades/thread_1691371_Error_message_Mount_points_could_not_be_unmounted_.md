---
title: "Error message: Mount points could not be unmounted /cdrom"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by Jeaux on 2011-02-19
I have XP installed with a wubi installation of 10.04.  My CDROM is shot so I'm using Unetbootin to install from XP to a new partition.  I recieved some help in a diff thread that might be help for history albeit a short one. 

[http://ubuntuforums.org/showthread.php?t=1691317](http://ubuntuforums.org/showthread.php?t=1691317)

During installation it stops with error message that a mount point could not be unmounted    /cdrom.   

Many thx,
Joe

---

### Post by Dutch70 on 2011-02-19
Ok...over 45 min & you've only had 1 view, and that was me...lol.
 So, let's check this out.

1. How did you partition your hdd? 
2. What is the 57MiB, FAT16 Partition?
3. Where is your "swap" partition?

Also, please give the link to the tutorial you're using, if you have one.

---

### Post by Jeaux on 2011-02-19
LOL thx Dave.

OK I started this by inside XP making some space.  Then ran chkdsk, then defrag.  Went to Disk management and tried to resize partion but couldn't.  So converted to dynamic drive.  Tried to resize again and couldn't.  So I deleted a partion that was 5G and downloaded Unetbootin.  Choose ubuntu and 10.04 live and installed.  Rebooted and choose unetbootin as boot option.  Loaded into ubuntu and clicked the Install Ubuntu 10.04.2 LTS icon from the desktop.  Then got to the partition management step 4 of 8 page that you helped me with.  

In terms of tutorials I've just piecemealed this together from knowing what's going to go wrong from my Wubi installation (i.e. a graphics problem) to reading the forums when problems arise.  

I've since tried to use the directions found at 

[http://ubuntuforums.org/archive/index.php/t-1237721.html](http://ubuntuforums.org/archive/index.php/t-1237721.html)

but when executing the "sudo umount  -l -r -f" command in the terminal I get this:

Usage: umount -h | -V
       umount -a [-d] [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-d] [-f] [-r] [-n] [-v] special | node...

idk and suggestions?

---

### Post by Jeaux on 2011-02-19
[LEFT]After examining what was posted in the thread [http://ubuntuforums.org/archive/index.php/t-1237721.html](http://ubuntuforums.org/archive/index.php/t-1237721.html) 
I discovered a mistype.

He write:
This is from my previous thread
[http://ubuntuforums.org/showthread.php?p=10241015](http://ubuntuforums.org/showthread.php?p=10241015)

and when you look at that thread it says "sudo umount -l -r -f /cdrom"  instead of "sudo umount -l -r -f"  So I tried that and got new error messages.  YAY making progress lol.

The error was that Ubiquity has crashed.  I ticked the box to not notify me again of it crashing and tried to install again.  The installer now just stops running.  I googled ubiquity and found out it is a graphic live CD installer.  Any suggestions?
[/LEFT]

---

### Post by Dutch70 on 2011-02-19
Whoa, you're not doing a typical dual boot install that I'm familiar with. 

First, what version of windows are you using?

Do you currently have ubuntu installed inside of windows programs & features via wubi? If so, you can use the start up disk creator to create a livecd/usb, (as opposed to unetbootin) which you can boot to, or install with.

Here's a good tutorial(from scratch) that may make life much easier...
[[COLOR="Blue"]http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/[/COLOR]]("http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/")

Just noticed you have XP, check out this link...
[[COLOR="Blue"]http://www.psychocats.net/ubuntu/partitioning[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning")

Another great website ...of course.
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")
There is more there than the download.

---

### Post by Jeaux on 2011-02-19
That would be great Dutch but I've gone and screwed myself.  After following the directions in the forum post I specified earlier now I can't boot into XP.  It starts and then crashes.  Besides I can't make a CD because the CDROM is shot.  I started Gparted and it says that my XP partition is mounted on /cdrom  wth?  How do I fix that?

---

### Post by Dutch70 on 2011-02-19
> **Jeaux said:**
> That would be great Dutch but I've gone and screwed myself.  After following the directions in the forum post I specified earlier now I can't boot into XP.  It starts and then crashes.  Besides I can't make a CD because the CDROM is shot.  I started Gparted and it says that my XP partition is mounted on /cdrom  wth?  How do I fix that?

Really hate to hear that. This thread has some valuable info...
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1687855&page=2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1687855&page=2")

You don't need a cd, your live usb stick, created with unetbootin should work fine. isn't that what you're running on now? 

If you can't save xp, you may be able to access & save your most important files with your unetbootin live usb. Go to places>home folder> on the left, you should see your computer name. I included a pic of where I access my Vista files from my Compaq computer. Then click> users> your login name, and see if you can get to your docs, pics, etc.

---

### Post by Jeaux on 2011-02-20
No I'm not running off a USB stick.  I read an article that described installation with NO removable storage.  So that's what I did.  In Unetbootin there's an option for the creation of a USB or straight to harddrive.  I choose harddrive and then C: was the only option left.

Here's the display of what Gparted looks like now.

---

