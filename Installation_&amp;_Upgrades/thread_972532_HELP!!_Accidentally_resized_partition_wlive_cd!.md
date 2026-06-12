---
title: "HELP!! Accidentally resized partition w/live cd!"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by lev5c on 2008-11-05
My intentions were to reinstall/upgrade to 8.1 in order to restore all default ubuntu settings (ATI drivers & video playback in particular :evil:), but keep data across all partitions. Now, I'm afraid I've screwed up the main linux partition in the process.

Here's what went down:
------------------------------------------------
1. Booted from 8.10 LTS Live CD
2. Chose "Manual" hard drive partitioning
It displayed the following: (sizes are approx)
/dev/sda1 ext2 53gb 17gb used
unallocated 1gb
/dev/sda2 linux-swap 2gb ?
/dev/sda3 ntfs 60gb 52gb used
/dev/sda4 ntfs 40gb 37gb used

3. Resized sda1 to 25GiB

It did what I told it to do by unallocating space, I just assumed it would unallocate the 35 or so gigs of free space. Now, I can't boot cuz I'm getting a GRUB error 15: file not found. So, I rebooted with the Live CD and ran partition manager.

This is the current state: (sizes are approx)
/dev/sda1 ext2 23gb 375Mb used
unallocated 32gb
/dev/sda2 linux-swap 2gb ?
/dev/sda3 ntfs 60gb 52gb used
/dev/sda4 ntfs 40gb 37gb used

I tried the "undo changes to partitions" option to no avail, and that's exactly what I need to do. Been surfin' forums all day. Any help is appreciated. [-o<

---

### Post by zwygart on 2008-11-05
If I understand you wanted to install 8.10. But your Grub is set wrong and 8.10 is not present. Did you see the menu of GRUB (May be you have to press ESC durnig boot).

If not you have to reinstall GRUB.
Boot from live CD and type in the terminal
find /boot/grub/menu.lst
check the drive wich is outputed then type this with the drive
grub
root (the drive displayed)
setup (the drive)
This may help you Chek point 3.
[http://www.linux-france.org/article/sys/chargeurs/ix86/grub/installation.html](http://www.linux-france.org/article/sys/chargeurs/ix86/grub/installation.html)

If you see the grub boot menu then the file /boot/grub/menu.lst is set wrong.

Boot from the CD and chek this file. If you don't know how it works paste the last lines (without square) and the output of sudo fdisk -l.
Did you have windows?
Hopping that I can help.

---

### Post by lev5c on 2008-11-05
Thanks for checking this out! I started another thread earlier @ [http://ubuntuforums.org/showthread.php?t=972425](http://ubuntuforums.org/showthread.php?t=972425)
Maybe we should move discussion there? i dont know

Anyway, I am runnning the live cd now (only way to get online)
ubuntu@ubuntu:~$ find /boot/grub/menu.lst
find: `/boot/grub/menu.lst': No such file or directory

I'm gonna try the Rescue Remix iso now and see if that doesn't help at all?

---

### Post by dmizer on 2008-11-05
Please do not create multiple threads for the same question. It creates problems for people who are trying to help you, and duplicates troubleshooting among other problems.

Thank you.

---

