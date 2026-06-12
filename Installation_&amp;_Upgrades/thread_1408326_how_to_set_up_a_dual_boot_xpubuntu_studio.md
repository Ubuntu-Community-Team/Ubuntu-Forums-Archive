---
title: "how to set up a dual boot xp/ubuntu studio?"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by drumkitcat on 2010-02-16
Hi,

I have a desktop computer that is currently running WinXP home edition - it has a 40Gb drive that is unpartitioned, so XP has the run of the house, so to speak.

I would like to set that computer up to be a dual boot between XP and Ubuntu Studio - how can I do this?

I tried searching the forum but wasn't able to find anything exactly like what I wanted to do - please let me know.  I have a DVD of Ubuntu Studio 9.10 and if someone could walk me through this, that would be great, thanks

Paul

---

### Post by cchhrriiss121212 on 2010-02-16
Adjusting the partitions on a hard drive can cause loss of data, though I have never experienced this myself. You should defragment the drive through XP first, then insert the 9.10 DVD and reboot. When the computer starts up again press f12 to enter the boot menu and boot from the dvd drive. 
Unlike plain Ubuntu, the studio version has a text based install only. Also it is neccessary for you to have a wired internet connection during the install.

When you get the option of where you would like to install, the easiest thing to do is to select "install Ubuntu side by side with windows". However I would recommend using the partition editor which will allow you to define how much space to allocate for each OS and create a seperate home partition to keep your settings and files (this is useful when re-installing or upgrading Ubuntu). To do this you select "specify partitions manualy". 
Here's an example of how I would partion the drive:
XP-20GB
/-8GB
/home-11GB
swap-1GB

You should look at this: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
and this: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) once you are up and running.

---

### Post by drumkitcat on 2010-02-16
> **cchhrriiss121212 said:**
> Adjusting the partitions on a hard drive can cause loss of data, though I have never experienced this myself. You should defragment the drive through XP first, then insert the 9.10 DVD and reboot. When the computer starts up again press f12 to enter the boot menu and boot from the dvd drive. 
Unlike plain Ubuntu, the studio version has a text based install only. Also it is neccessary for you to have a wired internet connection during the install.

When you get the option of where you would like to install, the easiest thing to do is to select "install Ubuntu side by side with windows". However I would recommend using the partition editor which will allow you to define how much space to allocate for each OS and create a seperate home partition to keep your settings and files (this is useful when re-installing or upgrading Ubuntu). To do this you select "specify partitions manualy". 
Here's an example of how I would partion the drive:
XP-20GB
/-8GB
/home-11GB
swap-1GB

You should look at this: [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
and this: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) once you are up and running.


That's very helpful, thanks for your response!!

---

