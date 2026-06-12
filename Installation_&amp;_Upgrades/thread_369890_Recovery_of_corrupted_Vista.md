---
title: "Recovery of corrupted Vista"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by stenci on 2007-02-25
I installed Ubuntu in a brand new computer. During the installation I created the 2 partitions for Ubuntu, and Ubuntu now works well.
The problem is that Vista is dead: Vista doesn't reboot anymore, neither from hard disk nor from recovery CD. It restarts the reboot, and it hangs when I see the mouse pointer.

Here I found some info about how to setup a Vista-Linux dual boot: [http://blogs.sun.com/moinakg/#vista_and_solaris_express_dual]("http://blogs.sun.com/moinakg/#vista_and_solaris_express_dual")

My questions are:

1) Does the fact that Vista starts booting and hangs after 30 seconds mean that the boot doesn't work? 
Or, since the boot starts, Vista is corrupted and I need to format and reinstall it?

2) I worked with Unix years ago, but I'm new with Ubuntu and dual partitions, can you help me to understand the instructions?
"installgrub" in Ubuntu doesn't exist. I think I should use "sudo grub", but even after reading the grub documentation I don't feel comfortable with experiments on the MRB. (I already messed it up enough!)

3) Also "bcdedit" doesn't exist in Ubuntu. What do I do here?

(I'm interested on help, please don't waste time cursing Windows.)

---

### Post by lorpi on 2007-02-25
I only can answer **question 3)** half: "bcdedit.exe" is a Vista-tool for its own bootloader; to use grub isn't suitable for Vista. But you can add the MBR ubuntu has created in the BCD of Vista with commands listed in the howto you've noticed.

adds: **question 2)**: "grub-install" is the right command, but you won't need this for dual-boot Vista and Ubuntu; **question 1)**: yes, but maybe Vista can recover his own MBR when you choose "Repair an install of Vista" (I don't have Vista, so maybe its different). But the howto sais, that you have to install Ubuntu first and then Vista to get the MBR of Ubuntu.

---

