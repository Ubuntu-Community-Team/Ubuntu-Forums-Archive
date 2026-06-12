---
title: "Dual booting XP/Ubuntu (AMD64)"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by eqisow on 2005-04-16
OK, I'm trying to dual boot Windows XP and Ubuntu from a single drive. I've been working on this most of the night. At the moment, I have Linux on the first partition of my serial (sda) drive, Windows on the second partition, a Swap file for the 3rd, and a second FAT32 storage drive. Windows is set as the active partition and Grub is installed on the Linux partition. I can log into Windows just fine, and I have the windows bootloader set up to offer a choice between Windwos and ubuntu. It Does, when I choose Windows of course it works. When I choose Ubuntu I get taken to the Grub choice screen where I (again) get to choose between ubuntu and Windows. From THIS menu, however, I encounter issues. If I try to run Ubuntu from this menu I get:

root (hd1,0) kernel /boot/vmlinuz root=/dev/sda1 ro console=yyy0 quiet splash
Error 15: File not found

When I try Windows from the Grub menue I get:

root (hd1,1) Error 22 No such partition.

Any ideas guys? Getting quite frustrated, seeing as how I already lost my original windows partition (don't ask) and haven't made much progress all night...

---

### Post by eqisow on 2005-04-16
OK, wellll.... I discovered if (under Grub) I manually change the command hd1,0 (linux) or hd1,1 (win) to hd0,0 and hd0,1 respectively, it boots... but I'm having to manually change this before booting every time. Is there any way to fix this permanently? Also, Ubuntu booted, finished the installation, then prompted me with the log-in. Upon logging in it put my at a brown screen with my mouse... and then nothin. I ahven't tried again yet, to see if I get the same result... I will in a moment, I wanted to give an update here first.

---

### Post by eqisow on 2005-04-16
OK... sooo, I logged into the terminal, which worked, and did sudo apt-get install kubuntu-desktop... maybe replacing the desktop manager would work... worth a shot, right? Well it does the same thing as before. Also, if I try (at the log-in screen) to pick between a Gome, KDE, etc session... it immediately freezes and I have to reboot.  It does this as soon as I click to select one, no matter which one.

---

### Post by eqisow on 2005-04-16
So I've been browsing some other forums... I've tried updating nvidia drivers (sudo apt-get update / sudo apt-get install nvidia-glx) and installing Xwindows. The command 'sudo apt-get install x-window-system' gives me the following:

Package x-window-system is not available, but is referred to by another package. This man mean the package is missing, has been obsoleted or is only available from another source. 

So... yep... still lookin for ideas. :p

---

