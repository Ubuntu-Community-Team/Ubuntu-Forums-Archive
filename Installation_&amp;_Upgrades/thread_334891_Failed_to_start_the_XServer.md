---
title: "Failed to start the XServer"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by harusp3x on 2007-01-09
I had ubuntu installed, then I reformatted that partition and installed Fedora Core 6. FC6 made my monitor out of sync so I went in to edit the xorg.conf file. The editing process was crap and I'm sure I screwed something up. I decided to get rid of FC6 and go back to ubuntu.

So I start it up with the Edgy Eft Live CD in the drive hoping to just start up the Ubuntu installation and reformat my FC6 partition. Well FC6 kept loading under the Ubuntu installation. It would go to the Ubuntu splash screen and when I selected "Run Live CD or install" I kept getting a scrambled "Failed to start the XServer" error.

I went into Windows and used Paragon to delete all linux partitions, leaving me with just my XP partition and my Vista partition. I rebooted and realized I deleted the /boot partition Linux had installed GRUB onto, so I couldn't load jack an OS.

Luckily, I could still boot up the live CD. So I successfully got into the Ubuntu installation and installed it on the unallocated space I had just created from all of my linux partitions (ex3, swap). After installation, I rebooted and got to GRUB. I selected to load Ubuntu and it goes into the hideously deformed X86_64 usplash bug as it always has. But then it gives me the same XServer error... after I had reformatted. Why is this happening? And how can I remove my linux stuff COMPLETELY so I can start anew?

Thank you.

---

### Post by sdowney717 on 2007-01-09
load recovery console from winXP setup disc to get to a prompt.
Then type FIXMBR
this will rewrite the mbr just for windows.
When you get to windows again, goto 
click 
 start settings control panel administrative tools computer mangement storage diskmanagement
right click all the linux partitions and removen them till they are unallocated space.

So how do you dual boot vista and XP?

---

### Post by harusp3x on 2007-01-09
I figured out my problem. Turns out it was because my video card was sending out a digital signal and the linux drivers for that weren't installed. I had to run it with an analog monitor for the time being.

And to dual-boot XP and Vista, I just created another primary partition with Paragon Partition Manager and installed Vista on to that. It's not a problem to do if you have the RTM.

---

