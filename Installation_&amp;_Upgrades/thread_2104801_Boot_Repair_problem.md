---
title: "Boot Repair problem"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by ben222qmz7 on 2013-01-14
Hello to all!

I am a complete beginner with Ubuntu and Linux.

I removed Ubuntu 12.04 (installed with a USB-stick) from my HP- lap top and then I had to use Boot Repair  to be able to start Winxppro again.

Now I wanted to install Ubuntu again, but the installation does not start at all but goes direct to Windows. I suppose BR changed something so that the computer cannot find the USB-HDD.

The BR-report:[http://paste2.org/p/2725842](http://paste2.org/p/2725842)

As I would like to test various versions again 
I would be very grateful for any help.

---

### Post by TheFu on 2013-01-14
Anytime you want to boot off something other than the first hard disk, you need to tell the BIOS the boot device and boot order.

Also, not all USB flash drives can boot from every USB port.  I'd setup a new Ubuntu installer using Yumi [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/).  This is what we use at my LUG for installfests.

I suspect all that boot-repair did was set the default timeout for booting Windows to 0 seconds. You could probably rerun BR and force the timeout to be longer, if you like.  Yumi really is a great solution for creating multi-boot USB flash drives, however.

---

### Post by ben222qmz7 on 2013-01-14
> **TheFu said:**
> 

I suspect all that boot-repair did was set the default timeout for booting Windows to 0 seconds. You could probably rerun BR and force the timeout to be longer, if you like.  Yumi really is a great solution for creating multi-boot USB flash drives, however.

Thanks fo your quick reply. Yes, I think  the timeout might be the problem.

As far as I remember correctly there was not any possibility to set any timeout adjustments when I used the program.

How can I find these settings?

---

### Post by TheFu on 2013-01-14
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) didn't help?

---

### Post by ben222qmz7 on 2013-01-14
> **TheFu said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) didn't help?

"Unhide boot menu : 10 seconds"

Does not seem to make any difference. Computer going to Windows
without any questions.

---

### Post by audunpoi on 2013-01-14
Do you have the option to go to a boot menu? On this machine I press F11 at boot and then I can choose which device to boot. Some usb sticks will boot this way but not if you just set the boot order in the BIOS without specifying which usb to boot. At least it's my experience.

---

### Post by darkod on 2013-01-14
Are you using the very same usb stick unchanged? Did you test if it can boot in another computer? Maybe the stick doesn't have a correct boot sector so even if it is first in the order, the bios will try it and then try the second device if the first has no boot sector.

Have you confirmed USB-HDD is before HDD in the boot options? Also, many computers have a boot menu usually accessed with F12 which is perfect for selecting a temporary boot device. You want to boot the stick only once, not always, so using a boot menu and selecting it is much better than changing bios options (but both ways should work in any case).

---

### Post by ben222qmz7 on 2013-01-14
The boot order is ok apparently as Boot Repair stick starts
as it should. With another stick with either Lubuntu or Ubuntu in it the start menu in computer stops and says: Disk error, press enter to start. Pressing any tab starts Windows and thus unable to start installing Linux.

I use the same iso data which worked perfectly earlier. Possibly the stick is defective although it is hard to beleive as this happens just at the same time when with the aid of another stick "The Boot Repair" repaired the grub.

---

### Post by YannBuntu on 2013-01-15
Hello

In case your Ubuntu stick to be defective, just try to install Ubuntu via another stick.
Eg use your Boot-Repair-Disk stick, and make it a Ubuntu-Secure stick (so that you can use it to both install Ubuntu and if needed use Boot-Repair).

> **TheFu said:**
> I suspect all that boot-repair did was set the default timeout for booting Windows to 0 seconds.

No it didn't. Look at line 100 of the log.

---

