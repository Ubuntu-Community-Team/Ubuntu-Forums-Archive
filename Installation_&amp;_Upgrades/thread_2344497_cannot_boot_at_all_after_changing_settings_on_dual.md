---
title: "cannot boot at all after changing settings on dual boot Dell"
date: 2016-11-25
forum: Installation &amp; Upgrades
---

### Post by jmorgan2047 on 2016-11-25
Hello,

It all started when the Windows 10 side of my dual boot machine (a Dell Inspiron laptop) did an update, and afterwards, from the Ubuntu side, I could no longer view the Windows system files. 
Previously I had enabled dual boot and viewing of the Windows system files from Ubuntu by making sure "fast startup" and secure boot were disabled (from the Windows side).
I also issued a mount command, only one time, from the Ubuntu side, to mount the Windows file system.  Everything worked great.  For months.  Until the most recent Windows update.
Instead of trying to issue a mount command again, I started mucking around with "BIOS" settings.  Now it's all muffed up.
At some point while trying different settings in the setup and "BIOS" menus, Windows hijacked the boot process, and I could not get the grub menu with the option to boot Ubuntu.
I treid all kinds of combinations of boot menu settings.  Then, in desperation, I "removed" the Windows boot option (via the setup/BIOS/F12 menu).   
Now it won't boot at all, it can't find any bootable devices.
I created a Ubuntu Live usb drive and installed boot-repair-disk on it, and was able to boot from/into that.  
I ran the boot-repair utility several times, but it's not working.  It says:
    "The boot of your PC is in Legacy mode.  Please change it to EFI mode.  Please use 
     Boot-Repar-Disk-64bit (...) which contains an EFI compat version of this software."

But this message makes no sense because the boot of my pc is not in Legacy Mode (per the visible menu settings), and I am using the 64-bit boot-repair-disk utility.
EDITED:  actually, in order to boot from the usb, I do have the "Enable Legacy Optopn ROM" enabled.
And since I amt running Ubu Live off USB, and the USB is FAT32 format, that could be a problem.  I did create the usb using the Yumi tool and I thought that was supposed to format it appropriately.
note: I also edited the pastebin url which had a typo in it: it was missing the / between the domain and the query string
END OF EDIT

I have also tried running sudo update-grub from a terminal in the Windows Live/usb session, but got this error: 
      /usr/sbin/grub-probe: error: failed to get canonical path of `/cow'. 

The uploaded bootinfo file is at [paste.ubuntu.com/23535052]("http://paste.ubuntu.com/23535052")

Any help would be so very appreciated. Thanks.

---

### Post by oldfred on 2016-11-26
Yes it looks like you deleted all you UEFI boot menu entries.
> BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
EFI in dmesg.
[    0.000000] ACPI: UEFI 00000000dbc15958 000042 (v01                 00000000      00000000)
SecureBoot maybe enabled.


And you booted Boot-Repair/live installer in BIOS/CSM/Legacy mode:
> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.


Best to turn UEFI secure boot off. May say Windows or "Other" where Windows is secure boot.
I think Dell is one where it seems to work better if legacy mode on, but you still want to boot USB flash drive & actual installs only in UEFI mode. Most systems with Legacy mode on, only boot in legacy mode.

If you use Boot-Repair to do a total reinstall of grub2 from advanced settings, that will add the ubuntu entries back into UEFI boot menu. But you need to be in UEFI mode on live installer for efibootmgr to work.

And you can use efibootmgr to add a Windows UEFI boot entry.
To see current entries as shown in Boot-Repair
sudo efibootmgr -v
 New Windows entry - assumes default sda1  add -p 2 if sda2:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 
For others if ESP not sda1, see this for extra drive & partition parameters
man efibootmgr

 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 

        Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
            [http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

