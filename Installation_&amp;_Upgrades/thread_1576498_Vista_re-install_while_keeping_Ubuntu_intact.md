---
title: "Vista re-install while keeping Ubuntu intact"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by svikas on 2010-09-17
Hi,

I have a Dell studio 1555 with Grub bootloader and Vista and Ubuntu. From last 2 days, display is coming blank in Vista after clicking on login name. Display comes file in Vista boot DVD and also in Ubuntu. Since I don't have a restore point, Dell support is asking to re-install Vista.

So, I need to re-install Vista and keep existing data in Vista and Ubuntu intact. Could you please provide useful tips or point to some link.

Thanks in advance,
Vikas

---

### Post by uRock on 2010-09-17
I'd recommend using ubuntu to back up your data first. Unless you have your Windows data on a separate partition from the Vista OS you won't be able to save the data in that partition.

After reinstalling Vista you will have to reinstall the grub boot loader in order to boot ubuntu. [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Rubi1200 on 2010-09-17
If you reinstall Vista it will overwrite the Ubuntu bootloader. This is okay, because all you have to do afterwards is reinstall GRUB and you will then have the option to boot both operating systems again.

Here is a guide:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

The first method is the easiest and works in almost all cases.

If you have any questions, feel free to ask.

---

