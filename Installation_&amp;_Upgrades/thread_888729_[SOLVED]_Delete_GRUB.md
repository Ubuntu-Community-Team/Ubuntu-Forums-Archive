---
title: "[SOLVED] Delete GRUB?"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by MaddoxBT on 2008-08-13
Sorry if this is in the wrong place. Can't seem to figure out where it goes.

I installed Ubuntu on a whim recently and found that I liked it a lot more than I thought. I gave SuSE and Fedora a shot as well, but neither of them seemed as stable and intuitive as Ubuntu, so I decided to go with Ubuntu. 

I have come to realize that I don't need Windows anymore either, so there's no longer a reason for me to dual-boot. I want to get rid of the bootloader screen where I can choose between Windows, Ubuntu and SuSE. I just want it to boot straight into Ubuntu.

Is there a way to have it do that? Can I delete grub? How would I do that?

---

### Post by mattduckman on 2008-08-13
you need GRUB to boot into Ubuntu, but you can hide and/or shorten the time that GRUB waits for you. you'll have to edit /boot/grub/menu.lst. in a terminal type
```
gksudo gedit /boot/grub/menu.lst
```
and at the top there should be options with instructions for changing delay and hiding. let me know if you need additional help.

---

### Post by meindian523 on 2008-08-13
Don't need to delete Grub.Once you have deleted the Windows partitions,just remove the entries for Windows from /boot/grub/menu.lst.It's usually at the end of the file.

---

### Post by oldos2er on 2008-08-13
> **mattduckman said:**
> 
```
sudo gedit /boot/grub/menu.lst
```

 Should be "gksudo gedit /boot/grub/menu.lst"

---

### Post by MaddoxBT on 2008-08-13
Thank you guys! Solved!

---

### Post by mesyos on 2010-01-07
In Karmic Koala the config file menu.lst has been removed and i edited the file " grub.cfg " contained in " /boot/grub/ " so to remove the entries of old kernel images...

Now i wonder if it was wrong doing so?

It does work well but still...
Anyone would happen to know?

---

### Post by audiomick on 2010-01-07
You shouldn't actually edit that one directly, I believe.
Look at this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
for instructions on Grub2. The file you refer to is mentioned in the "file structure" section, which is a little way down, followed by a section on configuring, which tells you which file to edit.

However

If it is all working, I would count myself lucky and not mess around with it anymore. ;)

---

