---
title: "Unable to boot Windows after Ubuntu install"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by wadelius on 2015-11-07
Hi,


I've an Asus Ux303ln that  came with Windows 8.1. Immediately after buying the laptop I shrunk the  Windows partition, made sure it booted, and then created a repair USB  stick. After installing Ubuntu 14.10 Ubuntu booted, but Windows could  not boot. I've not really needed Windows until now. I've upgraded Ubuntu  to 15.04. 


The error message when booting Windows is:

The operating system couldn't be loaded because the HAL is missing or contains errors.

File: \Windows\system32\hal.dll

Error code: 0xc0000225


When  mounting the Windows drive in Ubuntu I can find the hal.dll file at the  specified location, so I think the bootloader can't find the correct  drive. 



I've tried the command prompt on the Windows repair stick, and tried things such as [FONT=monospace]bootrec /fixmbr[/FONT], [FONT=monospace]bootrec /fixboot[/FONT], [FONT=monospace]bcdboot[/FONT] (with arguments off-course).


[FONT=monospace]bootrec /scanos[/FONT] returns with 0 found Windows installations, the same result from [FONT=monospace]bootrec /rebuildbcd[/FONT].


There is no difference when I boot from Grub and from the BIOS (or whatever it's called now).


I  tried Ubuntu Boot-repair, and a couple of new Windows items appeared in  Grub, but none of them work except Ubuntu. The same error message as  before. The Boot-repair log is located at [http://paste.ubuntu.com/13142568/](http://paste.ubuntu.com/13142568/). 


Any help or pointers are appreciated!


Thanks in advance!

---

### Post by westie457 on 2015-11-07
Can you get into the 'one time boot' menu via the F12 key or whatever the manufacturer says in the manual.

Select Windows Boot Manager.

When Windows is running go into Control Panel > Power Options. Once here find 'Change settings not currently available', uncheck the box that has 'turn on faststart(recommended) next to it. Save changes and close out out of Control Panel.
Reboot to Ubuntu and in a terminal run ```
sudo update-grub
```
Reboot again and try Windows from the menu. Be careful, one of the entries might be for Windows Recovery.

Good luck.

---

### Post by wadelius on 2015-11-07
When I select Windows Boot Manager I end up with the same error message as when I try the Grub entries. So I'm not able to reach any settings regarding Fast start. The error message is presented by Windows, or at least the Windows bootloader.

Since even the recovery USB stick can't find the Windows partition I'm wondering what to do. I can access the partition without issues from Ubuntu.

---

### Post by oldfred on 2015-11-07
Back with Windows XP the hal.dll error was almost never hal.dll, but corruption in boot.ini.
But newer Windows do not use boot.ini, but /Boot/BCD, so I might think your BCD is corrupted.
That you can only fix from Windows, but do not know details.
Sometimes third party tools like EasyBCD may work when Windows own tools do not.

Grub only boots working Windows, so best to test by booting directly from UEFI or one time boot key.

You also showed a BIOS boot loader in the MBR. That will never work with your installs. Make sure you only boot in UEFI boot mode. 
Perhaps with Windows you tried to repair in BIOS mode?

---

