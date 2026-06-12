---
title: "stil hotkeys issues on Asus eeePC1005P"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by bripa on 2010-07-27
Hi,

New to Linux,  I need support. I have the hotkeys and above all brightness issue aftre first installation.

the ubuntu support website say: 
"Brightness control doesn't work properly. Pressing Fn-F5 or Fn-F6 changes the brightness randomly.
To get best support for hotkeys, update your BIOS to the latest version then add some kernel parameters to the grub config. Run sudo gedit /etc/default/grub
Edit the line with GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux acpi_backlight=vendor". The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
Save and then run sudo update-grub
Reboot
xbacklight, and xgamma work too.."

I did all the procedure without success. My bios is versio 0901. As the ASUS website discourage to update the bios, do I really need to update it to solve brightness control?

Additional question: when doing grub update, I get the message that GRUB_CMDLINE_LINUX was not found. What should be the correct value? 

Thanx for your reply
Paolo

---

### Post by bripa on 2010-07-29
Hi all,

Is there anyone that can help me?
Is my request not sufficiently clear?

Thanks

---

### Post by LunaticHiatus on 2010-07-29
It seems like its not really a fix but just a way of patching up the problem probably caused by lack of driver support via asus' side which might be fixed with a kernel update anyway.

You can just put a screen brightness applet on one of your taskbars as well without having to fiddle with command line if your concerned about screen brightness. I'm not what sure what trouble your having with grub though. Sorry I couldnt be of more help

---

### Post by bripa on 2010-08-17
Thanks for your reply.
Indeed I think the problem is in the GRUB_CMDLINE_LINUX value. 
When doing update -grub i get a error message for that value, which seems to be missed. 
 
Do you know which is the correct value for GRUB_CMDLINE_LINUX?
 
Thanks in advance
Paolo

---

