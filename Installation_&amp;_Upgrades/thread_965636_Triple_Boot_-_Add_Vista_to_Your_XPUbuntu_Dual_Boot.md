---
title: "Triple Boot - Add Vista to Your XP/Ubuntu Dual Boot"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by zobcat on 2008-10-31
I've been running a dual boot setup with XP and Ubuntu installed on a Dell XPS M1210 Laptop. I'd like to add Vista to the mix to make a triple boot system. I know that it is better to run each OS on a separate hard drive, but this is a laptop. So, all I have to work with are partitions. Normally, one would create a dual boot with XP and Vista, then add Ubuntu over the top to create the triple boot, but I do not intend on wiping my current OS's. Does anyone have any experience with this? Thanks in advance!

---

### Post by caljohnsmith on 2008-10-31
I would highly recommend "hiding" your XP partition so that Windows Vista doesn't put all its boot files in your XP partition, which is what it will do by default. That way you can keep them entirely separate, and it will be easy to boot each one from Grub. To hide the XP partition, first you need the Grub notation for it:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
...etc.
```
So, if your XP is on sda1 for example, do:
```
sudo grub
grub> hide (hd0,0)
grub> quit
```
Then go about installing Vista, and after Vista is installed you can unhide the XP partition:
```
sudo grub
grub> unhide (hd0,0)
```
Next you'll need to reinstall Grub to the MBR (Master Boot Record), because Vista will have installed a Windows MBR:
```
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then you should be all set except for adding an entry in your Grub's menu.lst to boot Vista. See if you can get this far and we can work from here, otherwise let me know if you run into problems. :)

---

### Post by zobcat on 2008-10-31
Well, I got as far as hiding my XP partition and creating a new ntfs partition. But, Vista installation stops before it even starts. I'm getting the error, 
[INDENT]"Windows could not assign a drive letter to a partition on disk 0.
The error occurred while preparing the partition selected for
installation. Error code 0x80004005"[/INDENT]
Also, I can actually see the XP partition in the Vista setup even though I followed the instructions to hide it.

---

