---
title: "Help--&gt; cant boot to ubuntu"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by ayet on 2007-11-29
I format my drive C where windows is installed and then re-installed windowsXP, but after that it boot and there is no GRUB boot loader, how do I return the grub boot menu?

---

### Post by Pumalite on 2007-11-29
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(installing XP after Ubuntu is many times a problem and not the ideal)

---

### Post by ayet on 2007-11-29
> **catlett said:**
> This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```
find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Finally exit the grub shell
```
quit
```

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.


@Pumalite
thnks. for the help problem solved:popcorn:

---

### Post by Pumalite on 2007-11-29
You are welcome. Good luck.

---

