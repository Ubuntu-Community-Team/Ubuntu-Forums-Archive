---
title: "Installing 7.04"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by sundial on 2007-06-22
I am a newbie with Linux and I was trying to install Ubuntu 7.04 on an old Desktop PC and found a strange problem when the CD started to run.  I got a message saying " 223.764478] Buffer i/o error on device fd0 logical B0".  I do not have a clue what that means.  Any ideas?

I then tried the 7.o4 Kubuntu cd and got the same message.

I had no problem running 6.06 on this machine and I am sending this messgae from that system now.

While I am at it, can someone tell me what the differences are between the 6.06  and 7.04 versions?   And also, when it is time to move to a new upgrade of Ubuntu, must I do a new install?  Or, is there a way to upgrade without losing all my older files or having to back them up?

I read in a Ubuntu book that it is possiable tyo switch between the Gnome and KDE interfaces, but it not at all clear how to do that without doing a complete install of the system.

Finally, I cannot seem to get the current upgrade of firefox (2.02) using this version (6.06), or am I going about it the wrong way?  My system is running 1.5 and cannot see the upgrade in the upgrade manger when I download it.

---

### Post by az on 2007-06-22
> **sundial said:**
> I am a newbie with Linux and I was trying to install Ubuntu 7.04 on an old Desktop PC and found a strange problem when the CD started to run.  I got a message saying " 223.764478] Buffer i/o error on device fd0 logical B0".  I do not have a clue what that means.  Any ideas?

I then tried the 7.o4 Kubuntu cd and got the same message.

I had no problem running 6.06 on this machine and I am sending this messgae from that system now.

While I am at it, can someone tell me what the differences are between the 6.06  and 7.04 versions?   And also, when it is time to move to a new upgrade of Ubuntu, must I do a new install?  Or, is there a way to upgrade without losing all my older files or having to back them up?

I read in a Ubuntu book that it is possiable tyo switch between the Gnome and KDE interfaces, but it not at all clear how to do that without doing a complete install of the system.

Finally, I cannot seem to get the current upgrade of firefox (2.02) using this version (6.06), or am I going about it the wrong way?  My system is running 1.5 and cannot see the upgrade in the upgrade manger when I download it.


It sounds like a hardware problem.  I wonder if you tried to install 6.04 again, if you would still get that error.

Anyhow, you can dist-upgrade from one release to the next.  There is no need to reinstall.  See here:

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
Use the part labled: "Sequential upgrade from an older version of Ubuntu"

---

### Post by sundial on 2007-06-23
> **az said:**
> It sounds like a hardware problem.  I wonder if you tried to install 6.04 again, if you would still get that error.

Anyhow, you can dist-upgrade from one release to the next.  There is no need to reinstall.  See here:

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
Use the part labled: "Sequential upgrade from an older version of Ubuntu"

Thanks for the suggestion on upgrade.  I followed the giude and I am now running 7.04 on this system  I had to go to 6.1 then 7.04.

Any idea about the error message I got using the CD?  Is fd) a reference to the CD drive?

---

### Post by pxwpxw on 2007-06-23
fd0 is usually a floppy drive, might have a diskette in it?

---

### Post by davidjmayo on 2007-06-23
RE Gnome and KDE

It's easy to switch from one to the other as long as you log out each time (there may be another way I don't know of - I'm still a noob too). I did it a couple of days ago.
Depending which you use add the other one from by add/remove or synaptic or adaptic

log off and then you see  options in the bottom left of your screen. Just choose which GUI you want to use

---

### Post by eapache on 2007-06-23
To clarify what davidjmayo said, open Synaptic (System > Admin), and search for the Kubuntu-Desktop package. Install it and all of it's dependencies. Now in the login screen, you can click on the bottom left-hand corner (session chooser or something similar) and select KDE instead of Gnome. Voila.

---

### Post by az on 2007-06-23
> **sundial said:**
> 
Any idea about the error message I got using the CD?  Is fd) a reference to the CD drive?

Yes, but I have had similar errors installing Ubuntu on older (dying) machines, and the floppy drive had nothing to do with it (if it was even plugged in)



Try booting the cd and picking the integrity check.  Try booting the Dapper cd and check it, too.

---

