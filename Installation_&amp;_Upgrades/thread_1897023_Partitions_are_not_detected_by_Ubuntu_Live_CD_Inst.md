---
title: "Partitions are not detected by Ubuntu Live CD Installer"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by guillerminn on 2011-12-18
This is the first time I'm trying to install Ubuntu on my PC, I've worked with other Linux-based Distros but always as live-USB. Any way, I'm quite noob with linux, and my english is not extremely good, but I'll try to explain my self as fine as I can.
I've looked for similar threads but I couldn't find anything that could help me.
I'm trying to install Ubuntu 11.10 64bits CD in my PC. When the installer pop-up (Ubiquity?) it doesn't show me any option like *Try or Install*, or the *Windows compatible installation.* Once selected the language and the wifi settings it's take me to the partitition manager but it's empty.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209317&stc=1&d=1324217595[/IMG]
If I click Install Now it says "No root file system is defined. Please correct this from the partitioning menu."
Gparted does recognize the partition ins sda:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209318&stc=1&d=1324217601[/IMG]

· **Sda2 and 3** are for Windows 7
· I've created **sda1** formated in ext4 to see if Ubuntu recognized it, but it had no effect.
· Actually, **sda5** is the only partition I care, the Windows one it's just installed, i can erase it and install Windows again, but I cannot loose sda5 partition.

I've also tried to install the 11.10 DVD version, the 32bit version, installing it from Windows through Wubi, but I always have the same result.

Did anyone have this problem or know how to solve it?

Thank you very much for your attention and help.

---

### Post by coffeecat on 2011-12-18
Welcome to the forum!

You get this problem with Ubiquity if there is residual RAID metadata on the drive. Was the drive ever used in a RAID? There is a simple terminal command to remove the RAID metadata. I'll see if I can find it for you.

---

### Post by guillerminn on 2011-12-18
Thank you for your help, I've tried this:

**sudo apt-get remove dmraid**

I'm installing the SO right now, I'll tell if the problem is solved when I reboot.

---

### Post by coffeecat on 2011-12-18
> **guillerminn said:**
> 
**sudo apt-get remove dmraid**


Ah, no. That's the command to uninstall the dmraid application from the system. You need dmraid to remove metadata from the drive. You can't uninstall dmraid from the live CD anyway, so from the live CD session, this command should work:

```
sudo dmraid -E -r /dev/sda
```

---

### Post by guillerminn on 2011-12-19
I've done what you said, everything's gone great. 
Thank you very much.

---

