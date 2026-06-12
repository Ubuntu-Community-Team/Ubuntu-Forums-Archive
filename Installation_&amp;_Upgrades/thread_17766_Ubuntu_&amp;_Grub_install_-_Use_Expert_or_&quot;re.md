---
title: "Ubuntu &amp; Grub install - Use Expert or &quot;regular&quot; installer?"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by pigpen on 2005-03-02
Hi. New linux user here and I've got a question about the Ubuntu installer and Grub and installing it to dual boot on an existing install of win98 on a laptop. (Panasonic CF-M2 Let's Note model)

Does the normal (non-expert) Ubuntu installer for Warty(not Hoary) allow you to install Grub on a partition of your choice? I want to install Grub on a 60mb /boot partition I created, rather than in the MBR or in a /root partition.  I can't get a clear answer to this and the only way to find out it seems is if I actually go ahead and install (or use the expert installer), so I'm hoping to hear someone say "yes you can install anywhere".   =P~  If not, I'll forge on ahead and use the Expert installer  8-[ 

Main reason I want to do this is to avoid the Grub Error 18, as described in the [wiki](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes). My bios is in Japanese and I hate messing with it so I'd rather not attempt the bios solution, and alternatively not mess with my Japanese Win98 mbr. Therefore, as the guide suggests, I've created a partition to install Grub into.  Before I install Grub, do I need to somehow set a mount point for this partition as '/boot'? If so, how do I do this from within the Warty installer? Right now its is just simple a ext3 formatted partition (/dev/hda5), and within the 1024 cylinder limit.

Also, is it necessary to set this /boot partition with the bootable flag on?

Thanks in advance. I've heard great things about this Ubuntu and even better things about this community. I just love the whole philosophy about this distro, so I can't wait to try it out.

---

