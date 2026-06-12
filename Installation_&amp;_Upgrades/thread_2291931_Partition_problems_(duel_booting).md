---
title: "Partition problems (duel booting)"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Danfun64 on 2015-08-24
Hello. I recently installed Lubuntu as a duel boot setup using Unetbootin and the netboot image through usb stick. After the installation I tried having kwin as the desktop manager. When I tried that, the top window bar-thingy (don't know what it's called, but with minimize/maximize/close buttons) didn't appear. Having had success with kwin and xfce in the past, I decided to delete my lubuntu partition (using Tuxboot GParted Live) and install Xubuntu in it's place. However, I didn't intend on that being so literal...

After I apparently deleted the linux partitions I used the netboot image again to try to install xubuntu. When I tried to use "guided-use free space remaining", it froze at 33%. I tried rebooting, and somehow managed to "install" xubuntu. It turned out to be install right on top of where the Lubuntu partition was supposed to be deleted, as my Firefox history remained despite sync not being setup in either lubuntu or xubuntu.

For the record, despite duel booting with Windows 10 (which has attracted lots of threads here), that isn't the issue, and I can access the Windows partition without issue.

---

### Post by Bucky Ball on 2015-08-24
Try using 'Something Else' when you get to partitioning instead. Completely delete the Lubuntu/Xubuntu partition with Gparted prior to the install leaving only free/unallocated space to install to. Create a / and /swap partition. /swap only need to be 2Gb and / 20-25Gb (and that may be too much). This would rely on you storing your personal data on another, larger partition. If this is not the case, make / big.

Sounds like the install has marked the Lubuntu partition to use but not to format as it seems to have added a Xubuntu install to what you already have. The result appears to be the same as if you'd have installed xubuntu-desktop while running Lubuntu.

Couple of things, though: Where is your Firefox profile stored? On the same partition you thought you were installing to or a different separate /home partition or other data partition?

---

### Post by Danfun64 on 2015-08-24
> **Bucky Ball said:**
> Couple of things, though: Where is your Firefox profile stored? On the same partition you thought you were installing to or a different separate /home partition or other data partition?

The partition I thought I was going to install to.

edit: I created the necessary partitions through gparted and routed the netinstall setup to use them. Everything is working correctly so far.

---

### Post by Danfun64 on 2015-08-24
Turns out my other problem (no window bar thingy appearing in kwin) is an issue with xubuntu as well. I'm guessing the new qt5 version of kwin is to blame. Anyone got any recommendations for setting the qt5 theme?

Edit: This question has nothing to do with this section of the forums, or the thread title. Marking as solved.

---

### Post by Bucky Ball on 2015-08-25
> **Danfun64 said:**
> Edit: This question has nothing to do with this section of the forums, or the thread title. Marking as solved.

Good plan and good news. Mark this as solved (first link in my signature for how) and post a new thread for the other issue. Good luck. :)

---

