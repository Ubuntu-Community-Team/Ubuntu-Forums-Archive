---
title: "Windows 8 Gone?"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by Vatteck on 2013-03-29
Hello, today I decided to install ubuntu from a usb drive. I chose to install alongside windows 8, and it asked me to divide it into partitions with the slider thing, and all was done. However, my computer was restarted afterwards, and i did not see the usual boot screen. Instead the screen stayed blank until finally the ubuntu logo appeared, and booted. I was worred, so I installed GParted, and checked. There appears to be an error on my on HDD, and the other where ubuntu is is fine. There's no boot screen or anything though, and I can't even go into the BIOS.
 [IMG]http://i.imgur.com/M8NWmF5h.png[/IMG]


[IMG]http://i.imgur.com/WIZSEUp.png[/IMG]

[IMG]http://i.imgur.com/ZLcCPFy.jpg[/IMG]

---

### Post by Mark Phelps on 2013-03-29
You should have come here and asked BEFORE you did the resize thing with the slider -- as I would have told you NOT to do that, as it often results in corruption of the Windows file system.

You could try using Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Vatteck on 2013-03-29
That doesn't seem to be working. For some reason, my monitor doesn't receive a signal until ubuntu boots, but when the no signal thing was going on, I tried pressing the arrow keys and pressing enter, and memtest popped up. I just don't understand why I can't even see the the loading screen when the computer starts up, where you can go into the bios. Sorry, i don't really know what that screen is called, but I hope you know what I mean.

---

### Post by Vatteck on 2013-03-29
Boot-repair is telling me

The boot files of [The OS now in use - Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

I don't really know if that's the problem though..

---

### Post by Vatteck on 2013-03-29
Okay, I somehow booted into windows with random button presses, and deleted the ubuntu partitions. Guess I'll stick with wubi..

EDIT: Sorry about the triple posting.. forgot that's a no-no.

---

### Post by darkod on 2013-03-29
If the grub boot menu doesn't show up you can try setting a lower resolution. You can do that by editing /etc/default/grub and removing the #symbol for the line saying like GFX MODE 640x480. Save and close the file. Run sudo update-grub to update the grub.cfg. Reboot and see if it helped.

---

### Post by darkod on 2013-03-29
No need to stick with wubi, that's not even proper ubuntu. Set the resolution and the boot menu should show up fine. Up to you.

---

