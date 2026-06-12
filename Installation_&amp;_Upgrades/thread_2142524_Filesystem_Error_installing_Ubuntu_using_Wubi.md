---
title: "Filesystem Error installing Ubuntu using Wubi"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by shangw on 2013-05-06
Hi Everyone,

I am completely new to Linux system. This is what happened

First, I downloaded the standard package for Ubuntu 12.04, hope to install Ubuntu system on my old netbook and to run dual system with WinXP.
Second, I installed Ubuntu using Wubi.
Third, I restarted the computer and chose the Ubuntu system.
Fourth, the system tries to boot up, but it says (I know some other users have the same problem but it seems mine DOES NOT get solved the same way, and there are further descriptions coming up)

Errors were found while checking the disk for drive /.Press F to attempt to fix the errors, I to ignore, S to skip mountingm or M for manual recovery.
Then if I press F, it says 


The disk drive for /tmp is not ready
I tried the following:
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]mount -o remount, rw /
[/FONT][/COLOR][/LEFT][I]dpkg --configure -a
[/I]reboot

Then it gives a bunch of message like following:
INFO: task sh:679 blocked for more than 120 seconds
"echo 0 >/proc/sys/kernel/hung_task_timeout_secs"
(a lot of such)

And it just stops, the blinker keeps blinking and never moves any where.

Fifth, I power off the computer, start it again and go to the Ubuntu recovery system, and chose fsck, it gives the following message:
The filesystem size (according to the superblock) is 19169856 blocks they physical size of the device is 18161923 blocks. Either the superblock or the partition table is likely to be corrupt!
fsck terminated with status 4
Filesystem has errors
Skipping mounting/since Plymouth is not available. 

Finally, when I resume from the recovery mode, it gives the same error as in step 4 and 5. 

Any ideas how to fix this? 
Or if there is another way to install the system?
Thank you so much in advance!

---

### Post by bcbc on 2013-05-06
You could try this: [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

For an older computer I'd try [12.04.1]("http://old-releases.ubuntu.com/releases/12.04.1/") (because some changes added with 12.04.2 are for newer computers). Also, if your computer is light on resources, you could try Xubuntu or Lubuntu. 

If you don't want to partition (you want to use Wubi to try things out), you can download the 12.04.1 wubi.exe and the 12.04.1 desktop ISO and place them in the same folder before running. Disconnect from the internet before running Wubi.exe and reconnect before rebooting to complete the install. (That's required to install an older release as Wubi checks the md5sum of the desktop ISO and it won't find the back release). 

I would advise just doing a normal dual boot, but make sure you backup your data and create a Windows repair CD and restore DVDs beforehand if you haven't already.

---

### Post by shangw on 2013-05-10
Thank you so much!
Indeed, it was foolish of me :)

---

