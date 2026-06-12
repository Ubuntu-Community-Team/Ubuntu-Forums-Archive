---
title: "Wubi to full install"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by malcmail on 2010-08-30
My desktop has been running both windows and ubuntu for a couple of months via wubi. The plan is to eventually migrate fully to ubuntu though.  Simple question, I hope, is it easy to effectively remove the windows side so that I dont have to make a new reinstall of ubuntu from scratch?

Thanks in advance.

---

### Post by bcbc on 2010-08-30
You can't exactly remove the 'windows side'. Wubi installs ubuntu to a virtual disk on the windows file system, so you need to either [migrate this]("http://ubuntuforums.org/showthread.php?t=1519354") to a direct partition, or backup your data and reinstall ubuntu.

If you have room on your drive, create new partition(s) for Ubuntu and migrate it. After that you can do what you want with the windows partition.

---

### Post by darthdart on 2010-08-30
by "do what you want" you mean like you can actually delete it? I'm having a different problem since I'm having a dual boot xp and ubuntu.. but I want to remove XP. does it mean I can delete xp without messing up grub?

---

### Post by bcbc on 2010-08-30
> **darthdart said:**
> by "do what you want" you mean like you can actually delete it? I'm having a different problem since I'm having a dual boot xp and ubuntu.. but I want to remove XP. does it mean I can delete xp without messing up grub?

It's possible I suppose to change the partition ordering by deleting/splitting an existing partition. But as long as you do it from your Ubuntu install e.g. using gparted, just running
```
sudo update-grub
```
before rebooting will reorient grub.

It's not a serious problem to recover from - you can manually override the grub boot instructions if necessary. But any partitioning carries risks and backing up is a necessary precaution.
I'd create a thread stating what you want to do, and then you'll get advice specific to your needs.

---

### Post by malcmail on 2010-09-05
Ah so wubi effectively installs Ubuntu inside Windows (kind of) ? This would answer why its been a little less than steller in performance. There are just something on the Windows side I need to deal with then would like to ditch it but have made a lot of changes to Ubuntu installation which I can't remember :-s.

Thanks for the help anyway fella :)

---

