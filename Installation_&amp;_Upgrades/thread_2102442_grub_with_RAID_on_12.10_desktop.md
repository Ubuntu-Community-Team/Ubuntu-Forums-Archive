---
title: "grub with RAID on 12.10 desktop"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by botcolon on 2013-01-07
hi there,

I have installed 12.10 desktop with an underlying RAID1 configuration but having issues with GRUB. I have tried for the last week to circumnavigate this issue, and with the help of boot-repair I am hoping I can get some help from this forum. 

After the boot-repair I now get a grub menu (a first), but when starting up the O/S it stays on the purple splash screen.

Below is the boot-repair log 
[http://paste.ubuntu.com/1506701/]("http://paste.ubuntu.com/1506701/")

-the raid is md3 with members SDB1 and SDC1.
-I have no separate /boot
-and boot-repair was actioned via a liveCD (desktop 64bit version)

any pointers on what I should do differently would be greatly appreciated.

thanks
michael

---

### Post by darkod on 2013-01-07
And what is the md2 device? It doesn't seem configured/working correctly.

The purple screen might be video driver issue. What video adapter do you have?

You can try this. In the grub menu, highlight the ubuntu entry and press 'e' for edit. In the line starting with linux, move the cursor towards the end with the arrows keys and delete the 'quiet splash'. Press Ctrl+X or F10 to boot.

That should remove the image while booting and show a scrolling text. When it stops somewhere, it will usually say what is the problem in the last few lines.

I don't know how you tried to install ubuntu and especially grub, but installing grub with software raid is very easy and trouble free. If there were problems, they might be related to why it's not working correctly right now.
Usually grub2 can be problematic to install on fakeraid, but not with software raid since it installs the same as normal install, on the MBR of the disk(s).

---

