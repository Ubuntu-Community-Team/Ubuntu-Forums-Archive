---
title: "Help with USB install for a IBM T41 laptop"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by construxboy on 2007-12-27
Hi guys, 

I have a work laptop (IBM T41) that I don't have admin rights on that has some internet sites blocked that I want to use when I travel, like personal email and EBay. So I wanted to boot the laptop to ubuntu to be able to access these sites. I have a LiveCD of Fawn and that has worked so far. 
However, now I see two downsides:
1) Booting from the CD is pretty slow
2) Can't save files on the boot, like Firefox favorites or new programs

So I am trying to install a persistent Fawn boot through a 1 GB pen drive. 
I followed the directions on [http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/")
here and it worked fine up until the use on the T41. I checked the BIOS and see that USB is Enabled and again, the LiveCD works fine. What happens when I boot is that the screen goes blank for about 2 minutes, as though it is starting to read the USB drive (which is lit) and then it jumps back into the normal Windows XP Pro boot. 

I heard something about a bootloader here. (GRUB?). Do I need that? Where would it go in the sequence of the steps I use on the page linked above?

Also, I'm using Fawn because it looked like the latest persistent install, but are some of the later releases also available in persistent mode for a pen drive?

Thanks for any and all help!

---

### Post by construxboy on 2007-12-27
OK as an update I did the pendrive all over, this time using Gusty and following the instructions on the LiveUsbPendrivePersistent Wiki page. Same result. LiveCD works fine. Pendrive gives blank screen for two minutes before going to XP start. 
Any ideas? Is there any reason that a LiveCD would work on a laptop, but not the Pendrive related to the computer? The BIOS setting I see doesn't have the USB drive listed. Can I add a listing in the boot sequence for that?

---

