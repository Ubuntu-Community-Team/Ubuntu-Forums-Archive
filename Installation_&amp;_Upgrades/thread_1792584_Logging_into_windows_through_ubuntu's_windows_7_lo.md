---
title: "Logging into windows through ubuntu's windows 7 loader"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-28
I have windows 7 on my C drive. I installed ubuntu 11.04 in a separate partition. Now, by default my computer boots into ubuntu. To log into windows there is a 'windows 7 loader' option inside the ubuntu logon screen. This is somewhat strange to me as so far my computer used to ask me to select the OS at bootup (that was with a wubi installation), and if i did nothing it woud boot into windows. Is booting into windows through the windows 7 loader ok? Or should i change the grub bootloader?

Also, I was quite surprised to find that ubuntu was able to "see" my C-drive and all its folders without me installing any separate software. How is it possible? (Windows 7 is not able to see the ubuntu partition. I know that it needs separate software)

---

### Post by lightstream on 2011-06-28
> **ktp.kti said:**
> Also, I was quite surprised to find that ubuntu was able to "see" my C-drive and all its folders without me installing any separate software. How is it possible? (Windows 7 is not able to see the ubuntu partition. I know that it needs separate software)

An open source driver (driver is probably not the right word strictly speaking) has been available that can read/write to disks formatted with Microsoft's NTFS for several years now.

Microsoft of course don't want to support non-Microsoft products if they can help it, so there's no native support for ext disks in Windows. You can however get an add-in for Windows that will allow reading of ext file systems (but writing is not usually available)

---

### Post by collisionystm on 2011-06-28
> **ktp.kti said:**
> I have windows 7 on my C drive. I installed ubuntu 11.04 in a separate partition. Now, by default my computer boots into ubuntu. To log into windows there is a 'windows 7 loader' option inside the ubuntu logon screen. This is somewhat strange to me as so far my computer used to ask me to select the OS at bootup (that was with a wubi installation), and if i did nothing it woud boot into windows. Is booting into windows through the windows 7 loader ok? Or should i change the grub bootloader?

Also, I was quite surprised to find that ubuntu was able to "see" my C-drive and all its folders without me installing any separate software. How is it possible? (Windows 7 is not able to see the ubuntu partition. I know that it needs separate software)


Yes, using the Windows 7 loader is okay. It is just the way GRUB labeled your windows partition. WUBI is different because it is using the Windows master boot record MBR to load, grub replaces that with a full install, such as the one you performed.

You can change your proffered OS using Startup-Manager. Its available in the Software Center. Just choose Windows 7 loader as default and then when you don't choose anything it will automatically boot to windows.

---

### Post by ktp.kti on 2011-06-28
> **collisionystm said:**
> You can change your proffered OS using Startup-Manager. Its available in the Software Center. Just choose Windows 7 loader as default and then when you don't choose anything it will automatically boot to windows.

Cool! It was so easy! Thanks collisionystm!(I am not very good at using the terminal)

By the way, Is there anyway to use windows MBR as default instead of grub?

---

### Post by collisionystm on 2011-06-28
> **ktp.kti said:**
> Cool! It was so easy! Thanks collisionystm!(I am not very good at using the terminal)

By the way, Is there anyway to use windows MBR as default instead of grub?


There may be... but I would not recommend trying it! It would take you a lot of effort to do it and you can easily break your system playing with boot records lol. Just keep grub.

---

