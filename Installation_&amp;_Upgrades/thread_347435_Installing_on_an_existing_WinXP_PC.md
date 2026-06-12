---
title: "Installing on an existing WinXP PC"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by une on 2007-01-27
I have access to a WinXP AMD processor PC (one HD) at work that I want to do some Linux work on, writing and testing C++, Java and BASH shell script code on. I therefore want to install ubuntu on this PC. However if I do anything that changes in ANY way how other users of this PC have to interact with this PC, I will be hung, drawn and quartered.
I have used my ubuntu CD as a Live CD on this PC with no trouble. However it seems that in this mode of use I cannot save data or configuration files to the HD or to a USB memory stick for later use by the Live CD. So I would like to install ubuntu on the HD.

What I want is for **nobody to even notice that I have installed ubuntu.** Only when I need to use it could a Linux Ubuntu session be invoked. The main worry I have concerns booting. In the past I have found that having Linux and Windows on the same HD often results in boot loader hassles.
If I install Ubuntu how and when would the user be asked which OS to choose?
Ideally they would not be asked at all.
Could I have it so Windows would always boot unless something extra was done at startup?   
I searched for similar threads but could not find one that answered my question.

---

### Post by PurplePenguin on 2007-01-27
There might be a better way, but you could set grub to display the boot selection menu for a single second.  That way, if you're one of the other users, you probably won't even be paying attention.  If you want to boot into ubuntu, you'll just have to keep your eyes open for when the boot menu comes up and quickly hit a button so you can make the change.

There might be a better way that I don't know of that will make it even more transparent to the other users.

Another possibility is using one of the linux distributions that work inside windows.  There are such distros that run off of USB keys and allow you to use the USB key's memory as disk space.  Also, Puppy Linux can be burned onto a CD and any changes you make can also be saved (multisession burning).  With Puppy Linux, you won't have to install anything on your hard drive... it will only boot up into linux if you stick your CD or USB drive in then reboot.

---

### Post by une on 2007-01-27
I have investigated the Puupy Linux option and am impressed by this distro. It works as you say. I would ideally like a full featured distro thus my interest in ubuntu.
So it seems you think that a Grub "Choose OS" window will appear at boot, but that I can alter the time for which it is displayed. Is this correct?

---

### Post by une on 2007-01-27
I have investigated the Puupy Linux option and am impressed by this distro. It works as you say. I would ideally like a full featured distro thus my interest in ubuntu.
So it seems you think that a Grub "Choose OS" window will appear at boot, but that I can alter the time for which it is displayed. Is this correct?
Also, will the ubuntu install program detect existing partitions, leave them alone and create the new partitions it needs?

---

### Post by PurplePenguin on 2007-01-27
If you go the Puppy route, you could load it from USB key or CD, therefore you wouldn't need grub.

If you go for Ubuntu, you'll want to use grub, but you can set the timeout from the default of (I believe) ten seconds to, say, 1 or 2.  If Windows is the default operating system in grub, it'll continue to load Windows if nobody presses anything during the second or two that grub is displayed.

Both Puppy and Ubuntu have really good partition tools that will allow you to make new partitions.  Just to be safe, though, you should back up any important information before doing anything with partitions.

---

