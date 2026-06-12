---
title: "Can you install ubuntu on an external Maxtor usb HDD?"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by a_washington on 2008-10-25
And if so how can I dual boot it?:confused:

---

### Post by Pumalite on 2008-10-25
You can install to an external drive. Use your Live CD and at step 7; go to 'Advanced Tab' and change (hd0) for /dev/???, where ??? is your external drive ( find out with sudo fdisk -lu)
It's better than installing Grub on your internal drive.
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by a_washington on 2008-10-25
And when I do that how can I make it show up when I want to choose which OS I want to boot? And what text should I add to the boot.ini file?:confused:

---

### Post by Pumalite on 2008-10-25
You will have a boot loader (Grub) in the external drive. You have to change your BIOS to boot from USB

---

### Post by a_washington on 2008-10-26
> **Pumalite said:**
> You will have a boot loader (Grub) in the external drive. You have to change your BIOS to boot from USB How would I do that?

---

### Post by Pumalite on 2008-10-26
BIOS can be accessed easily hitting 'Del' or similar key at boot. There make USB bootable in first place, followed by CD and then primary hard drive

---

### Post by senor.ehlert on 2008-10-26
> **Pumalite said:**
> You can install to an external drive. Use your Live CD and at step 7; go to 'Advanced Tab' and change (hd0) for /dev/???, where ??? is your external drive ( find out with sudo fdisk -lu)
It's better than installing Grub on your internal drive.
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

I was considering installing to an external HD myself. So when you were refering to step 7, did you mean step 7 in the install?

And just to be certain, before I start changing things, you replace /dev/ with (hd0) then replace ??? with whatever shows up under "sudo fdisk -lu"?

And I am assuming you can easily partition the external HD?

Thanks, and sorry I hijacked your thread!

---

### Post by Pumalite on 2008-10-26
Step 7 of installation

---

### Post by a_washington on 2008-10-26
Thanks for all of your help!:) So if I install ubuntu on my USB HDD it WILL NOT erase Windows XP or make it unbootable. The reason I ask is because once when I installed ubuntu on my USB HDD drive it made both ubuntu and WinXP unbootable (even with the usb HDD disconnected). It said GRUB error 21. So if on step 7 I deselect GRUB it won't install GRUB? Do I understand you right?

---

### Post by Pumalite on 2008-10-26
You don't deselect Grub. You chage it for the device that corresponds to your USB drive.

---

### Post by a_washington on 2008-10-27
> **Pumalite said:**
> You don't deselect Grub. You chage it for the device that corresponds to your USB drive.

But what happened the last time I installed ubuntu is that even when the usb harddrive was UNPLUGGED the internal HDD still said GRUB error 21. And it should have booted Windows XP.

---

### Post by Pumalite on 2008-10-27
That's because after installing Grub to your internal drive; you didn't fix your Windows MBR. Use your installation CD to do it: hit 'r' for Recovery>FIXMBR>FIXBOOT
Or Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by a_washington on 2008-10-27
> **Pumalite said:**
> That's because after installing Grub to your internal drive; you didn't fix your Windows MBR. Use your installation CD to do it: hit 'r' for Recovery>FIXMBR>FIXBOOT
Or Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Windows came preloaded on my computer. So I don't have a Windows Install disk.

---

### Post by Pumalite on 2008-10-27
That's what Super Grub is for.

---

### Post by a_washington on 2008-10-27
What am I supposed to do with SuperGrub?:confused:

---

### Post by Pumalite on 2008-10-27
Read the documentation.

---

