---
title: "devices fail to automount after upgrade: Solution"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Bloch on 2008-04-29
Some users report that flash memory devices fail to automount after the upgrade (not fresh installation) to 8.04 Hardy Heron

The issue relates to this bug in Gutsy: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)


Here is a solution:
Oeen the program configuration editor ALT+F2 and typing the command
gconf-editor

(as daengbo remarks below, it is not in the menu by default
Applications > System Tools > Configuration Editor might not exist)


In the gconf-editor window, go to the key 
system > storage > default_options > vfat
Edit the ```
mount_options
``` key (double click it) and remove the ```
usefree
``` option.

You may need to reboot.
The devices should then automount when plugged in: i.e. the icon will appear on the desktop.

I emailed one of the developers involved, Martin Pitt.
> That's indeed the right solution. 'usefree' is deprecated in Hardy (it
was only a temporary hack in Gutsy), and thus the gnome-mount
option 'usefree' has been removed in Hardy again.

You need it in Gutsy to avoid minute-long hangs when mounting a VFAT
drive. In Hardy this was fixed properly in the kernel.

If this key does not exist then clearly this solution does not apply to your problem.
Please add a post if it worked.

---

### Post by daengbo on 2008-04-29
Umm, the GConf Editor is not in the menu by default (for me, at least, and I'm an upgrader), so people will either need to add it to the menu using System > Preferences > Main Menu, use ALT-F2 to bring up a command prompt or start a terminal.

ALT-F2 and the terminal require this command:
> gconf-editor

---

### Post by lecter255 on 2008-05-09
> **Bloch said:**
> 

If this key does not exist then clearly this solution does not apply to your problem.
Please add a post if it worked.

yea i don't see the key in there, so no solution for me. do you have any idea why else might external hard drives not mount? i started the following thread to get help, please check it out.

[http://ubuntuforums.org/showthread.php?t=784970](http://ubuntuforums.org/showthread.php?t=784970)

---

### Post by radimatt on 2008-05-12
Yep, this solved it after a reboot.

Thanks!

---

### Post by Elaztic on 2008-05-25
Like Lector255 I don't have that in my gconf-editor either. As weird as that may sound....
The contents of my vfat key is:
shortname=mixed
uid=
utf8
umask=077
exec
flush

There is no usefree entry!

Any suggestions?

Since no one has responded to this I thought I'd add some more info:

dmesg | tail gives this after having plugged in my Kodak digicam:
usb 3-2: new full speed USB device using uhci_hcd and address 4
usb 3-2: configuration #1 chosen from 1 choice

lsusb gives this:
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 040a:057b Kodak Co. CX7430
Bus 003 Device 003: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000

Have tried to replace 'flush' with 'usefree' in the gconf-editor and reboot and even change it back with no difference.

From all the threads I have read I might be a 'legacy' problem from upgrading from Gutsy (I have just upgraded every time since Dapper!).
Is the solution to make a clean install or is there in fact a workaround?

Fixed!

Just upgraded to kernel 2.6.24.18 and now everything works again.
Don't think I have ever been more puzzled.
The upgrade to Hardy however killed the app (can't remember the name) that handled my digikam import by default.
After installing F-spot I got the import worked out even though it only copies and doesn't delete from the digicam. A little cumbersome but It'll do for now.

---

