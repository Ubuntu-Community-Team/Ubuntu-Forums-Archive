---
title: "Newbie: Grab Error15 on usb HD"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by darkskyitaly on 2008-03-03
Hello forum,
i'm a newbie that's trying to install Ubuntu 7.10 on a USB HD.
My pc's got 2 hd SATA in raid 1 where xp has been installed.

I've added an EXTERNAL usb HD and i've installed ubuntu on it.
When i start the pc from the external hd, i receive only a message such as "grub error 15".
I don't know how to fix it, i'm worried about the possibility of destroy the Xp boot loader or so on..
Please, help me... 

I have to remember you that i'm a really newbie on the fantastic linux'world, so please... be clear! :)

---

### Post by logos34 on 2008-03-03
Set the usb drive as first in the hard disk boot priority.  Then set the device boot order to cdrom first and boot from the live cd to access and edit your grub config files on the usb.

Accessories>terminal
**gksudo nautilus**
(opens file browser as root)

Click on root partition in side pane to mount (should do so at '/media/disk')

GO to /boot/grub folder and open menu.lst

Change 'groot' and root lines to (hd**0**,x).

Reason: as soon as you change the Bios boot order to boot from the usb, it becomes '(hd0)'

Rewrite grub to the mbr of the usb drive.

(from terminal):

> sudo grub

> find /boot/grub/menu.lst
(enter in next command)
> root (hdx,y)
> setup (hdx)
> quit

---

