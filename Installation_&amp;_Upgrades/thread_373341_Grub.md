---
title: "Grub"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by jhcoles on 2007-03-01
I need to create a new GRUB bootloader.  My PC originally had two hard drives – one containing Win 98 (used by my wife!), a “Shared” partition accessible to both Linux and Windows together with a current laboriously updated Ubuntu system.  The other small drive has another copy of Win 98 which is used solely to automatically back up “Win98/My Documents” from the main drive.  (I have always insisted on a separate back up drive.)   At some stage when I was “experimenting” with the  Ubuntu installation (and after downloading a fair number of updates) I made a boob and lost/corrupted the bootloader.  I decided an easy solution (since Ubuntu installs so quickly) was to introduce a third small drive and install Ubuntu on it SOLELY to create a new bootloader which would “pick up” the other operating systems.  (The beginner's approach!)
This works well and when I start I can choose which system to boot from with the normal menu.  However I now need to remove the third drive (to replace it with a DVD drive) and hence my problem.  If I disconnect this drive GRUB comes up with error code 21 (missing device) as you would expect.
How do I create a new/amended GRUB – which  would have to be installed onto the  main drive – so that I can once again boot from Ubuntu/Windows1/Windows2?  I do NOT want to have to re-install Ubuntu from scratch – downloading all those updates again with a dialup connection would give me a coronary!!  Any advice would be very welcome.

---

### Post by realalien on 2007-03-01
> **jhcoles said:**
> 
How do I create a new/amended GRUB – which  would have to be installed onto the  main drive – so that I can once again boot from Ubuntu/Windows1/Windows2?  I do NOT want to have to re-install Ubuntu from scratch – downloading all those updates again with a dialup connection would give me a coronary!!  Any advice would be very welcome.

I have an problem alike, how to remove the windows partition which may contained the grub, and reinstall grub to the Ubuntu partition for leading in without reinstalling and updating the os again.

---

### Post by realalien on 2007-03-01
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
That post seems to be quite useful, I hope it bullet proof.

---

