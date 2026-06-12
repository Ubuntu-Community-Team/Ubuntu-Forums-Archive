---
title: "problem upgrade wubi 10.04 to 10.10 update-manager"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2011-01-08
Hi, I tried to upgrade from dual boot WinXP / wubi 10.04 to 10.10 because of problems with wifi (see my other post) and simply because ubuntu 10.10 is said to be so much better :-)). I got the message (sorry but some of the lines were output in German some in English): 

Es konnte nicht ermittelt werden, welche Systemaktualisierungen verfügbar sind

An unresolvable problem occurred while calculating the upgrade:
Es wird versucht, die auf der schwarzen Liste stehende Version »blcr-dkms_0.8.2-13« zu installieren

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

Falls nichts davon zutrifft, melden Sie dies bitte als Fehler im Paket »update-manager« und fügen Sie die Dateien aus dem Verzeichnis /var/log/dist-upgrade/ Ihrem Fehlerbericht hinzu.

I found it somewhat complicated to post this as a bug at the appropriate site, so I am asking for help here. I also could not upload all files from /var/log/dist-upgrade/ (as requested) since the .log files were not accepted here!

Attached is the remainder of the requested files. I would be happy if somebody could provide a solution. I am not aware of having installed anything form the blacklist and to the best of my knowledge none of the given possible causes applies. 

Thanks, D-,

---

### Post by bcbc on 2011-01-08
I searched around and found this:
[http://askubuntu.com/questions/5615/upgrade-fails-because-of-blcr-dkms](http://askubuntu.com/questions/5615/upgrade-fails-because-of-blcr-dkms)

Hopefully it helps.

PS when upgrading wubi to 10.10 - it is known to fail when the wubi is on the same partition as windows. See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for info on how to fix it.
When not on the same partition as Windows, there is a danger of the user choosing to install the grub bootloader to the MBR. Same thread has fixes.

PPS I'd be surprised if upgrading fixes your problem - or put it this way, if you haven't found something that indicates it will fix it, then it probably won't.

---

### Post by bcbc on 2011-01-08
Try this: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1005HA]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1005HA")

PS: I've tried netbook edition 10.04 and 10.10, and 10.04 is much nicer in my opinion. Before upgrading, download and try it via a USB stick. Or backup your root.disk so you can fall back to 10.04 if you decide you don't like it (backing up is a good idea anyway before an upgrade).

---

### Post by dieter-erich on 2011-01-08
Thanks a lot, in particular for the hint with partition and GRUB. I decided to only try the upgrade when back from vacations since I do currently not have any means of re-writing the Windows MBR if anything goes wrong Your answer might have prevented me from screwing up my system wihout being able to restore it! D-E

---

### Post by bcbc on 2011-01-08
> **dieter-erich said:**
> Thanks a lot, in particular for the hint with partition and GRUB. I decided to only try the upgrade when back from vacations since I do currently not have any means of re-writing the Windows MBR if anything goes wrong Your answer might have prevented me from screwing up my system wihout being able to restore it! D-E

You're welcome. The MBR prob can be avoided (the user is 'tricked' into doing it) - but better not to take a chance!

---

### Post by dieter-erich on 2011-01-10
Hi bcbc this  'sudo apt-get install linux-backports-modules-karmic' worked perfectly for me! Wireless now connects immediately!
Thanks for the hint!

---

### Post by bcbc on 2011-01-10
> **dieter-erich said:**
> Hi bcbc this  'sudo apt-get install linux-backports-modules-karmic' worked perfectly for me! Wireless now connects immediately!
Thanks for the hint!

OK great. But I thought you were on 10.04. There was a separate list of instructions:
> for wireless issue (see Karmic) Run 'sudo apt-get install linux-backports-modules-wireless-lucid-generic' instead.

---

