---
title: "I need help fast please..."
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2005-10-02
Alright. I just downloaded Ubuntu, however I accidently installed it on my 120 GB Hard Drive that had my Windows XP Pro on it. I had thought I lost all data, because I told the installer to format the drive. To my relief, it kept Windows and all my files, and there was the option to boot into Windows. It worked then, but now I don't see a option to do that. I only booted into Windows once since I installed Ubuntu on that drive, then I restarted my computer, installed Ubuntu on my secondary 20 GB Hard Drive, used it for a few hours, and then I wanted to go back into Windows to burn a few files to transfer over to Unbuntu. There wasn't an option. I have no idea how to get to my files. Most are able to be thrown away, but my Apache server files, and all of my web documents, cannot be lost. I have spent too many days of my life coding to have it all lost.

This is what it outputs when I try to boot from the unfinished Ubuntu on my 120 GB Dirve (the one with all my files):

root (hd0,0)
Filesystem type unknown, partition type 0x7
kernal /boot/<other stuff here>
Error 17 - cannot mount selected partition.

Is there any way I can access my files? I know they arn't gone, even if Windows is corrupted, but I can't get to them. i can't even boot the Ubuntu on that hard drive - I never finished installation on that drive and I'm affriad to restart it just in case it does erase everything.

This is my first experience with any kind of Linux... any help is greatly appreciated.

---

### Post by aysiu on 2005-10-02
This will help you get your files for now:

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

For the error you get, one of these might help:

[http://ubuntuforums.org/showthread.php?t=11359](http://ubuntuforums.org/showthread.php?t=11359)
[http://ubuntuforums.org/showthread.php?t=294](http://ubuntuforums.org/showthread.php?t=294)
[http://ubuntuforums.org/showthread.php?t=58174](http://ubuntuforums.org/showthread.php?t=58174)
[http://www.ubuntuforums.org/showthread.php?t=47920](http://www.ubuntuforums.org/showthread.php?t=47920)

---

### Post by XtremeGamer99 on 2005-10-02
Thank you very much!

Well, not that I got the files that I need, can someone explain to me what mounting it? I'm all very new to Linux and the Filesystem, so I'm basically just learning.

---

### Post by aysiu on 2005-10-02
I wrote a guide, which is everything I wish someone had told me when I started Linux: [http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

It has a quick glossary in it, too, which includes *mount*

---

### Post by Emerzen on 2005-10-02
Let me try to recap to see if I understand first:

-You have two harddrives, hda 120GB (master), and hdb 20GB (slave/external). 
-Windows lives on hda and you started to install Ubuntu there, then stopped and rebooted   into windows but got far enough that GRUB was installed onto your MBR.
-You then installed Ubuntu onto your 20GB hdb.  Since then, you can't boot into either OS living or your 120GB drive?  Ubuntu or Windows?  
-What OS are you trying to boot when you get the above error?  Windows or Ubuntu?

I would go to System->Admin->Disks and see what it lists for each of your harddrives.  For each harddrive, select partitions tab and write down the device path for each partition and what type of filesystem is on there.  For example, /dev/hdb2 ext 3, etc...

---

