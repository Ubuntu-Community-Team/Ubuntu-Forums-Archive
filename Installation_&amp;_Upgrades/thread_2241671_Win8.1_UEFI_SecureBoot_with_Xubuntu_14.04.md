---
title: "Win8.1 UEFI SecureBoot with Xubuntu 14.04"
date: 2014-08-27
forum: Installation &amp; Upgrades
---

### Post by info-web-ridge on 2014-08-27
[http://paste.ubuntu.com/8142366/](http://paste.ubuntu.com/8142366/)

So, a new £800 laptop (HP - ENVY 17-J184na 17.3"). Have followed:

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

But even better is this:

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

But still no dice. I have yet to try renaming the windows EFI file and renaming the xubuntu EFI file to the windows one to try and trick the firmware to boot to GRUB.

Has anyone had success with this?

P.S. I have nothing to lose as my current Asus G71v xubuntu 13.04 is still running, albiet the power button doesnt work as well as it should...

---

### Post by ubfan1 on 2014-08-27
I think HPs require the rename, you can do it yourself (they are just files), or use boot-repair.

---

### Post by info-web-ridge on 2014-08-28
Ok, so I tried the boot-repair's automatic renaming of EFI files and it still didnt work. I tried this procedure both with SecureBoot on and off.

I also tried Rod's refind unitilty and the lappy still booted straight to windows. Nothing seems to shift HP's custom firmware mod. I looked at the BIOS and the "reset to default settings" option is greyed out.

[http://paste.ubuntu.com/8170717/](http://paste.ubuntu.com/8170717/)

---

### Post by JMB74 on 2014-08-28
Manual rename?

Is this info for a similar laptop helpful?

[http://ubuntuforums.org/showthread.php?t=2211913](http://ubuntuforums.org/showthread.php?t=2211913)

---

### Post by info-web-ridge on 2014-08-29
Yes it's a similar lappy, mine is an HP Envy 17-j168ea. The steps are what ive carried out aready though, so nothing new there. I will try the manual rename. Refind installed and gives me its selection menu but I think that'll confuse the issue

EDIT: Didnt do the manual rename, Just tried the boot-repair (recommended) again with secure boot disabled, on the installed 14.04. I didnt restart but shutdown after boot-repair ran. [http://paste.ubuntu.com/8180282/](http://paste.ubuntu.com/8180282/)

Switching the Laptop on and I got the GRUB menu! So i made sure it worked booting into xubuntu, and booting into window, and back again into xubuntu. There was an entry called system settings, which also tried, it booted into the bios selection (F9, boot menu, F10 system settings). I pressed enter to continue booting and Win 8.1 loaded and thereafter, GRUB was lost again, each reboot went straight to Win.

So i have a new problem of the changes not being persistent through reboots

---

### Post by ubfan1 on 2014-08-29
Boot order changes are sadly all too common -- can't even blame it all on Windows either, so I just use the efi boot menu to select the OS I want to boot.

---

### Post by info-web-ridge on 2014-08-30
Yes, I think that is going to be my choice, rather than spend more days trying to work it out. Thank you all.

EDIT: This might help someone struggling to get an HP UEFI Laptop (ENVY or otherwise) to dual boot with *buntu:

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/m-p/3384985#M172240](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and-Software/Changing-Boot-Order-on-Dual-Boot-Windows-8-and-Ubuntu/m-p/3384985#M172240)

The above link helped me to get grub to start when either rebooting or powering up. I can get to xubuntu or Win8.1 with no bother. What it hasnt done yet is allow me to go into BIOS without that defaulting everything back to HP's factory settings - hopefully I dont have to go there that often.You were correct ubfan1, it was a boot order that was constantly changing

---

