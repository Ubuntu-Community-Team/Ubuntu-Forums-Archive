---
title: "Ubuntu 12.04 Black screen on boot before Grub"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by cullster on 2013-05-19
Hi there,

I started my computer up yesterday and this problem occurred, after the BIOS logo screen I just get a black screen with a flashing '|'. I have looked around to see what the problem may be, and a lot of threads state it is usually graphics problems with proprietary drivers that can make this happen. However, I have had Ubuntu installed and have been using everyday for almost a year. What may have caused this is when I tried to update my graphics driver, when I was prompted by Steam, although I just got an error message and the driver didn't appear to update. I am unsure how to resolve this issue as the solutions I have come across seem to only apply to people who are booting Ubuntu for the first time, or are having similar problems with a live cd. Furthermore, there appears to be no way to get into the OS to maybe do an update, some solutions suggest pressing shift on boot to get GRUB up, and then edit the GRUB splash screen, though pressing shift does not work. Any help or indication to what may have caused this problem and how I can resolve it would be much appreciated,

Thanks

---

### Post by ajgreeny on 2013-05-19
Try booting to an earlier kernel in case the most recent one is not working for some reason.

If you do not normally see the grub menu hold shift at boot until it appears (possibly repeat presses of Esc if you have UEFI type BIOS).

Good luck!

---

### Post by cullster on 2013-05-19
Yes I do have a UEFI BIOS, although pressing escape still does no get grub up, 

Thanks

---

### Post by jamesisin on 2013-05-19
Two things.

First, do you have any USB drives attached?  Unplug them.  Reboot.

Second, if that does not fix your issue try to login using an Ubuntu LiveCD.  From there open a terminal and run *sudo update-grub*.  Reboot.

---

### Post by VeeDubb on 2013-05-19
In recent releases of GRUB, you get the boot menu by holding down the shift key, rather than pressing Esc.

---

### Post by ajgreeny on 2013-05-20
> **VeeDubb said:**
> In recent releases of GRUB, you get the boot menu by holding down the shift key, rather than pressing Esc.

Not always!

On my new machine with UEFI install of Xubuntu 12.04 I have to press Esc; Shift does nothing, and I believe this may be either specific hardware related,  or a result of the use of UEFI.  See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI")

---

