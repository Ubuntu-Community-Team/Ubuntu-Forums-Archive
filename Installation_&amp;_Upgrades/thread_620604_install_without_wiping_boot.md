---
title: "install without wiping boot"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by djre on 2007-11-22
Hi guys!
This is my first time to install ubuntu(kubuntu actually, i hope no one flames me :) ). I have the gutsy gibbon kubuntu live cd. I booted it and tried it out. I must say I'm impressed with how it looks. So I wanted to install it.
   However, I have one bit problem. I prepared my harddrive for a triple boot system. The other two systems being windows and archlinux. I used gparted when I prepared my hard drive. So here's how my partition looks.

sda1 Windows (primary partition)
sda2-3 Linux (extended partition)
    sda5     /boot
    sda6-7  swap
    sda8     archlinux /
    sda9     (kubuntu) /
sda4 Fat32 (primary partition)

 I clicked the install icon in the desktop. But when I came to the preparing harddrive part that's were I have problem. The installer wants to format my /boot partition and as you can see, I have that shared with archlinux so Im definitely not wiping it out.

Help. Is there any way to work around this problem?

Thanks in advance.

---

### Post by Pumalite on 2007-11-22
Use Manual and choose your partition.

---

### Post by djre on 2007-11-22
that's what i chose. i think the automatic mode cleans the whole drive so i chose manual and that's my problem. is there something "more manual" mode?

---

### Post by Pumalite on 2007-11-22
Manual lets you choose sda9 and that should leave sda5 alone.

---

### Post by rnwright on 2007-11-22
Use Wubi 


[http://wubi-installer.org/](http://wubi-installer.org/)




Wubi is an unofficial Ubuntu installer for Windows users that will bring you into the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other application. If you heard about Linux and Ubuntu, if you wanted to try them but you were afraid, this is for you.


From there site:

Wubi is Safe

It does not require you to modify the partitions of your PC, or to use a different bootloader.

Wubi is Simple

Just run the installer, no need to burn a CD.

Wubi is Discrete

Wubi keeps most of the files in one folder, and If you do not like, you can simply uninstall it.

Wubi is Free

Wubi (like Ubuntu) is free as in beer and as in freedom. You will get this part later on, the important thing now is that it cost absolutely nothing, it is our gift to you...

---

