---
title: "Ubuntu freezes after new installation"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Krudtugle on 2008-02-08
I just bought a new HD and installed Ubuntu 7.10 to it. The installation worked out just fine with no signs of any problems at all.

In the end of the installation the CD ejected and I rebooted. Ubuntu starts and the statusbar appears, but it freezes after just one very tiny little bit (just a few % of the statusbar). When I reboot again, the same result.

I have also checked the CD for errors, but no errors found.

Hw can this be possible?

---

### Post by Partyboi2 on 2008-02-09
try booting with nosplash to see where it is stopping.
When you boot the system you will see grub starting to load something like stage1_5 loading.... Press Esc to enter the grub menu. then press "e" to edit the highlighted kernel, then highlight the entry that starts with kernel... then press "e" and you will see the word splash change that to nosplash and press enter then "b" to boot.

---

### Post by Krudtugle on 2008-02-10
Thanks, I tried this and the result was the following.

First the following line:
[  337.567402] usb2-1: can't set config #1, error -71

Then, after a while:

check root=bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda1 does not exist. Dropping to a shell!

BusyBox v1.1,3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

---

### Post by Krudtugle on 2008-02-18
This was solved by editing the /boot/grub/menu.lst and exchange "hda" to "sda". I gues GRUB didn't find the disk, since there IS no disk called hda, just one which is called sda.

I find it very strange that Ubuntu installs GRUB with these settings in the menu.lst file. Why write hda in menu.lst when there's no disk called that???

Anyway, it works now.

---

### Post by licklavin on 2008-02-18
i'm having the same issue. how do i edit the  /boot/grub/menu.lst  ?? new here

---

### Post by Krudtugle on 2008-02-19
I used the following procedure:

1. Started Ubuntu from the live CD
2. Started GParted to check what the disk was called (/dev/sda1 in my case)
3. Mounted the disk with the command **sudo mount /dev/sda1 /media/mnt** (the folder where you mount the disk, /media/mnt in this example, must of course exist).
4. Edited the file with the command **gksudo gedit /media/mnt/boot/grub/menu.lst**

---

