---
title: "Uninstalling Vista and going to Ubuntu Only"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by cappii on 2007-09-18
**[FONT="Tahoma"][/FONT]**

Howdy :) from Texas!!  I have migrated all of my home computers over to Ubuntu now, and am ready to do so with my laptop....  However, I am dual booting Vista and Feisty, and REALLY do no want to lose my setup here.  I can lose everything on the Windoze side, I've pulled over the media files that I wanted to keep anyway.  Is there any way that I can just uninstall the Windoze partition?  I know that I will likely have to use the Live CD to repair Grub, and I am okay with that.  Second part of the question.. while I am breaking my Windoze... should I completely repartition the Hard Drive into one nice big one for Ubuntu, or would it be okay to leave the former Windoze partition intact, only use it for storage, such as an extended partition?  Thanks for your thoughts, and any ideas on how to make it a little easier to work :D

Cappii

---

### Post by Pumalite on 2007-09-18
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to erase Vista and 'recovery partition'
Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
And then use this to make yourself a new /home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by cappii on 2007-09-19
Hey!!  Thank you!  Using GParted, which I had already installed, worked well, and re-doing Grub was a simple procedure.  After a quick reboot, I was left with a nice clean partition for lots of storage.  Now... since Vista was an upgrade from XP, how do I edit Grub to remove the WinXP entries?  Thanks again!!

---

### Post by Pumalite on 2007-09-19
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst.back, then:
gksudo gedit /boot/grub/menu.lst
Erase XP entry, save exit and reboot.

---

