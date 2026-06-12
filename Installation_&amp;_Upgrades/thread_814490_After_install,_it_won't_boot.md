---
title: "After install, it won't boot"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Kivamaki on 2008-05-31
I'm installing ubuntu onto a old HDD put into a external case, so its not USB.

I installed ubuntu to it, then it told me to reboot my system, then take out the cd, etc. I did so, and it comes to a black screen with a little line blinking like this: "-"

A guide told me to go into a rescue mode to make changes so the usb hdd will let ubuntu load, but i can't get into rescue mode. I hit exit at the CD menu to take me to "boot:" and I type in "rescue" but it just says "can't find kernel image: rescue" and every single command I use I get the same thing. 

Any idea what is going on?

---

### Post by Herman on 2008-05-31
> I'm installing ubuntu onto a old HDD put into a external case, so its not USB.:confused: Ignoring what kind of a box it's in for now, is the hard drive you installed Ubuntu in attached to the motherboard by an IDE ribbon cable, a SATA cable, a  cable that plugs in to a firewire port or a cable with a plug for connecting it to your motherboard via a USB port?

What kind of box it's in is irrelevant, and for booting purposes, whether it's a hard disk drive or a flash memory drive is also irrelevant too. What is relevant is how it is connected to your motherboard. :)

I'm only guessing, but I would think you probably have no boot loader installed in your computer's internal hard disk's MBR now. A zeroed MBR (zeroed in the bootstrap code area), produces the same symptoms as you just described.
If I'm correct, then the easiest way to fix it would be to get yourself a [Super Grub Disk]("http://www.supergrubdisk.org/")  and fix the boot of Windows in MBR, (assuming the main operating system inside your computer is Windows).
After that, use [Super Grub Disk]("http://www.supergrubdisk.org/")  to install the USB disk's GRUB to MBR in the USB and you'll be all set. :)

---

