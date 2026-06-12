---
title: "Quick Install question"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by jpadillafx on 2008-04-26
Hello everyone, let me begin that I am a ubuntu newbie but I am very excited about what I've seen and can't wait to dive in deeper. 

Ok, here it goes.. I want to install ubuntu 8.04 on my external hard drive so I can dual boot between winxp and ubuntu. I just insalled it from the livecd, partitioned my external hard drive, and restarted. However, when I go to f12 when i start my computer and tell it to boot from usb I get a grub 17 error saying something about not being able to mount the drive or something similar. 

So... should I go and do it over again and tell it put the bootloader on a different partition? I currently told it to put it on sdb1 (external harddrive). 

Here is how my external partitions are. 
sdb1 (I want to use as storage space, I currently have 6 gbs worth of important data on it)

sdb2 - I want for the ext3 for ubuntu- I think there is something like 100 gbs free space.

sdb3 - swap- I designated like 10gbs to this. I know, too much but does it matter?

What specific things do I need to do to get this running? Do I have to tell it put the bootloader on my hda? I did this last night and had tons of trouble with grub errors when I started my computer.. (recovery console>fixmbr corrected this for me after hours of research :cry:)

Thanks to anyone who wishes to help this ubuntu newbie become a less of a ubuntu newbie. Cheers!

---

### Post by mathenge on 2008-04-26
Here's a long post that might point you in the right direction. Please read carefully and don't do anything that you might find suspicious. It looks really well written though.

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

The gist of the post is that you need to install Ubuntu to your external (USB) drive as you did. However, when you reboot and the disk is ejected, put it back in and boot again from it, however, boot into recovery mode.

At that point, the author explains how to get USB support. I believe that's why you got the GRUB error.

Hope this helps.

---

### Post by jpadillafx on 2008-04-26
Thanks for the great post! I have a big read in front of me. I hope I get this up and running before I get tired and give up.

---

