---
title: "Ubuntu Dual-Boot w/Windows 10, not loading after installation."
date: 2019-04-01
forum: Installation &amp; Upgrades
---

### Post by coreyd2 on 2019-04-01
Apologies if I do not give enough details with my issue, i've never played around with Ubuntu before.

First of all, through many failed attempts, i was unable to get the Ubuntu installer to detect that windows was already installed.
Eventually i gave up on trying to get this to work, so i created my own partitions (Swap, EFI and Boot) and ran the installer through the 'something else' option.
Everything installed correctly after about 10 minutes and then it asked to restart the PC, after doing so however i have been unable to access Ubuntu at all, i've played around with boot options but haven't found any other solutions to try and fix this.

Windows 10 is 64-bit, as is Ubuntu. I installed Ubuntu through a USB drive, and the BIOS is MSI which is running in 'LEGACY+BIOS' mode in the boot settings. If you need any other details just let me know as i'm not too sure what else to say.

Thanks

---

### Post by oldfred on 2019-04-01
If Windows installed by vendor then it will be UEFI, not legacy.
And then motherboard should not be in Legacy boot mode.
If you added an ESP - efi system partition, then you also installed Ubuntu in UEFI boot mode.

Or did you install Windows yourself and install in Legacy mode? 
UEFI & BIOS boot modes are not compatible.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coreyd2 on 2019-04-07
Ohhh okay. Using the EFI Partition was the only way that i found on the internet which seemed to install for me. 
I had this PC custom built so i installed windows myself, my BIOS says Legacy, so how would i go about installing Linux through Legacy rather than UEFI? 


If that does not work then i will use the Boot-repair to get you a report to look at.

---

### Post by oldfred on 2019-04-07
How you boot install media UEFI or BIOS from your UEFI boot menu is then how it installs for both Windows & Ubuntu.
Often the legacy/UEFI setting in UEFI, does not change the option in booting a flash drive. Only if UEFI Secure boot is on, then usually booting of any other media is turned off (as not secure), but then there may be another setting to allow USB boot.

In UEFI boot menu you should normally have two boot options, one UEFI "flash" and other "flash" (usually dose not say BIOS/Legacy/CSM) where "flash" will be the name or label of your flash drive. My system shows all my flash drives as pmap. Not sure if that is brand or what as most are Microcenter house brand.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by yancek on 2019-04-07
Take a look at the link below which is the Ubuntu documentation on dual booting with windows.  Also explains what you should see (different screen image) when booting UEFI or Legacy.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

