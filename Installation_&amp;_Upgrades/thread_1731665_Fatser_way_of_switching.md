---
title: "Fatser way of switching"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by TheExposedOne on 2011-04-17
I think this is in the right category
I'd like to switch from windows to ubuntu right now but i can't be bothered to back up all my data
Is there a way of installing ubuntu over windows and keep the files
I know they're completely different os' Linux/Windows and the procedure isn't as simple as pop in the disc and upgrade but possibly somthing like, install ubuntu transfer files and remove windows without changing partitions or risking all my hdd space going due to the file transfer

thanks

edit: woops in the title

---

### Post by dino99 on 2011-04-17
why not choosing the secure way, install ubuntu as your first Os but keep win.
First always clean the room with win:
- defrag
- chkdsk
- resize the partitions to make room for ubuntu

then reboot and set the bios to boot on cdrom or usb to make installation following this howto:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by TheExposedOne on 2011-04-17
how do i make windows the 2nd partition whilst making ubuntu the first

---

### Post by Frogs Hair on 2011-04-17
Woops Misread !

---

### Post by dino99 on 2011-04-17
> **TheExposedOne said:**
> how do i make windows the 2nd partition whilst making ubuntu the first

with multiple OS on the same system (real installed prefered, not fake like wubi) the bootloader of ubuntu will deal with order when you set bootup-manager (set it after installation). At boot time the loader (grub) will popup its menu where you pick either ubuntu or windows to boot on.

note: let windows partitions at the beginning of hdd

---

### Post by TheExposedOne on 2011-04-17
@Frogs Hair  so, wubi installs inside windows, meaning in the Program Files dir right?
That means i can't get rid of windows then
or can I?

@dino99 And that means I can't change the partition order either

---

### Post by Frogs Hair on 2011-04-17
I misread your post.

@Frogs Hair so, wubi installs inside windows, meaning in the Program Files dir right?
That means i can't get rid of windows then
 or can I?

It is possible to move a Wubi installation to its own partition , but there is no point if you already have a dual boot .

---

### Post by TheExposedOne on 2011-04-17
i'd dual boot but am running out of space
well i'll wait till summer when i have loads of spare time on my hands to transfer the data

---

