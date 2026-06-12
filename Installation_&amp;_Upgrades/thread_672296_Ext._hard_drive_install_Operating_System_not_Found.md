---
title: "Ext. hard drive install: Operating System not Found"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by therealtigger on 2008-01-19
Ok, I was trying to install onto my external hard drive, with the desired outcome that I could turn on my laptop with the ext HD plugged in, and boot linux, but when it wasn't plugged in, it would boot straight to windows.

So, I burned a live cd, unplugged my internal drive, installed ubuntu+grub to the external drive, and booted back up (still without the internal drive plugged in). Everything loaded fine, I was happy. I plugged the internal drive in, and booted windows:perfect. However, now that I have both the internal and external plugged in, I can't boot either! I've tried disabling the internal drive in the BIOS as a quick fix to boot linux, but that doesn't make any difference. I can only boot linux with the internal unplugged, and I can only boot windows with the external unplugged. This is of course, hardly ideal.
(and no, I cannot install to the internal HD or anything like that, so please don't suggest it)

I'm sure I installed correctly, so what's going wrong?:confused:


Thanks for your help.

---

### Post by logos34 on 2008-01-19
So, with both drives plugged in, changing the Bios boot order has no effect?
On some bios menus you can choose the external drive in the **device boot order** (cdrom, **usb**, hard disk), on others you click on 'hard disk' and choose usb, or else go to a separate **hard disk boot priority** section.

---

### Post by therealtigger on 2008-01-19
The boot order is set up correctly (and I have tried choosing them directly as well).
I realized that I had disabled the internal drive when I was trying to boot with both in, which gave me the OS not found error. However, with it enabled (and the external plugged in) it boots straight to windows, so for some reason the comp is skipping past the external (which it of course doesnt do with the internal HD unplugged). I know that this sounds like the boot order is wrong, but I have checked several times to try and fix it. I will try it with the *wrong* boot order, maybe that will make it work :confused:


thanks for your help

---

