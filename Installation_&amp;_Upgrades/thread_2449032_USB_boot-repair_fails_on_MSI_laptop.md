---
title: "USB boot-repair fails on MSI laptop"
date: 2020-08-18
forum: Installation &amp; Upgrades
---

### Post by djohnlewis on 2020-08-18
Successfully installed Ubuntu 20 on my MSI GL72M-7REX laptop, but it won't boot into it.

I know it was successful because 'ubuntu' appears in the boot menu when I press F11 at the BIOS screen, and I'm sure the BIOS is set for USB boot because I've had rufus create a live USB that worked.

Please can you help. My boot info summary is available at [paste.ubuntu.com/p/YfXMPbg3kN]("http://paste.ubuntu.com/p/YfXMPbg3kN"), which comes from a failed attempt to use boot-repair 

Thanks
John

---

### Post by CelticWarrior on 2020-08-18
You don't have BIOS, you have UEFI, the firmware that replaced BIOS a decade ago.
Please open the UEFI ("BIOS") settings > Boot menu (or something similar), find the setting where it shows "Windows bootloader manager" and replace it withe "Ubuntu".

If you're dual-booting with Windows then you must disable Windows' Fast Startup feature.

---

### Post by djohnlewis on 2020-08-18
Thanks for bringing me into the 21st century with correcting my BIOS talk. I did find and correct the boot menu in the UEFI pages.

So,thanks very much. I was surprised that the boot order could be overridden by the boot menu

---

### Post by CelticWarrior on 2020-08-18
You're welcome.

Please use the thread tool to mark this one as solved.

---

