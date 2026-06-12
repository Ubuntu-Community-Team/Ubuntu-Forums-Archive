---
title: "Did Ubuntu override Windows XP?"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Bluesharpman on 2008-02-03
A friend just called to tell me he installed Gutsy Gibbon as a dualboot with Windows XP.  He does not get a boot menu that allows him to select XP or Gutsy.  I'm afraid he may have overridden Windows XP.  How can he tell?  He has access to Gutsy but not Windows.  menu.lst does not contain windows info. Thanks

---

### Post by forestpixie on 2008-02-03
get him to do this first from terminal

sudo fdisk -l

---

### Post by nobody13 on 2008-02-03
He needs to edit /boot/grub/menu.1st and comment out hiddenmenu so the option for xp will appear at boot. You should also uncomment the pretty colors line and change the timeout to 10 so you have a few more seconds to choose operating systems.


```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]hiddenmenu[/COLOR]

# Pretty colours
#color cyan/blue white/blue


```

---

### Post by orange2k on 2008-02-03
In the installation process, Ubuntu asks you if you want to use the entire disk (or disks) or if you want to partition it. If you chose the first option then there is no Windows anymore...

---

### Post by Bluesharpman on 2008-02-03
Thank you for your response.. I"m afraid that he may have used option 1.  I'll be calling him back in a moment.

---

### Post by nobody13 on 2008-02-03
Hopefully he didnt do that. You can check what partitions are on your computer by opening a terminal and  typing fdisk /dev/hda (or sda .b ..c depending on you configuration) then type p and enter to list partitions.

---

### Post by forestpixie on 2008-02-03
sudo fdisk -l would let you know if there were ntfs partitions

---

### Post by nobody13 on 2008-02-03
I didn't know that one, thanks

---

