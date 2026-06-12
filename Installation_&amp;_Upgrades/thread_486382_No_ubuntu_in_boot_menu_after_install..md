---
title: "No ubuntu in boot menu after install."
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by mark0077 on 2007-06-27
Hi all,

I am sure some of you will be able to help me, hopefully. I have installed Ubuntu 7.04 onto my machine.

Here is my drive setup.

Drive 1: Partition 1 (only), Windows XP

Drive 2: 
  Partition 1, Vista
  Partition 2, ext3 partition for ubuntu (which I believe successfully installed, at least it told me it did)
  Partition 3, swap partition

When my pc boots, I recieve a menu that simply shows Windows XP and Vista on it, its the new fancy vista bootloader menu. But no sign of ubuntu after installation...

Looking in partition magic I see only one active partition on my whole system, and that is on drive 1.

Any help would be great. Thanks!!!

---

### Post by confused57 on 2007-06-28
Try booting first to your hard drive 2 just to see if grub might have been installed to the mbr of this drive.

If this doesn't work, you might download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD may be able to boot your Ubuntu partition...

---

### Post by mark0077 on 2007-06-28
Damn, disk 2 doesn't boot at all, probably because it has no active partition set.

I really want to work through these problems :(

---

### Post by confused57 on 2007-06-28
> **mark0077 said:**
> Damn, disk 2 doesn't boot at all, probably because it has no active partition set.

I really want to work through these problems :(
Are you getting a grub boot menu, when you boot first to your disk 2?  If you're not, you could use the live cd to install grub to it's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Read the thread I provided, but it would be something like this:
```
sudo grub
find /boot/grub/stage1
```
use whatever the result is for:
```
root (hd1,x)
setup (hd1)
quit
```

If you then get a grub boot menu, then highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...if it works, you can make it permanent.

---

### Post by mark0077 on 2007-06-28
wow great, I am now able to boot into Ubunto aswell as select vista and xp from a sub menu.

One final problem, I guess I should look elsewhere, Ubuntu complains that it cannot start X, even though the Live CD booted up and showed a lovely GUI. I cannot get a GUI using my newly installed Ubuntu however.... :(

Nvidia 7600GT

---

### Post by confused57 on 2007-06-28
> **mark0077 said:**
> wow great, I am now able to boot into Ubunto aswell as select vista and xp from a sub menu.

One final problem, I guess I should look elsewhere, Ubuntu complains that it cannot start X, even though the Live CD booted up and showed a lovely GUI. I cannot get a GUI using my newly installed Ubuntu however.... :(

Nvidia 7600GT
When Ubuntu complains it cannot start X, you can press "Ctrl+Alt+F1", this should get you to a console prompt, then you would enter:
```
sudo dpkg-reconfigure xserver-xorg
```

For the screen to select video driver, you can try "nv" first, then if it doesn't work try "vesa"...once you save this configuration, then type in "startx", without the quotes...if this doesn't work, then press "Ctrl+Alt+F7", then "Ctrl+Alt+Backspace", this should restart GDM.

Once you get a GUI, then you can look into installing the "nvidia" drivers, for 3D acceleration for your card:
[http://ubuntuforums.org/showpost.php?p=2925959&postcount=2](http://ubuntuforums.org/showpost.php?p=2925959&postcount=2)
just check out the links in this post for installing Nvidia drivers...the manual method in the link is for Dapper, this is for Feisty:
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Added:  It might be easier to change the video driver manually, "Ctrl+Alt+F1" to get to a console, login, then:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
sudo nano xorg.conf
```
change the driver to "nv" or "vesa"...with quotes, then Ctrl+X, y, enter...to save...then startx or
"Ctrl+Alt+F7", then "Ctrl+Alt+Backspace"...

---

