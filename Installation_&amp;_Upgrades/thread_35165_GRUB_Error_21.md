---
title: "GRUB Error 21"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by tbmelancon on 2005-05-17
Please help.  I am trying Linux for the first time and know very little about it.

I installed a second (slave) 1GB HD ant tried to install Ubuntu.  It successfully installed GRUB and rebooted, then started downloading lots of files.  When the HD filled, it stopped.

That was OK becuase I could still boot to Windows 2000 on the master HD.

I pulled the 1 GB HD and installed a 20 GB HD as a slave and tried to reinstall ubuntu on that drive.  It installed GRUB and instructed me to remove the CD so the computer could reboot.  It gets stuck on error 21 and I cannot even boot to windows.

I would really like to try Ubuntu.

Tom

PS I put the original 1GB HD back in so I could boot to windows to find some help.

---

### Post by defkewl on 2005-05-17
Why don't you install Ubuntu as a Master?

---

### Post by nad on 2005-05-17
Your /boot/grub/menu.lst needs to be modified.

At the grub prompt, issue the command: find /boot/grub/stage2

Note the location and follow instructions in these forums to edit the file.

---

### Post by tbmelancon on 2005-05-18
Thanks for the help. I will try the find command. If that doesnt work,I will try resetting the 20 GB HD to the master and the windows HD to the slave.

---

