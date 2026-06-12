---
title: "Will I mess up the ubuntu install if I move my HDD to a different SATA slot?"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by JonathanWest on 2011-10-08
I currently have a single HDD on my laptop in the first SATA slot. This has a dual boot Windows/Ubuntu 11.04 setup.

My laptop has two SATA slots internally.

I am buying an SSD, and received wisdom seems to indicate it is best placed in slot 1 (it will be my default boot device for Win 7). So if I do that (put it in slot 1 and move the HDD to slot 2) and then install Win 7 onto the SSD, I know I will need to repair my grub2 boot loader - but will I need to reinstall ubuntu or otherwise fix it (e.g. will the sda(x) change from 1 to 2 and hence send the device mappings screwy?)

---

### Post by Basher101 on 2011-10-08
I could only see an issue in Windows 7 on your HDD...otherwise Ubuntu always rescans on every boot the hardware to check for any new/changed hardware and it then applies the appropriate drivers. I know this works since i put my Ubuntu install on a USB stick, made it bootable and put it into a computer at my school. Everything worked like a charm.

Your GRUB on your HDD could get some errors when changing the slots, because the UUID could change with the change from /dev/sd[COLOR="Red"]**a**[/COLOR] to /dev/sd**[COLOR="Red"]b[/COLOR]**. But as far as i can tell, they rank up like this: on 1. are hard disks, on 2. USB drives (sticks and external drives the same) and 3. come discs. I have no idea how two hard disks will be labeled as, or the criteria for that (e.g. the one in slot 1 being /dev/sda and the one in slot 2 /dev/sdb or the other way around). So in short, just swap it and see if ubuntu boots without issues. If it does you at least know where to ask how to fix it *hint hint* ;]

---

### Post by JonathanWest on 2011-10-08
Thanks for that information about the rescan on boot. As I will be doing a Grub restore/repair after the Win 7 install on the SSD anyway, that should clean up the Grub references.

---

### Post by Basher101 on 2011-10-08
after you do that i do not see any issue on that then. Also, since you will have 2 hard disks (with windows on the SSD and Ubuntu on the HDD?), the bootloaders wont overwrite then. You can reinstall Ubuntu and Windows as many times as you like without breaking either bootloader (you will have to change the bootorder in BIOS to get access to ubuntu after reinstalling Windows then and reconfigure GRUB so it can see your Windows).

---

