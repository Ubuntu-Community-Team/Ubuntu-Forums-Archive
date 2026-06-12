---
title: "Any Acer One Z1402 user here?"
date: 2016-12-23
forum: Installation &amp; Upgrades
---

### Post by edwankael on 2016-12-23
How did you guys install ubuntu on your Z1402? The UEFI situation are ridiculous.
The UEFI doesn't have "set supervisor password", or "add uefi as trusted" that kind of stuff.
It was able to boot from usb and finish the installation just fine, it's just that it won't boot into the installed ubuntu 16.04.

---

### Post by oldfred on 2016-12-23
Page 38 of your manual.
> Setting passwords
To set a password on boot, activate the BIOS utility, then select
Security from the categories listed on the left of the screen. Find
Password on boot: and use the touchscreen to enter a password
and enable this feature.

[https://www.acer.com/ac/en/ID/content/support-product/6200;-;Z1402](https://www.acer.com/ac/en/ID/content/support-product/6200;-;Z1402)

---

### Post by RobGoss on 2016-12-23
With Acer's it's much more complicated getting things installed and running the correct way, so on my all in one Acer after trying to add UEFI as trusted and was unable to do so

I just downloaded refined and with using a USB thumb drive I now have a few options to boot my multi system [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

This method worked best for me

---

### Post by edwankael on 2016-12-24
Well...that option is missing from the UEFI. There's only two options in it, Secure Boot, and Secure Boot mode, Which is weird.
We've tried there version of UEFI, 1.06, 1.07, and latest 1.10. No difference.

---

### Post by oldfred on 2016-12-24
Is this a 32 bit UEFI system?
They created those as then Linux did not have a 32 bit UEFI, so they thought they had a Windows only system. But later Linux released a 32 bit UEFI.

---

### Post by edwankael on 2016-12-25
How to check for that? I know my teclast X80h is using 32bit UEFI, but it does have custom efi to boot 64 bit linux distro on it.
Z1402 natively runs 64 bit windows 10 though...

---

### Post by oldfred on 2016-12-25
What cpu. If i3 like this system, then probably 64 bit.
[https://forums.linuxmint.com/viewtopic.php?t=208434](https://forums.linuxmint.com/viewtopic.php?t=208434)

If it only has 2GB of RAM, you may prefer Lubuntu, Xubuntu or 
 Ubuntu Mate.

---

### Post by edwankael on 2016-12-26
i3-5005u, 4GB of RAM, so probably 64 bit.
Update: Finally got into ubuntu for the first time ever. (Still not fixed)
Workaround is by using EasyUEFI and set it boot one-time for ubuntu. if not, boot order will be reset. Is there anyway to make it "persistent"? Would be a chore to set it everytime the pc startup.
My E5-574G has an i5-6200u, 12GB of RAM, love Xubuntu, it's super lightweight and usable imo. :)

---

### Post by oldfred on 2016-12-26
Once installed.
Some with difficult UEFI use rEFInd which is another boot manager.

But many just copy shimx64.efi to /EFI/Boot/bootx64.efi. And then boot a hard drive or fallback entry in UEFI, not the ubuntu entry.
Boot-Repair will make that copy if you use advanced options and check 'use the standard efi file'.
But it will not add a fallback UEFI boot entry. Some systems already have one.

Also more details in link in my signature below.
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by edwankael on 2016-12-27
So Acer replied..

[http://i.imgur.com/NqBhQLb.png](http://i.imgur.com/NqBhQLb.png)

I'll try later, my friend is still MIA.

---

