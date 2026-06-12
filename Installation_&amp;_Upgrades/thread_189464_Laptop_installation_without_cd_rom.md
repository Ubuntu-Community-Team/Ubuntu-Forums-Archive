---
title: "Laptop installation without cd rom"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by JamesB on 2006-06-05
I have an old laptop (P111 192meg ram) where the cd rom is broke. Can I take the hard drive out and put in another machine and install and then put the hard drive back in the original machine. Would this work? Or is there another way of getting ubuntu on to this machine?

---

### Post by pellgarlic on 2006-06-05
hi jamesb - i would advise against moving the drive into another machine to install ubuntu - during the install process, ubuntu looks for the installed hardware, and sets it up, including writing the fstab, which tells ubuntu where to find the hard drives, optical drives, floppy drives and so on. it also sets up different modules to load automatically depending on the available hardware. for this reason, if you move the hardrive into another computer, and install it there, it will not be prepared for the hardware in your laptop. 

it would be possible to make the necessary changes to the fstab file, and figure out what modules were needed/desired and make the relevant entries in config files to have them run automatically, but there may be an easier solution, if you have access to another computer with a cd drive, and you also have a (1 gb or larger) usb flash drive, and assuming the laptop has a usb port, and that you can boot from the usb port (if any of these requirements are not met, this will not be of any use to you, but it is the only alternative i can think of to get around your broken cd-rom).

this site: [http://www.usbuntu.com/](http://www.usbuntu.com/) has instructions for "installing" the ubuntu live cd onto a flash drive. NOTE: this is not a "real" installation, as the live cd's structure is kept, so that each time ubuntu is run from it, it searches for the available hardware, and loads the relevant modules, and also writes a relevant fstab (temporarily - for the length of the "live" session). with the new "dapper" desktop cd, the "live" and "install" functions are integrated into one disc, so putting this onto the flash drive, and booting from it would allow you to install ubuntu from it.

[edit]: actually, if the laptop has usb ports which you can boot from, you  could also try to "acquire" a usb cdrom on a temporary basis, and just use the ubunut cd that way? or you could just bite the bullet and replace the cdrom! :D

---

### Post by CyberX on 2006-06-05
Hello.
Yes you can. In fact, that was precisely the way I managed to install Breezer and Dapper on my Toshiba Portege 7010CT,since I don't have the external CD-ROM:

I took the disk off, put it in a desktop computer (with a IDE to mini IDE cable adaptor) as Primary IDE Master, booted from Dapper Desktop CD and when the installer asked to remve the CD and reboot, I put the disk back in the laptop.

Just two warnings:
- Dapper doesn't like my Toshiba so I have to manually edit Grub and put 'acpi=off' at the end of the second line (but Breezy works fine). After login I edit /boot/grub/menu.lst so I don't have to do it again at every boot.
- Since the Graphic Card is not the same, when Dapper tries to start X it fails, so I have to login in text mode and 'sudo dpkg-reconfgure xserver-xorg' to reconfigure it, then 'sudo starx' or reboot.

By the way... my laptop is a Pentium II @ 300 MHz with 160 MB of memory. After some performance tweaks, it is enough for my needs... but I think that your Pentium 111 (is it really 111 MHz?) will be very slow in X, even if you change GNOME with Xfce Icewm or Blackbox.

---

### Post by JamesB on 2006-06-05
Hi 
Thanx for the info. The laptop is a P3 700mhz and doesn't have boot from usb facility... I'll try the 'install in different computer' and report back with the results... maybe useful for others etc...

---

### Post by dmizer on 2006-06-07
be careful with the boot partition on that kind of install.  you could mess up your host system's mbr if you're not careful.

also, installing on a host is no problem.  i would suggest doing a server only install though.  then replacing the drive into the laptop before installing ubuntu desktop.  that way you don't have hardware detection problems.

let us know how it goes.

---

### Post by pellgarlic on 2006-06-10
while browsing generally, i came across this page, and remembered your quandary. i guess you're going down the "move the hard drive into another machine" route, but i thought this was interesting enough to warrant a mention anyway. it involves installing linux (with specific details of several different distributions, including ubuntu) purely via the internet - i.e. no need to burn cds, or use usb devices - direct install over the internet, from an existing windows installation. it can be found here:

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by bl@ckm@ge987 on 2006-06-17
I've done that with ubuntu 5.10 and my Toshiba 7010CT. Hooked it to my old comp, installed ubuntu, after it restarts during setup, put the HD back in my Toshiba, boot-it, and I had to wait 4 hours for something called "laptop detect", and aside from no sound and 640x480, its good.

---

### Post by pellgarlic on 2006-06-17
[QUOTE=bl@ckm@ge987]and aside from no sound and 640x480, its good.[/QUOTE]

you could try doing this:

```
sudo dpkg-reconfigure phigh xserver-org
```

if that doesn't work, try it without the "phigh":

```
sudo dpkg-reconfigure xserver-org
```

it will ask you some questions about display, keyboard, mouse etc. i did this when i was messing about with stuff, and lost my 1280x1024 resolution - got stuck at max of 1024x768. doing the above got it back.

(i think for both of these, you need to restart X - do a ctrl-alt-bkspc)

these are the kind of issues i mentioned in my previous post - ubuntu will be expecting to find the same hardware that was there when you installed it. it seems to be  flexible to a certain extent, but it should still function. there are  most likely ways to fix these things, but i'm not savvy enough to suggest any more than the one above for display problem. even then that might not fix it... 

i guess using a computer with as similar a list of specs to your destination computer as possible for your "host" installation would cut down the number of issues as well.

---

### Post by Etoile on 2006-06-18
Perhaps one of these would help?
[Advanced Installation Methods](https://wiki.ubuntu.com/Installation#head-ea0039061a9c639249330e80e8369cfe32d99805)

---

### Post by thumpa007 on 2006-06-18
If your old laptop boots windows then install grub for windows and do a net install (see link in Etoile's post). I've just done this on my laptop, let me know if you need more info.

---

