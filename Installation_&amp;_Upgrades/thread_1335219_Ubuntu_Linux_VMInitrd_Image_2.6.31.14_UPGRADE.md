---
title: "Ubuntu Linux VM/Initrd Image 2.6.31.14 UPGRADE"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2009-11-23
Hello,

I've just upgraded the Ubuntu's Linux Image from 2.6.31.14 to 2.6.31.15 and now I have four Ubuntu Entries:

Ubuntu 2.6.31.15
Ubuntu 2.6.31.15 (Recovery)
Ubuntu 2.6.31.14
Ubuntu 2.6.31.14 (Recovery

And there is also two Memtest options as well.

How can I remove the older Linux image? The newer one works just fine.

Thank you.

Edit: I checked Synaptic and the older linux image isn't there so is uninstalling it as simple as going into my /boot directory and deleting the 2.6.31.14 files?

---

### Post by pi4r0n on 2009-11-24
First of all backup your **menu.lst** file by doing

> sudo cp /boot/grub/menu.lst  /boot/grub/menu.backup

then edit this file by typing below command in terminal console

> sudo vi /boot/grub/menu.lst

You can either delete below entry or just comment it out.

> 
title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            75b2488b-37c6-469d-b474-7bff394ceaa6
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=75b2488b-37c6-469d-b4$
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            75b2488b-37c6-469d-b474-7bff394ceaa6
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=75b2488b-37c6-469d-b4$
initrd          /boot/initrd.img-2.6.31-14-generic


Cheers

pi4r0n

---

### Post by bumperchaser on 2009-11-26
I've just upgraded to 2.6.31.15 but it won't boot up.  It gets to the splash resolution test and just sits there flickering with a login line.
Any ideas? 2.6.31.14 still works so I'm using that at the moment.

---

### Post by bumperchaser on 2009-11-28
bump

---

