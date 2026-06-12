---
title: "Repairing GRUB loader"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by hemajith on 2008-06-11
I had a dual boot system with XP and Ubuntu. I had to reinstall Windows and installed Vista. Now I cannot get the Ubuntu to load! How can I recover my Ubuntu and get the Grub loader to work?

---

### Post by mxg01 on 2008-06-11
You can restore GRUB using the Ubuntu liveCD.

Here is a thread on how to do it:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by hemajith on 2008-06-11
I tried running the grub shell, it goes to 'grub>'. But when I give 'find /boot/grub/stage1' command, it says 'error15 : file not found'

---

### Post by mxg01 on 2008-06-11
If you know which drive and partition grub is installed on then you can progress to the next step using the values you know. So, if you have one hard drive and /boot on the first partition then type:

```
root (hd0,0)
```

where hd0 is the hard drive and 0 is the partition number. If it's the second partition then it's (hd0,1).

Try that and see how it goes.

---

### Post by meierfra. on 2008-06-11
post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by hemajith on 2008-06-11
This worked! Thank you MXG.... find would not work but I opened the menu.lst file in a text editor and found the partition Ubuntu is installed and then followed the rest of the commands and it was pretty simple afterwards..Thank you very much...

---

