---
title: "Ubuntu says BusyBox can't create a directory/cow/on/root the structure needs cleaning"
date: 2024-04-06
forum: Installation &amp; Upgrades
---

### Post by tgodmuna on 2024-04-06
I tried installing Ubuntu I got this error message saying:
 BusyBox V1. 30.1 Ubuntu 1:1.30.1-7bubuntu3) built-in she (ash).
Enter help for a list of built-in commands.

(Initramfs) Mkdir: can't create a directory /cow/on/root failed: structure needs cleaning overlay Mount failed.
[9.842059] EXT4-fs error (device sdb2) : ext4_validate_block_bitmap:429:comm ext4lazyinit:bg14:block 458752 : invalid block bitmap.


How do I resolve this issue above

---

### Post by yancek on 2024-04-06
Which release of Ubuntu are you using?  Did you download from the Ubuntu site?  Did you verify the iso download according to the instructions on the Ubuntu site?  Did you write the iso file to a usb?  If so,  what software did you use?  Is your computer EFI capable?  If so, did you boot in EFI mode?  At what point did you get the error message you report?  Was it when you booted the USB?  If you have an error relating to the mkdir command then you must have been able to boot the install medium.  What were you trying to do when you got this error?  Likely explanations would be a bad download or a bad write to the USB.

---

### Post by tea for one on 2024-04-06
(initramfs) prompt - type exit
You may see more details about the problem e.g. file system corruption as detailed below:-
```
EXT4-fs error (device sdb2)
```

My guess would be that you will need to boot into a live session and run fsck on the partition(s) with errors.

If you've only just installed Ubuntu, it may well be quicker to start from scratch.
Create your target disk with GPT before starting the installer.

---

### Post by MAFoElffen on 2024-04-06
+1 -- w/ tea for one

What he said... Exactly what I was thinking. (If that was on after in install, on the first boot.)

---

