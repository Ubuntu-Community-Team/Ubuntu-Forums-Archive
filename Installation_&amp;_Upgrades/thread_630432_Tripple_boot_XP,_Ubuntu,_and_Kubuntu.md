---
title: "Tripple boot: XP, Ubuntu, and Kubuntu"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by JaggedOne on 2007-12-03
I currently have XP and ubuntu installed. I have about 20 gb of free space on my ubuntu partition that I want to reallocate for a kubuntu install. I tried to do it on my own but kept getting errors about things like a lack of a root partition or too many partitions during the disk partitioning phase of the kubuntu install. In what order do I need to resize my current partitions, install kubuntu, sacrifice goats to get this working?

---

### Post by kebes on 2007-12-03
> **JaggedOne said:**
> I currently have XP and ubuntu installed. I have about 20 gb of free space on my ubuntu partition that I want to reallocate for a kubuntu install. I tried to do it on my own but kept getting errors about things like a lack of a root partition or too many partitions during the disk partitioning phase of the kubuntu install. In what order do I need to resize my current partitions, install kubuntu, sacrifice goats to get this working?

The difference between Ubuntu and Kubuntu is only the desktop environment (Gnome vs. KDE). So, actually, you can install KDE into your Ubuntu partition, and you'll be able to switch between the two environments easily. (You won't even have to reboot, just exit the desktop session, and you'll have the option of using either KDE or Gnome on login.)

To install Kubuntu, just add the package "kubuntu-desktop" which will install KDE and the various KDE applications.


If you absolutely want Kubuntu on a separate partition, that can also be done, of course.

---

### Post by JaggedOne on 2007-12-03
I know I can. I would like to keep the boots seperate.

---

### Post by JaggedOne on 2007-12-04
I hate to have to bump but I still need an answer. I would really like to keep the two boots separate. How do I do this?

---

### Post by kebes on 2007-12-04
> **JaggedOne said:**
> In what order do I need to resize my current partitions, install kubuntu, sacrifice goats to get this working?

The Kubuntu installer will provide an option for resizing and formatting partitions, so you should just start the installer and use its features. (Note: Always **perform a backup** before using a partition tool!)

So, basically:
1. Boot the Kubuntu CD into the live session, and start the installer.
2. At the partitioning step ("Prepare disk space"), select the manual option.
3. Shrink other partitions as required to make space for Kubuntu (~6 Gb is typically enough).
4. You will have to assign mount-points for the various partitions. You can use the same SWAP for both Linux installs (Ubuntu and Kubuntu). You should assign the newly freed space to be the root partition ("/") for the new install. If you have your "/home/" on a separate partition (convenient for multi-booting), you should assign that manually.
5. Let the installer format and install files. (Make sure that you have selected "format" only for the new partition you have created! Don't let it wipe your other partitions!)
6. When it's done, it will reboot.


Now, the installer ~should~ have added all the recognized partitions to the bootloader, so that when you boot up you see a list of options. You can then pick the operating system you want. However if it doesn't list all the ones you want, you can fix it by editing the file:
/boot/grub/menu.lst
while running Linux. You can also manually run grub from Linux (from your install, the LiveCD, or the recovery console) to fix the bootloader.

From your original post, it sounds like you tried to do this but ran into some kind of error. If you run into an error again, it would help if you describe in detail what you were trying to do, what options you set, and exactly what the message was.

Hope that helps.

---

