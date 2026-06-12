---
title: "Error Installing Netbook Remix"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by xanfantasy on 2010-10-13
I am trying to install Ubuntu 10.10 Netbook Remix on my Asus 1005HA but every time when I get to the keyboard selection screen it freezes. Since the screen resolution is too small I cannot see the command line. I hooked it up to my 720p TV as the only main display and this time it went from the ubuntu desktop to a completely black screen with my mouse cursor as the loading wheel but frozen and displays "(process:300): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"

Any help would be much appreciated as I have not been able to successfully install the past 3 releases on this machine and would much prefer ubuntu and unity over windows XP.

---

### Post by mavrek on 2010-10-15
I'm having a similar issue, but I have found this thread in the forums:

[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

My first thought would be to try a different method of install (ie use a CD instead of a USB key, if possible). It seems that a number of different issues are all leading to the same error message. Another thought is to possibly use a 10.04 install, and then upgrade to 10.10. You can install the Netbook Remix packages (like Unity) from within a normal version of Ubuntu, if that was the final setup you wanted.

Good luck

---

### Post by xanfantasy on 2010-10-18
I have tried both 10.10 desktop and netbook remix using both usb and external cd drive and all times trying it on my netbook screen and with my tv/monitor and it either freezes or generates the above error with a different Process number somewhere between 290-300. As I also stated before I would have to go back to 9.04 to get an install to work and then upgrade all the way to 10.10 but I have had problems before when I have done this from 9.04 to 9.10.

---

### Post by xanfantasy on 2010-10-18
So I tried using the desktop version on my thumb drive while using the netbook screen again but this time setting up all partitions in Gparted instead of in Ubiquity installer. I also did not tell Ubiquity to format any of the partitions either. This has allowed me to install the desktop version but I am not sure about any of the other combinations. I am just happy to finally be able to use my netbook with ubuntu again.

---

