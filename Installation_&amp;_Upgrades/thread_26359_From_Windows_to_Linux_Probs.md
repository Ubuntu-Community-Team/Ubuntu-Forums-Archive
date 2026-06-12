---
title: "From Windows to Linux Probs"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by ScepticalLinux on 2005-04-12
Hey all,

Heres my problem:

I have two hard drives one 250GB and one 40GB. Up until recently I had Windows XP home on my 40 as well as almost everything else (documents etc.). On my 250GB I had some games and a few of my larger documents. I put the linux CD into my drive and rebooted. I told it to partition my 250GB which it did (erasing everything and installing linux). It placed a "Grub loader" onto my 40GB (master) and rebooted. Everything was fine (Linux booted and so did windows) Then I realised I had lost some files by mistake so I formatted my 250 (erasing Linux) and recovered my files. Now when I boot with both Hard drives plugged in it says something about a Grub boot error 17. I formatted my 40GB and my 250GB again and reinstalled windows on the 250GB. Now if i boot with just the 250 my windows is fine but if i boot with both drives it still gives me the error. What can I do to remove the boot loader and allow the use of both my drives under windows again? All help will be much appreciated and thanks in advance

Brad B
ScepticalLinux

---

### Post by sinbad782 on 2005-04-13
I think there's an option in Windows which runs along the lines of issuing a command like 

fdisk /fixmbr

and this should remove grub and restore the usual Windows bootloader in the hard disk's master boot record. Have a proper look on google to make sure before you do anything though!

---

