---
title: "Triple Boot Windows 7, Vista, Ubuntu 9.10"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by 93dan93 on 2009-12-10
I currently have Windows 7 (64 bit) and Vista in a working dual boot but now I want to add Ubuntu 9.10 into the equation.
I have a 320gb hard drive with (according to Palimpset Disk Utility):
Windows 7 on /dev/sda2
Windows Vista on /dev/sda3
Ubuntu 9.10 on /dev/sda5.

/dev/sda1 is a system reserved partition for Windows 7

When i startup my computer i am presented with 'GNU Grub version 1.97 beta4'
which gives me the options of:
Ubuntu, Linux 2.6.31-14-Generic
Ubuntu, Linux 2.6.31-14-Generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

I can load Ubuntu by choosing the first option but if I want Windows 7 or Vista I have to choose the last option (windows 7 (loader) (on /dev/sda1)) which takes me to 'Windows Boot Manager' which gives me the options of:
Windows 7
Windows Vista
Windows memory diagnostics


What I need help with is getting rid of the 'GNU Grub version 1.97 beta4' screen and adding an Ubuntu option to the 'Windows Boot Manager' screen.

I would really appreciate someones help.
Thankyou

---

### Post by cmcginty on 2009-12-10
Look at /boot/grub/menu.lst file for grub startup settings.

However, I don't believe that the Windows boot screen can start Linux. So you are better off staying with Grub and disabling the Windows menu.

---

### Post by 93dan93 on 2009-12-10
I had a look for that file but I couldn't find it.
I am pretty sure there is a way to have Ubuntu in the Windows boot manager because a while back I had a Windows vista, Mac osx, and Ubuntu 8.10 Triple boot running and I could load them all from the windows boot manager.
I think it might have something to do with this newer version of Ubuntu.(9.10)
I am still open to suggestions.
thanks

---

### Post by QIII on 2009-12-11
If you installed Karmic rather than upgrading, then you no longer have legacy GRUB, but GRUB2.  menu.lst no longer exists.

You will likely have to edit /etc/grub.d/40_custom -- back up your current copy first.

Then:
```
gksudo gedit /etc/grub.d/40_custom
```You will have to be careful about your devs/partitions, since they will surely be different from mine (I have three physical disks), but here is an example

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Vista" {
        set root=(hd1,1)
        chainloader +1
}

menuentry "OpenSolaris" {
        set root=(hd2,1)
        chainloader +1
}

```

Since you are already seeing the 7 entry, you may only need to add the Vista.  I can't help you with the Windows Memory Diagnostics bit.

When you are done, run

```
sudo update-grub2
```If that doesn't work, come back and we'll try something else.

---

### Post by 93dan93 on 2009-12-12
I haven't tried you solution yet but I will soon. But is there no way to hide the grub2 boot manager at startup and just have the windows boot manager with the Ubuntu option. I would prefer to have the windows boot manager rather than grub2 because grub2 isn't as easy edit as windows boot manager.

---

