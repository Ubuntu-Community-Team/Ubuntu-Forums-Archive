---
title: "ubuntu along windows 11 isn't shoing grub for choosing what system to load...?"
date: 2021-10-11
forum: Installation &amp; Upgrades
---

### Post by ronjjjg8885 on 2021-10-11
hi
what is the right procedure for installing ubuntu 20.04 alon windows 11.....

i will tell you what i did and what has happened.
i've installed windows 11.
then ubuntu with the 'something else' option for partitioning.

after installation there wasn't the grub loader.
just windows 11 loaded regularly....

for some reason i couldn't find good info on that....

let me know if you know and can assist because i'm starting to feel desperate with it

tNx

---

### Post by oldfred on 2021-10-12
Do not know Windows 11.
But Windows requires fast start up off as it sets hibernation flag preventing the Linux NTFS driver from seeing the NTFS partitions.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If not the hibernation flag in Windows post this:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ronjjjg8885 on 2021-10-13
hi
thanks
i think i will use another pc just for ubuntu because i can't stand windows and i don't like all the hassle of dual boot and the configuration of the disks

---

