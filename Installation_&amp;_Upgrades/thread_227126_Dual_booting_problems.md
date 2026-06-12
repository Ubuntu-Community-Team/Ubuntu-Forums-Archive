---
title: "Dual booting problems"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by sbu on 2006-08-01
Good day all!

I am trying to dual boot windows and ubuntu on my system but experience problems.I first installed ubuntu 5.10 and then windows XP.
When I restart my system it goes straight into windows(I cant even see my ubuntu partition).

So I tried doing the following (as adviced by the website:[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-32d586a32fe70f9e1accb80d55cf3d3f0600175a](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-32d586a32fe70f9e1accb80d55cf3d3f0600175a) ):
   *

    " - Enter your computers BIOS to check computer can boot from CD ROM. If you can boot from CD, insert CD ROM into drive. Exit the BIOS (if needed save your settings to make sure the computer boots from the CD ROM).
   

   - When the Ubuntu splash screen comes up with the boot: prompt, type in rescue and press enter.
    *

    - Choose your language, location (country) and then keyboard layout as if you were doing a fresh install.
    

    - Enter a host name, or leave it with the default (Ubuntu).
    

      - At this stage you are presented with a screen where you can select which partition is your root partition (there is a list of the partitions on your hard drive, so you are required to know which partition number Ubuntu is on). This will be dev/discs/disc0/partX, where the X is a partition number.
    

    - you are then presented with a command prompt (a hash).
    

    - type $ grub-install /dev/hdaX where X is your Ubuntu root install. "

After entering what is required after the # I am told that there is no such directory or the volume is a block volume.

Can anyone help or explain what could be going on?#-o

---

### Post by confused57 on 2006-08-01
Here's a thread that may help:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

---

