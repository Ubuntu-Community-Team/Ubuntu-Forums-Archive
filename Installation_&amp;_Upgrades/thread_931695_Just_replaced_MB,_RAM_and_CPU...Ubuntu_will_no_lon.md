---
title: "Just replaced MB, RAM and CPU...Ubuntu will no longer boot"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by Zaragon on 2008-09-27
Hi  You've helped me before and I need help again.  I have a multi boot setup with Vista, XP, and Ubuntu 8.04.  I replaced the CPU, MB, and RAM.  I managed to get both Windows systems working but have not been able to get Ubuntu happening.  I have to problems:
1)  I downloaded a new Ubuntu image file.  I need to know what parameters to use to burn a new CD using Nero.
2)  Is there a graceful way to repair Ubuntu without flushing it and starting over?  Keep in mind that while I'm pretty adept in Windows stuff, I don't know my *** from a rock with Linux stuff yet.
Thanks to any who can offer help and advice.

---

### Post by Herman on 2008-09-27
> 2)  Is there a graceful way to repair Ubuntu without flushing it and starting over?
:)
Can you please describe what error message(s) you get or what happens, (what you see), when Ubuntu tries to boot?

If you have a recent version of Ubuntu, (Hardy Heron or later), it should boot up just fine all by itself almost no matter what hardware changes you made.

If you have plugged in your hard disks in a different order you might need to edit your /boot/grub/menu.lst file to get it to boot up. You should get yourself a copy of [Super Grub Disk]("http://www.supergrubdisk.org/"), that should be the easiest way to help you boot up initially. Then you can edit your GRUB menu to fix it if that's your problem.

If you need help with that, please post the output from 'sudo fdisk -lu', and a copy of the bottom half of your /boot/grub/menu.lst file so someone can see if it needs any corrections.
```
sudo fdisk -lu
``````
gksudo gedit /boot/grub/menu.lst
```Regards, Herman :)

---

### Post by Herman on 2008-09-27
> 1)  I downloaded a new Ubuntu image file.  I need to know what parameters to use to burn a new CD using Nero. I don't know anything about Nero because I've never used it, but the main thing to be aware of no matter what software you use for CD/DVD burning is that the file needs to burned as an .iso disk, and not as a data CD.

---

### Post by Zaragon on 2008-09-27
I did indeed plug hard drives in in a different order.  I just downloaded Super Grub Disk as you recommended and will give that a try.  Thanks

---

### Post by Herman on 2008-09-27
> I did indeed plug hard drives in in a different order. I just downloaded Super Grub Disk as you recommended and will give that a try. Thanks:) Okay then, your BIOS will automatically try to boot the MBR in whichever hard drive you have plugged in and jumpered as your first hard drive, which is number zero to GRUB.
You need to install GRUB to (hd0).

You should be able to do that with Super Grub Disk fairly easily.
You can do that either before or after you boot Ubuntu and edit your /boot/grub/menu.lst file, it doesn't really matter.

---

