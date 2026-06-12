---
title: "Secure Boot UEFI and GRUB"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by Wrkcncanter on 2020-07-03
Hello,
I have a Surface Pro 4, with an Ubuntu installation that has gone mostly unused for several years. I have secure boot off, and boot into grub, then into Windows most of the time.

Lately I've upgraded Ubuntu, and would like to switch Secure Boot back on in UEFI settings, to get rid of the red bar across the top. (I forgot how pretty it looks without it until recently).

However, when I turn on Secure Boot in UEFI settings, setting it to either to Microsoft Only or to Microsoft + 3rd Party CA (neither of which I really understand). It appears that UEFI skips over grub in the boot order, and boots directly into Windows. If I change it back to "Disabled" it boots into grub as normal.

I thought that Ubuntu came preconfigured to work with secure boot. What am I doing wrong? And what do I need to do to fix it?

Thanks!

---

### Post by oldfred on 2020-07-03
What version of Ubuntu?
Is it fully updated?

Ubuntu does work with Secure Boot, but if you have to have proprietary drivers for video or Wi-Fi chip, you have to add your own Key as Ubuntu cannot certify third party apps. A user can if that user trusts the vendor.

There are different versions of grub as shim & kernel that are signed, so they work with Secure Boot.

Probably easiest to boot Ubuntu live installer in UEFI mode with Secure Boot on. You probably have to turn on allow USB boot as that also is not considered Secure. Then run Boot-Repair to install the signed versions of grub & kernel.

---

### Post by Wrkcncanter on 2020-07-03
HI, and thanks oldfred!

I have Ubuntu 20.04 LTS, recently upgraded from 18.04. It was fully updated.

I solved the problem (and will update my post) by installing ```shim``` and ```shim-signed``` which were not installed on my system. ```grub-efi-amd64-signed``` was already at the latest version. Now I can boot into Grub and Ubuntu with UEFI set to Microsoft & 3rd Party CA, which I've learned is the expected setting.

(I actually discovered that this is what I needed to do by reading an Ubuntu doc wiki that referenced reporting a bug in shim if secure boot would not work -- I ran ```man shim``` and discovered it was not installed.)

I did not have to run Boot-Repair, but would that have found this issue? 

Thank you again for your answer!

---

