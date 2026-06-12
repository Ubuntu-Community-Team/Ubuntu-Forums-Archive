---
title: "Working with grub2"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by mikester01 on 2011-03-03
I need to make a change to my grub configuration. For systems based on grub1, the change I need to make is quite simple - change the root device from a UUID based reference to /dev/hda1. For example:
 
```

root=UUID=XXXXXXXXX-XXXX-XXXX-XXXXXXXX

```
 
to 
 
```
 
root=/dev/hda1

```
 
I've spent the last two hours reading through all the grub2 documentation, and I've yet to figure out how I can do this. I know the easiest way is to create a new entry in /etc/grub.d (for example, 11_my_boot), but I've been unsuccessful so far.
 
Is there some trick that I'm missing? Is there a guide that details how to do this? I've read through the GRUB2 Basics in this thread ([http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)), but the Adding Entries to Grub 2 didn't answer my question. 
 
-M

---

### Post by oldfred on 2011-03-03
UUID's are preferred as they are less likely to change.

The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

In this file from drs305's instructions in above link:
/etc/default/grub

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

sudo update-grub

---

