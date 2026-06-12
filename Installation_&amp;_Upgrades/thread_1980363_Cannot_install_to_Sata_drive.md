---
title: "Cannot install to Sata drive"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by johnno56 on 2012-05-15
I have acquired a new, never been used before, pc to install Ubuntu 10.10

I have used both live CD and USB to install but the installation will not "see" the Sata drive. There is nothing wrong with the CD or USB as they were used to install 10.10 on my previous pc (HDD was an IDE). Bios indicates that the Sata is configured for IDE

The installation does not get to the part where the partions are created.

fdisk -l shows the exeistence of the Sata drive. I have even tried the dmraid -E -r /dev/sda1 - replied 'no block devices found'

I cannot install my old IDE drive as my new PC does not have any IDE sockets on the mobo. (Gigabyte H77-D3H)

Both CD and USB will allow "Try without installing".

At the moment I am forced to use Windblows to log this problem. I am suffering from withdrawl symptoms. I want my Ubuntu back.

Any suggestions would be appreciated.

Regards

J

---

### Post by darkod on 2012-05-15
You ran the dmraid command to a partition, /dev/sda1. It's usually run to the whole disk, /dev/sda. See if that changes anything.

Also, any particular reason you want to install 10.10? It's already out of support. Can you use a newer version?

The best is to use the latest LTS version, 12.04 LTS.

Also double check in BIOS that by any chance you don't have RAID enabled for the sata mode. It should be AHCI.

---

### Post by johnno56 on 2012-05-15
Darkod,

Problem solved. Sata should have been set to AHCI mode. System installed to drive without a glitch.

Reason for installing 10.10: I am not a big fan of Unity. But that being said, when 10.10 installed, a message warned me of that fact of non-support. I am now running with 12.04 LTS. Looks like I may have to try and "get along" with Unity. The other alternative is to go back to that other operating system. (which shall not be named...)

Regards

J

---

### Post by darkod on 2012-05-15
If you prefer the older interface you can install and use Gnome Classic:
[http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html)

That still keeps Unity, you can select what you want to load at each login.

---

### Post by johnno56 on 2012-05-16
I think I tried to use classic when I was trying out 11.04. I think I did something wrong and broke 11.04.... I do not know what I did wrong, but that was the point I decided to regress to 10.10.  I have tried many distros, but I alway came back to Ubuntu. Must be one of the most user friendly OS's out there. Now all I have to do is learn to like Unity.

Many thanx for the advice / assist.

Regards

J

---

### Post by darkod on 2012-05-16
As you can see in that link, the instructions are very easy, you only run one command. Only installing classic can't break anything.

Now, if you start playing with different options (either in Unity or Classic), yes, things can go wrong. But not with only installing it. That should be fine.

At the login page, with the ubuntu icon next to your user you can select which session to load, unity or classic. It remembers the last choice usually so you don't have to select at each login.

But if you want to load the other session, you simply click the icon and select what you want.

---

### Post by Cheesemill on 2012-05-16
Also take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

