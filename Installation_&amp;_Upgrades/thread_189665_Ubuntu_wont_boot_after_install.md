---
title: "Ubuntu wont boot after install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Left Face Down on 2006-06-05
Well short and sweet I installed Ubuntu and everything thing went fine up until it told me that every thing was done and just reboot my computer. When I did that the computer restarted, started to load the Kernel and before it had even spit out a page of info the computer just restarted. I've gone around and messed around with the HDD settings as I had a similar problem installing Gentoo Linux and it was just Grub being stupid, but I was dual booting on that computer. I also went into the Grub menu and tried to boot up the recovery mode but the same thing happened after I selected that.


For reference I am not dual booting any other OS on this computer. I have two 8Gb HDDs, both detected during instillation, which I set up a Swap [Primary] (510Mb) partition and the rest I just partitioned as a bootable partition, once again a primary partition. I partitioned the whole second HDD with a primary partition but I did not make it bootable as I was told only the partition with the OS itself needed to be bootable.


That's really all the info I have. I can't begin to think about what's wrong and I haven't gotten around to it but I was just going to install it again and see if that'd work.  


Any one have any ideas?
-LFD

Edit: I use the normal x86 CD to install.

---

### Post by Endwin on 2006-06-05
I have the same problem, the difference being I used the Ubuntu server i386 image. When I used the alternate cd image it worked fine. I recall reading about people having a lot of problems with the server  image, and to a lesser extent the desktop image. Give the alternate CD a shot and see how that goes. it worked for me, and my constant rebooting problem.

---

### Post by Left Face Down on 2006-06-05
Alright, that fixed the rebooting but I don't have a GUI, or it doesn't automaticly boot up into the GUI. Once again, I was told installing Ubuntu installs Gnome and the videos on Google Video, interesting as they may be, have nothing about installing a GUI.


I can sucessfully log in through command line but I don't know any of the Ubuntu language, as every Linux seems to be different, and "sudo --HELP" gives me a very small list. 


I downloaded and used the Alternative ISO and I told it to create a server, as the other disk was a server disk. Was I just wrong in assuming this was the GUI version and that it really is a command line prompt server version?

---

