---
title: "Bootup Troubles"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Peder_Erickson on 2008-03-04
I just installed Ubuntu 7.10 on my mom's computer, and after the install, Windows XP won't boot!

I know that Windows is there, and she needs it to work, because she has some applications that require Internet Explorer, which doesn't come with WINE. :(

It appears in the GRUB Login manager, but if I choose Windows XP, it just hangs at the words "Starting Up..."  It also has the Windows XP recovery menu item, which does work, but I don't want to erase everything

Also Ubuntu is able to access the Windows partition.

Thanks for any help.

---

### Post by mikewhatever on 2008-03-05
Please post the following info:

- the output of <sudo fdisk -l>
- the output of cat /boot/grub/device.map
- the output of cat /boot/grub/menu.lst

---

### Post by Peder_Erickson on 2008-03-05
I think that I found out what went wrong, The installer got confused, and gave most of the HD to Ubuntu, instead of Windows.  Windows had system files past the half-way point of the HD, and they were probably erased when the partition was shrunk.  That would explain Windows being listed, and it not booting.  I probably will do a system restore, then re-install GRUB later

But she is happy that her machine is WORKING again.

She says that Linux is MUCH faster than Windows, and it hasn't even "Shaken" once.

:)

Wow just two laptops to go, then every machine that we use will be running Linux as the main OS
... But I have to wait for their copies of Windows to die first...:rolleyes:

also at this time, I'm at my college, so I don't have access to her machine, so I cannot do those commands.

---

