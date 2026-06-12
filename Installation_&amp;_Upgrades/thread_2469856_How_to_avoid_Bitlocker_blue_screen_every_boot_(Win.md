---
title: "How to avoid Bitlocker blue screen every boot (Win11-Ubuntu dual boot)?"
date: 2021-12-11
forum: Installation &amp; Upgrades
---

### Post by anon847 on 2021-12-11
Every time I boot up lately, it defaults to Win11 and goes directly into the blue Bitlocker screen asking for me to decrypt using the key. In order to access Ubuntu right now, I "skip" Bitlocker and restart using the advanced reboot options, then access the UEFI boot menu. This allows me to access the UEFI folder menu and after about 3 menu selections can get to GRUB.

The thing is, I believe I installed Ubuntu alongside Windows 11 correctly, and keys were assigned to the Ubuntu install. Also, for several days it would boot directly into GRUB. Now, the only way I've found to access GRUB/Ubuntu is to use the steps above.

How can make GRUB the default secure boot, UEFI boot option? Is it possible to have Windows bootloader integrated into GRUB like in the past, or is that gone now with secure boot/dual boot with Win11?

Should I change TPM settings in BIOS?

---

### Post by tea for one on 2021-12-11
> **anon847 said:**
>  Also, for several days it would boot directly into GRUB.
Windows 11 Update turned on hibernation?

---

### Post by anon847 on 2021-12-11
Hibernation was enabled by default. I had already disabled fast-boot--no effect. Did try disabling hibernation and retrying, but no luck.

I've tried installing boot-repair, but apparently it's not available for v21.10, Impish Indri.

---

### Post by anon847 on 2021-12-11
This seemed to fix it: 
[COLOR=#232629][FONT=ui-monospace]update-grub 
[/FONT][/COLOR][COLOR=#232629][FONT=ui-monospace]grub-install

[/FONT][/COLOR]But I suspect that if/when I boot back into Win11 (I avoid using windows at all costs), it may revert back to the previous issue.

I do wonder if using the bcdedit cmd from within Windows might allow me to fix it for good. ([https://superuser.com/questions/1247300/how-to-make-uefi-bios-start-grub-not-windows](https://superuser.com/questions/1247300/how-to-make-uefi-bios-start-grub-not-windows))

---

### Post by westie457 on 2021-12-11
Hi, my 2 cents worth.

Re-enable Secure Boot in the UEFI Settings.
Boot into Windows and disable Bitlocker or completely remove it. [https://uit.stanford.edu/service/encryption/wholedisk/bitlocker](https://uit.stanford.edu/service/encryption/wholedisk/bitlocker)
Double check that Fast Startup has not been re-enabled.
Power off the computer - not a restart.
Power on, you should get the Grub menu. Windows should now start properly.

---

### Post by yancek on 2021-12-12
I have windows 10 so I'm not sure if all will be the same with 11.  Some but not all, windows updates will turn hibernation back on and enable Secure Boot if it is set to disabled so you need to check these after each update.  These updates may also change the boot option setting in the BIOS firmware, setting windows first.  On my HP laptop, if I turn off/disable TPM, windows 10 won't boot but my Linux systems will.

You can use sudo efibootmgr -v to get information on boot files in the BIOS firmware such as the order to boot, first to boot,  etc.

---

