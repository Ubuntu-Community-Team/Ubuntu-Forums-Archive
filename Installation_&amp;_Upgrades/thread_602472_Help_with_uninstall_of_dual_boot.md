---
title: "Help with uninstall of dual boot"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by mgm2rr on 2007-11-04
I did a fresh install of Gutsy a few weeks ago, but I could not get it to work with my video card, so I installed Feisty Fawn on a different partition.  I had been using dual boot, and when it boots, Grub has Feisty as the default and you have to scroll down to select Gutsy if you want to use it.  Well, I solved the video card problem, and I migrated all of my files to Gutsy, so now I would like to format the partition with Feisty on it and use the whole hard drive for Gutsy, but I don't want to break GRUB and make it impossible to boot.  Can I just redo the partitions using GParted, or do I need to do any fancy footwork involving GRUB?  Any advice would be greatly appreciated.

---

### Post by Pumalite on 2007-11-04
Just use Gparted and later reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by celettu on 2007-11-04
First of all, make sure grub is installed on your gutsy partition, so boot into that, then do this:

```
1. sudo grub
2. find /boot/grub/stage1
you should get output like this
(hdx,y)
3. quit
4. sudo grub-install /dev/hdx #this is from your output
5. sudo grub
6. root (hdx,y) #from your output
```

Check if that gives you a grub-menu with gutsy on top.

If everything works, reboot into gutsy, and do

```
mke2fs /dev/<yourfeistypartition>
```

Needless to say, be careful with formatting.

HTH

---

