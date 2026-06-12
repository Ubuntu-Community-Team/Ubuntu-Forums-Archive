---
title: "unable to boot up in ubuntu"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by peter577 on 2009-11-28
I have been using ubuntu for two weeks as a dual boot system with windows xp and installed some updates this morning then restarted the computer but now a programme called GNU GRUB version 1.97~beta4 starts up and when I exit it the computer just reboots back to GNU GRUB. So I would like to know what the programme does and how can I get rid of it and start using ubuntu again?

I would be very grateful for any help with this problem as I really like using ubuntu and set up my wife's new computer the same way as mine but won't be using update until I can get my computer going again in ubuntu.
Thank You in advance for any help in this matter.
Peter Breed

---

### Post by lsk3993 on 2009-11-28
Did you use Wubi to install it? I'm having the same problem, seems to be only if installed with Wubi though: [http://ubuntuforums.org/showthread.php?t=1339541](http://ubuntuforums.org/showthread.php?t=1339541)
It looks like loads of other people are having the same problem too: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

---

### Post by peter577 on 2009-11-28
> **lsk3993 said:**
> Did you use Wubi to install it? I'm having the same problem, seems to be only if installed with Wubi though: [http://ubuntuforums.org/showthread.php?t=1339541](http://ubuntuforums.org/showthread.php?t=1339541)
It looks like loads of other people are having the same problem too: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)
Hello. I used the ubuntu installer for windows and don't know much about linux yet so I don't know if the ubuntu installer for windows used Wubi. I did try typing into GRUB the 140+ characters but just got the message that it couldn't find the file and tried /hda1 and /sda2 and /sdb1 with no luck. I am out of my depth as am trying to change over from windows xp and vista. sorry I can't help you either.

---

### Post by lsk3993 on 2009-11-28
> **peter577 said:**
> Hello. I used the ubuntu installer for windows and don't know much about linux yet so I don't know if the ubuntu installer for windows used Wubi. I did try typing into GRUB the 140+ characters but just got the message that it couldn't find the file and tried /hda1 and /sda2 and /sdb1 with no luck. I am out of my depth as am trying to change over from windows xp and vista. sorry I can't help you either.
Ok, try this, it looks as if my source had a typo [http://ubuntuforums.org/showthread.php?t=1339541&page=2](http://ubuntuforums.org/showthread.php?t=1339541&page=2)
Yes, I think Wubi is the Ubuntu installer for Windows. You can always uninstall Ubuntu as you would any other program in Windows and then reinstall it properly (onto a new partition). I am on this stage myself so I can't help with that. There are other threads discussing this issue though (one made by me), see if they help at all...
[http://ubuntuforums.org/showthread.php?t=1337754](http://ubuntuforums.org/showthread.php?t=1337754)
[http://ubuntuforums.org/showthread.php?t=1339541](http://ubuntuforums.org/showthread.php?t=1339541)[URL="http://ubuntuforums.org/showthread.php?t=1340071"]
[/URL]

---

### Post by peter577 on 2009-11-30
Hello Isk3993 and thank you for your interest in my problem. Seems like a very large number of us share the same problem. I have been reading some of the posts and it seems that anyone that runs Linux on a windows partition is using wubi and we are the only ones affected so I am going to either use two disk drives or partition a hard drive so that I can still use a dual boot system.

Wish me luck!
Regards Peter :)

---

### Post by muralidharbhat on 2009-11-30
Hi peter577 & isk3993,
 
Same problem here too, got it soon after the latest update and just when i was really enjoying using ubuntu, please pop a message as soon as any of you you get a solution. 
 
Many Thanks in advance.
Cheers!!

---

### Post by peter577 on 2009-12-05
> **muralidharbhat said:**
> Hi peter577 & isk3993,
 
Same problem here too, got it soon after the latest update and just when i was really enjoying using ubuntu, please pop a message as soon as any of you you get a solution. 
 
Many Thanks in advance.
Cheers!!

Hi again isk3993
I have my desktop computer working again normally in Ubuntu and windows. What I did was to install Ubuntu on a second hard drive and all is well again. Ubuntu even used the picture of stone henge from the windows desktop and also even my favourites list from Firefox on windows appeared on Firefox on Ubuntu. Now I just want to find the restore disks for my Medion laptop before I partition the hard drive and install Ubuntu on it as I really prefer the Linux system. Good luck and hope to hear how you have overcome the problem also.
Cheers :p

---

### Post by darkod on 2009-12-05
Peter, welcome to how it's properly done. :) Dual boot side-by-side, not inside windows. Glad you got it working.

---

### Post by peter577 on 2009-12-20
> **darkod said:**
> Peter, welcome to how it's properly done. :) Dual boot side-by-side, not inside windows. Glad you got it working.

Thanks darkod ISK3993 and Muralidharbhat for your interest and advise. Ubuntu is still working well on a second hard drive on my desktop and have made a dual boot on my laptop by partitioning the hard drive and it is also working well. Did find that I couldn't save utube videos any more but was advised to install downloadhelper and it works a treat. Am very happy again. Once again thanks very much for the help.
Regards Peter577:P

---

### Post by domnz on 2009-12-20
Just downloaded the file "wubildr" from this location (it's near the bottom) and followed the instuction exactly: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

Problem solved! :P (for me anyway)

---

