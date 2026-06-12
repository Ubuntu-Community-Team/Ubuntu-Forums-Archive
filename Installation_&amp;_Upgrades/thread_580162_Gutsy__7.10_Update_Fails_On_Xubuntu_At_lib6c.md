---
title: "Gutsy / 7.10 Update Fails On Xubuntu At lib6c"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mig5 on 2007-10-18
Hi.

Today I tried to upgrade from Xubuntu 7.04 (Feisty) to Xubuntu 7.10 (Gutsy) via the update manager.  The upgrade was going OK until it got to lib6c, when I received an error message saying that gnome-net-status applet had encountered an error and had to close.  Straight after I received a similar error message, but this time saying that cupsys had to close.  And then after that one I got the last and worst: update-manager has encountered an error and has to close.  And it did.  The upgrade program disappeared and I received an message saying that the upgrade had failed and that my system might be unstable/broken.

As I my system still appeared to be functioning I thought that I could simply re-run the update manager and try to upgrade again.  However, when I tried this I found that I was no longer given the option to upgrade to 7.10.  Instead I was offered 1 update, to cupsys, which I did.

Confused, I decided to restart my computer to see what state it was in.  On boot I found that I had 3 different kernel options to choose from (I only had 1 before attempting the upgrade).  The first one was a new one, the second one was also new (yet the same version number as the first - it wasn't the recovery, there was a recovery boot option for both of these kernels), and the third was the kernel that I had before attempting the upgrade.  I booted the first one.

The system seemed to boot OK, although it was slow and the GDM login had changed back to the default orange.  However, on login I discovered that the internet wasn't working (I was going to look for information on how to rectify my upgrade problem).  In the network configuration application my wireless card is no longer listed, all that shows up is my LAN card (which isn't the method I use to connect to the internet).  The only information that I can give about my wireless card is that it is ASUS and before the attempted upgrade the connection was called 'rausb01'.

Now I am stuck.  I don't know whether the new kernel or the half-done upgrade are to blame for the disappearance of my internet connection.  I also have no idea of how to get my wireless card back in the network interfaces list either.  At the moment I'm writing from Windows XP on the same computer (before this upgrade I had not booted Windows for 4 months, so just imagine how much security update backlog I've had to go through just to get this message out).

It appears that I am not the only person to have had the problem with the update manager closing during the upgrade, I found someone else with the same problem on this thread: [http://ubuntuforums.org/showthread.php?t=579337](http://ubuntuforums.org/showthread.php?t=579337) .  However, at the moment they have not fixed their system either.

---

