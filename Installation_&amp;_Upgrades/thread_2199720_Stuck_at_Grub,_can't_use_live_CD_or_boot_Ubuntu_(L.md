---
title: "Stuck at Grub, can't use live CD or boot Ubuntu (Lenovo s440 dual boot)"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by samoos on 2014-01-15
I'm trying to set up a dual boot of Win 8 (preinstalled) and either Ubuntu or Ubuntu Studio on a Lenovo s440 haswell ultrabook (HD4400 and AMD HD 8670M graphics cards, 8GB RAM, 256GB SSD). 

I am currently unable to boot a Live CD USB (either the boot-repair .iso, gparted .iso, ubuntustudio or  ubuntu 64bit 13.10 .iso) - after selecting the USB in BIOS I'm left with a black screen. (i read a suggestion somewhere that in this situation I press Ctrl+Alt+F1 and then Alt+F6 to get the graphics to work(?) but no luck). 
I have also encountered the error message "the system is running in low-graphics mode" I didn't get very far following these instructions: [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error) - I either got 'fatal error: no screen detected' or 'usb 1-5: can't read configurations, error -71' (no device was plugged into any usb port)

I was able to install ubuntu, but not able to successfully reboot after install (booting into installed ubuntu from the BIOS goes to a grub page: "Minimal BASH-like line editing is supported...  grub>"). 


What I did to get here:

turned off secure boot and fast boot in the BIOS, and checked that it was set to UEFI boot. I defragged my windows drive, backed up my windows recovery, shrunk the windows partition, and tried an ubuntu live CD so I could run GParted. 
after live CD failed I decided to go ahead and try to install anyway. I got the message 'this computer currently has no detected operating systems' so when asked where/how to install I chose 'something else'. I made a 20GB and a 165GB ext4 partition and an 8GB swap (no idea if that is the right size/at all necessary). Installer finished and told me to reboot. I got stuck at the grub> screen.
then two big mistakes: after not finding a solution, I deleted the linux-swap, plus the two ext4 linux partitions from within windows. I tried re-installing Ubuntu although I guess the previous install had put grub on the /efi partition (?) so 90 percent through the installation I got an error message 'grub installation failed'.

Since then I've tried live booting/installing ubuntu studio, as well as live booting GParted and Boot-Repair with no success, and I don't know what else I can try.

Any suggestions?

---

### Post by ubfan1 on 2014-01-15
There's a "boot speed" setting in the UEFI Settings(BIOS) which should not be "fast", but the "fast boot" setting which needs to be turned off is in the Windows 8, Power Settings.  Did you try  nomodeset on the grub linux boot line to get by the graphics problems?  There are a variety of other things to try also, if that doesn't work.

---

### Post by samoos on 2014-01-15
thanks for both tips! I turned off fast boot in windows.

running the Boot-repair USB with nomodeset got me through to the splash screen, at least - but then I got an unending error:
unable to read config index 0 descriptor/start -71
hub 2-0: unable to enumerate USB device on port 5 
usb2-5: can't read configurations, error -71
(same result with UbuntuStudio live CD)

I don't know if I'm able to somehow add nomodeset to the boot options and reboot when I'm in the plain 'minimal bash-ike editing...' grub screen though, so I can't get any further booting the installed Ubuntu Studio.

---

### Post by oldfred on 2014-01-15
some other Lenovo


 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12

---

### Post by samoos on 2014-01-15
thank you for the links - it seems there are a few other people also with this strange usb error. 

I tried acpi_backlight=vendor and also rootdelay as some of the posts suggested, but got no further.
there was mention of turning off NIC in the BIOS? What does this do, should I do it and how?
Is it worthwhile trying to find out what usb 2-5 is? can I do so without a terminal?
As I can't even get to a command line in this situation, I basically can only adjust things in BIOS, Windows, Grub boot options (for Live CD) or the grub black screen (grub>) in the case of trying to boot the installed UbuntuStudio.

also, in BIOS Network Boot is set to PCI LAN - is that right?

still very lost unfortunately...

---

### Post by oldfred on 2014-01-15
You do not want network boot, in boot order it should be last.

Some have UEFI/BIOS setting for Intel NIC, but the controls Ethernet but may be related to USB issue? User that turned it off said wireless still worked, but Ethernet did not. And normally we suggest Ethernet hard wired connection as it is faster.

---

### Post by samoos on 2014-01-15
I just managed to boot into the ubuntustudio live CD! I guess next step is boot-repair, right?

---

### Post by oldfred on 2014-01-15
Boot-Repair is after you have installed. So it may suggest some fixes. With the very newest 13.10 or soon 12.04.4, Boot-Repair may not normally be required, currently most UEFI installs need some fixes.

---

### Post by samoos on 2014-01-15
so I should re-install UbuntuStudio from this Live CD?
 
I already installed it beforehand, but wasn't able to actually reboot into the installed OS (just got black grub screen instead), hence trying to boot a Live CD - I assumed I should use boot-repair in the live CD and that would repair grub and finally allow me to boot into the installed UbuntuStudio? or do I have things around the wrong way?

---

### Post by samoos on 2014-01-15
could be useful: [report from boot-repair]("http://paste.ubuntu.com/6759006/")

---

### Post by oldfred on 2014-01-15
I would not install signed verision. 
It does look like you ran the 'buggy' UEFI rename. If you can boot the ubuntu entry in UEFI menu, then you should undo the rename.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Install in sda6, looks incomplete. No grub nor kernels.

Black screen issue is past grub boot and into driver issues, most often video driver.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by samoos on 2014-01-15
Ok, the only thing that has changed now is that I can't boot Windows anymore. I still can't boot ubuntu Studio (the sda8 install) - it still goes straight to the basic grub> screen (not grub menu).

I can boot back to the live CD, but that is it.

yes, the sda6 vanilla ubuntu install is incomplete - that is where I had tried to delete the failed ubuntu install from windows so I could try to reinstall it (not a good idea, as it turns out).

if I install new drivers in the live CD will that allow me to then get past this grub screen and boot the installed version?

---

### Post by oldfred on 2014-01-15
With the 'buggy' UEFI file rename you can only boot grub. Both ubuntu entry & Windows entry in UEFI menu boot to grub and you have to boot Windows from grub menu.
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

From grub prompt does this work?


 configfile (hd0,gpt8)/boot/grub/grub.cfg

---

### Post by samoos on 2014-01-15
yes! 'configfile (hd0,gpt8)/boot/grub/grub.cfg' worked. thank you! also  after 'restore efi backups' I can now boot to windows too. 
to avoid inputting this configfile change each time I boot need to edit grub.cfg and insert it, right?
I will also go sort out the settings/drivers for video cards etc now.
thanks for all your help, marking this thread solved. :)

---

### Post by oldfred on 2014-01-16
There have been one or two cases where a grub.cfg had to be added to the efi partition with the configfile entry to call the real grub.cfg in the install. Not sure why. The install of grub to efi partition is supposed to add the correct info so it knows where to go.
If a grub update or other fixes do not work and you have to manually add the configfile, create a grub.cfg in the efi partition in the ubuntu folder and add just the one line configfile entry in that grub.cfg.

---

