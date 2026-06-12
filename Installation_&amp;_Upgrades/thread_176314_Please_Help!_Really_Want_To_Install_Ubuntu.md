---
title: "Please Help! Really Want To Install Ubuntu"
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by ubnub2k6 on 2006-05-14
I want to install ubuntu on my laptop but the bios does not support booting from usb drive (cdrom). Updating bios is not an option. I can install win xp fine thru dos boot disk that has usb drivers, so I was hoping the same could be done with linux. Is there some sort of linux boot disk that will allow me to load my usb drive so I can install ubuntu? 

I have tried smb and other boot managers but they do not support usb booting if the bios doesnt either. Thats why I am hoping there is linux boot disk that has usb drivers to load a usb cd rom

I have a laptop toshiba portege 7200 cte w/ floppy drive.

---

### Post by louis_nichols on 2006-05-14
Are you sure the laptop doesn't support booting from cd? I thought so too at first, about my girlfriend's laptop, also a toshiba, but for a brief moment when starting, you can press f12 for bios menu or f2 for boot order. It's barely visible during boot, but it's possible. Try pressing these 2 keys after poweing on the pc.  Check that it's not coming out of suspend state, but really from shutdown.

---

### Post by ubnub2k6 on 2006-05-14
the bios does support booting from cd rom this however doesnt work for usb cd rom drives or at least i cant get it to work

---

### Post by Nonno Bassotto on 2006-05-14
I'm not sure I understand, so I ask you. Your Bios can boot from cd but not from an external usb cd drive, is this right? Is your standard cd drive broken?
How could you install Windows, then? Does XP have an option to reboot with usb drivers already loaded?

EDIT: I now realize you used a floppy,  sorry. Anyway this page might help you
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)
The author shows how to install some distros (ubuntu is among them) without cd's, floppys, dvd's or whatever else, only by network.

---

### Post by Sef on 2006-05-16
Read this:

[https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies?highlight=%28drive%29%7C%28hard%29%7C%28install%29]("https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies?highlight=%28drive%29%7C%28hard%29%7C%28install%29")

or this:

[https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28drive%29%7C%28hard%29%7C%28install%29]("https://wiki.ubuntu.com/Installation/HardDriveAndPcmcia?highlight=%28drive%29%7C%28hard%29%7C%28install%29")

---

### Post by ubnub2k6 on 2006-06-06
does anyone know if this hard drive install for ubuntu (from the link above) can be done by doing the setup thru windows instead of thru tomsrtbt linux because i have the ubuntu iso already on my hard drive but I dont know how to get the installer program to know where the iso image is. The installation starts up but I dont know what to do from the point where the installer is looking for the cd rom drive. (dont understand the whole /dev/.... stuff. How do I let it know to look on the hard drive partition that the iso is on.

---

### Post by bcw on 2006-08-26
This project allows you to install from a Windows disk:
[http://www.sourceforge.net/projects/instlux](http://www.sourceforge.net/projects/instlux)

I have just worked out a way to install from a USB CDROM if your system can boot from a diskette (but not a USB device).  I'm finishing the install to verify it all works, and then I'll post the details.

Edit: look at this posting:
[http://www.ubuntuforums.org/showthread.php?t=244918]("http://www.ubuntuforums.org/showthread.php?t=244918")

---

