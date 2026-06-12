---
title: "Not able to upgrade/install Lubuntu 12.10 on Compaq Armada M300"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by Comodín on 2013-01-19
I have tried in several ways now to upgrade my Compaq Armada M300 (P3-600Mhz-320MB RAM) from Lubuntu 12.04 to 12.10. First I tried to upgrade within 12.04 (sudo do-release-upgrade & update-manager -d) and when that didn't work I burned the CD and did a clean install.

I have spend already many hours on this, as the machine is not really fast. What happens is that after updating (without error messages) I try to boot up and it just keeps on looping with flashing letters stating STARTING. 

Any help or suggestions would be much appreciated.

---

### Post by Comodín on 2013-01-20
Two screenshots that might give an indication of what's going on. It seems like something is not mounted. If I wait or press S, then the flashing and looping starts. If I press M then I get to the other screenshot, but unfortunately I don't now what to do.

This is now the sixth time I tried to upgrade to/ clean install Lubuntu 12.10 with three cd's burned and verified at the lowest speed, and if this doesn't work then I'll stick to 12.04 or maybe look for another lightweight distro.

Seems it is not mounting swap... /dev/mapper/cryptswap1

---

### Post by mörgæs on 2013-01-20
I wouldn't invest many ours in this old guy. Used hardware is so cheap that you should consider a replacement, say 4-5 years old. 

Anyway, if you want to get 12.10 running this might help:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Installing the command-line only system first and applying all updates is another option. When this works you can add the GUI.

If you don't have any particular need for 12.10 then staying with 12.04 will give you a working system through october.

---

### Post by Comodín on 2013-01-26
Thanks for the reply, Mörgæs. Yes, it is an old machine, but it has, lets say, a lot of sentimental value for me. Thin as a MacBook Air and I got it complete with dock and working battery.

I will try the minimal install, but I fear it won't work. I read somewhere on the net that ATI dropped support for the older series of cards last summer so they won't write drivers for it anymore. If your suggestion doesn't work, then I'll just stick to 12.04.

Closing the thread.

---

### Post by mörgæs on 2013-01-26
A last comment, though the thread is solved:

Lubuntu 12.04 is a good alternative. In fact there are only minor changes from 12.04 to 12.10.

Yes, ATI has a bad record of abandoning what they define as obsolete cards, but the open source drivers are always available.

If you want to play with other light distros here is some inspiration:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

