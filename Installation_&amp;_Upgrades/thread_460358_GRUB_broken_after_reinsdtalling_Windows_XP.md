---
title: "GRUB broken after reinsdtalling Windows XP?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by roadkill on 2007-05-31
I have a dual-boot setup with Windows XP in my first partition, and Ubuntu in the last, with the swap space between them.  Last night I reinstalled XP, and think I made a couple of mistakes in the process of restoring GRUB which might have wrecked it completely.

First (and I admit I don't know what I was thinking when I tried this) I booted from the Feisty live CD and attempted to reinstall GRUB via Synaptic.  I wasn't expecting a successful installation, but it reported one anyway.  Booted straight to Windows on the next try, though.

Then I read [this document]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") and tried the first option, restoring GRUB while preserving Windows bootloader.  GRUB reported a successful installation, but again it booted straight to Windows on restart.

Finally I tried the troubleshooting section from the same document, and again GRUB reported a successful installation, but it still boots straight into Windows XP at restart.

Can anyone offer me some good advice?

---

### Post by bulldog on 2007-05-31
To reinstall GRUB you need the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by roadkill on 2007-05-31
> **bulldog said:**
> To reinstall GRUB you need the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next command 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

That's one of the processes I've tried, and I've had no error message, but it's made no difference.

---

### Post by merlinus on 2007-05-31
Please post the contents of /boot/grub/menu.lst

-merlin

---

### Post by roadkill on 2007-06-01
The file /boot/grub/menu.lst doesn't exist.  The contents of the /boot/grub folder are:

root@ubuntu:/# ls /boot/grub
default        fat_stage1_5       minix_stage1_5     stage2
device.map     installed-version  reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  jfs_stage1_5       stage1

---

### Post by roadkill on 2007-06-01
Weirdly, after I repeated the process to try and get the contents of /boot/grub/menu.lst and restarted, GRUB began working again.  So either I missed something the first few times or...

...you know what?  I'm not going to ask any questions.  I'm just going to hug my tower case and tell it everything's OK now.

Although I've just realised that there's no HD icon for my Windows partition on the Gnome desktop anymore.  Still, I'll call that a small price to pay in order to get all my documents back.

---

### Post by bulldog on 2007-06-01
> **roadkill said:**
> Weirdly, after I repeated the process to try and get the contents of /boot/grub/menu.lst and restarted, GRUB began working again.  So either I missed something the first few times or...

...you know what?  I'm not going to ask any questions.  I'm just going to hug my tower case and tell it everything's OK now.

Although I've just realised that there's no HD icon for my Windows partition on the Gnome desktop anymore.  Still, I'll call that a small price to pay in order to get all my documents back.


If your windows partitions are listed in fstab,you can try Alt-F2 and type  gconf-editor.
Now navigate to ==>apps==>nautilus==>desktop and look for the option 'volumes visible'.

---

