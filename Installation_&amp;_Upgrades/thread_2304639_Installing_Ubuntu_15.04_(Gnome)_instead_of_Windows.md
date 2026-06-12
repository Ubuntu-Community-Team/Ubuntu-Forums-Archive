---
title: "Installing Ubuntu 15.04 (Gnome) instead of Windows 10"
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by lukas27 on 2015-11-28
Hello,
I've tried install in last few days Ubuntu instead of Windows 10 so many times, but my notebook couldn't boot usb with ubuntu, not even DVD with ubuntu. I've tried disable fast/secure boot in BIOS, but still it doesn't work. Please, can someone help me?
My notebook: HP 15 r164nc
Thanks a lot for any advices!

---

### Post by Melnik_Hoogland on 2015-11-28
You probably need to change the boot order in your BIOS. You should also make sure Fast Startup is disabled. In Windows 10, go to Power Options in the Control Panel, click on "Choose what the power buttons do" at the left, click "Change settings that are currently unavailable", then make sure "Turn on fast startup" (near the bottom) is unchecked.
Now shut down your computer and make sure your ubuntu USB is plugged in. While you turn on your computer, keep pressing F12 (as if you're trying to enter the BIOS and F12 is the key to enter the BIOS). If a boot menu appears, navigate to your USB stick using the arrow keys and press enter. It should boot from the USB.
If that doesn't work, you'll need to change the boot order in your BIOS. Enter your BIOS, navigate to a section named "Boot" or "Startup" or something similar, then move "USB HDD" to the top and save and exit. Your computer should now boot from the USB.

---

### Post by oldfred on 2015-11-29
If you are installing Ubuntu only on a HP in UEFI boot mode, you need to change description of boot entry from ubuntu to Windows.

HP violates UEFI spec that says you should not use description as part of boot. But HP and many others have added description as part of UEFI boot and only description allowed is Windows.
There are several work arounds, some better if dual booting or if only Ubuntu.

       
 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Some other work arounds used by HP users:
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Or you can just install in BIOS/CSM/Legacy boot mode, but gpt & UEFI offer some advantages.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Some more details in link below in my signature.

---

### Post by lukas27 on 2015-11-30
**Melnik_Hoogland:**
obviously, I have USB on first place in bios, but anyway doesn't work.. I can't even see in bootmenu usb flashdisk with ubuntu.. And fast start-up I have turned off as well.
**oldfred:**
Unfortunately, anything doesn't work.. Btw, how can I change UEFI description, when I can't even try ubuntu without install(like is in ubuntu menu before instalation)? Because my ntb can't see my usb flashdisk in bootmenu, as I said before.

---

### Post by oldfred on 2015-11-30
You do need to boot Ubuntu installer in UEFI mode and use efibootmgr.

Your UEFI should show flash drive if flash drive correctly configured as a bootable UEFI device. And most show flash drive twice, once UEFI:flash drive label and then just by flash drive label or BIOS.

If you have secure boot on, your system may not allow USB boot or anything as that is not "secure". Make sure in UEFI you have secure boot off. Some UEFI also require separate USB settings to allow boot whether secure boot is on or not.

Did you review the other HP users. UEFI is often very similar across models, by vendor. And those users may have posted some details you need.

---

### Post by lukas27 on 2015-11-30
> **oldfred said:**
> You do need to boot Ubuntu installer in UEFI mode and use efibootmgr.

Your UEFI should show flash drive if flash drive correctly configured as a bootable UEFI device. And most show flash drive twice, once UEFI:flash drive label and then just by flash drive label or BIOS.

If you have secure boot on, your system may not allow USB boot or anything as that is not "secure". Make sure in UEFI you have secure boot off. Some UEFI also require separate USB settings to allow boot whether secure boot is on or not.

Did you review the other HP users. UEFI is often very similar across models, by vendor. And those users may have posted some details you need.
Secure boot should be disabled - [http://i.imgur.com/EqXTsrj.jpg](http://i.imgur.com/EqXTsrj.jpg) - my boot settings in BIOS. And still the same..

---

### Post by oldfred on 2015-11-30
What is inside the OS boot manager entry in UEFI.

If you want to boot in BIOS mode you have to turn on the legacy boot setting at the top. It shows disabled.

---

