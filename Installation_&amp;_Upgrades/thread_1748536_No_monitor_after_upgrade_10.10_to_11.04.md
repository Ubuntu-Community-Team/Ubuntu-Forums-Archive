---
title: "No monitor after upgrade 10.10 to 11.04"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by loy66 on 2011-05-03
I upgraded from 10.04LTS to 10.10 dell display moniter worked. Then upgraded to 11.04 and get no display. I can hold the Shift key down during boot and get Grub menu, using the Linux----  (recovery) and get a command prompt. If I run "sudo startx" , I get a fatal error " nvidia module" not found.  How do I get the nvidia module installed from  command prompt?  All my problems started originally form installing NVIDIA GeForce 210 display adapter ( for dual screen & HDMI connection to my LCD flat screen TV).  My motherboard has a built-in GeForce display adapter.  I was going to re-install the whole Ubuntu 11.04 but it will not boot from my CDROM.  I can boot  "Puppy Linix" with my CDROM. Puppy Linux works great and on my monitor.   I have no idea why Ubuntu 11.04 will not boot.  [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by moog10538 on 2011-05-08
Similar problem here.

I've just done a fresh install on a system with two nVidia GeForce 210 cards (triple-monitor setup).  Ubuntu fails to boot if the proprietary driver is enabled; it boots fine if the driver is disabled.

Anybody have any ideas?

---

### Post by loy66 on 2011-05-09
I spent so much time trying to get Ubuntu 11.04 to work. I just reinstalled Ubuntu 10.04LTS in a new partition.  Now I am trying to reinstall all the other programs that I lost. I don't know why I am running Linux anyway. I spend more time trying to get adapter cards like GeForce 210 to work than I ever did with Windows!

---

### Post by aapst12 on 2011-06-01
When trying to boot the upgraded OS, after the grub menu, I got no signal to the monitor, causing the monitor gave a message "entering power save mode".
 
My problem was solved as follows:
The cable at the back of the vga card is split in two, for the purpose of a dual monitor.  I disconected my monitor from the "2" female cable to the "1" female cable.  Then I rebooted.  Everything worked.

---

