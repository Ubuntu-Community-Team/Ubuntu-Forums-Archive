---
title: "Computer not booting after WUBI"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by jfb112697 on 2013-03-13
After I tried to install Ubuntu with WUBI on my HP Pavilion that came with Windows 8, I remembered that WUBI didn't work with UEFI boot systems. I got an error at the end of the WUBI installation, but I couldn't make any sense of it, and it didn't really seem important. After I restarted my computer just didn't boot. It doesn't try to load BIOS or anything, it just won't boot. At first I thought it was the monitor, but that I tried a different one and it still wouldn't boot. If anyone can help me figure this out it'd help a lot :) No it's not displaying any errors at all, I can't try to get into BIOS or the boot menu.

---

### Post by tejpatel98 on 2013-03-13
My computer had Windows 7 on it, but I upgraded to Windows 8 and used Wubi to dual-boot with Windows and Ubuntu. I had no errors or problems, but again I don't know if there is a difference between my upgraded Windows 8 from 7 and your Windows 8 that came pre-installed with the computer.

---

### Post by tejpatel98 on 2013-03-13
Another thing, if it won't even boot to the BIOS, have you tried unplugging the desktop from the power supply? :confused:

---

### Post by jfb112697 on 2013-03-14
Ahhh, found/fixed the problem. Windows 8 uses this awful feater called Secure Boot, which basically made it so I couldn't do anything on my computer once I dual-booted. For anyone else having this problem you can go about fixing it using these steps:
1: Turn off your computer/disconnect from the power supply
2: Disconnect your hard drive from the motherboard, you can keep it plugged into the power supply
3: Start up your computer, go into BIOS, depending on your manufacturer you'll find a setting called Secure Boot, disable it. For my HP the setting for Legacy Boot Sources was in the same places as the Secure Boot, enable those too.
4: Turn off your computer, plug your hard drive back in, and put the case back together.
5: Your computer should start up fine, I just installed Ubuntu 12.10 because of my Windows rage, especially with that sorry excuse for an operating system.

---

### Post by bcbc on 2013-03-15
This can't be normal. I think there's something wrong with your computer! There've been a lot of reports of the problem with Wubi and Windows 8 but never any mention of this sort of workaround required (and unplugging a hard drive from a motherboard is not exactly fun if you have a laptop). So likely you have some messed up firmware or something...

My 5c anyway.

Fortunately, now the [wubi download page]("http://www.ubuntu.com/download/desktop/windows-installer") specifically states that computers with a 'win 8' sticker (preloaded) or UEFI don't work with Wubi.

---

