---
title: "[SOLVED] Replace Vista for XP"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by carlosjoan91 on 2007-10-16
hi i have vista and ubuntu already installed on my computer, and i want to  replace vista with xp, i know that XP will mess up my grub, so i wanted to ask, how do i recover my grub menu after installing xp, i suppose i have to recover it from the cd, but more or less what do i need to change in grub.conf, and where is my grub.conf located?, thanks in advance!

---

### Post by Cynical on 2007-10-16
You can put the Ubuntu live cd in and boot into that environment after you install XP. There you would open up a terminal and run "grub-install /dev/hda1" (or wherever you originally installed grub) and it will  overwrite the windows boot loader.

---

### Post by carlosjoan91 on 2007-10-17
hi, i tried that, both attempting to install in /dev/sda5 (where i think grub was originally and in /dev/sda (MBR), both with the drive moiunted, and unomunted, and i always get the error "Could not find device for /boot: Not found or not a block device." what can i do? thanks

---

### Post by carlosjoan91 on 2007-10-18
i solved it using the Super Grub Boot Disk, now i can access everything, thanks anyway

---

