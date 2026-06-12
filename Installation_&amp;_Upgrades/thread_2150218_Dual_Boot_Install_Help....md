---
title: "Dual Boot Install Help..."
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by aj5string27 on 2013-05-31
Hi,

Right - I am sorting out my desktop that has had various versions of Linux and Windows on over the years.  I currently have Windows 8 installed, dual booting with Dream Studio.

I want to change/upgrade/install Ubuntu to where Dream Studio is, and leave Windows 8 totally untouched... now, I know this should be doable but I just can't seem to do it.  I thought the installer would give me the option to put ubuntu where Dream Studio is - it didn't, so I used the advanced partioner but couldn't quite get where I wanted!

Any tips, pointers of guidance would be much appreciated!

Alex.

---

### Post by dino99 on 2013-05-31
hi Alex
i cant help you directly dealing with w8; but there are lot of threads on ubuntuforums with such target

---

### Post by presence1960 on 2013-06-01
You want to choose "Something Else" from the options the installer gives you. Then you have to manually set up the install to that partition. Highlight the partition and click the change tab. Select ext 4 as filesystem and in the bottom drop down box select " / " as mount point. Continue ahead with the next step. Assuming you have only one internal disk sda will be where GRUB bootloader goes. You can leave that box alone unless you have more than one disk. If so we need your partition table to proceed.

---

