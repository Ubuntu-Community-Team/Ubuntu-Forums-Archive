---
title: "G580 laptop won't turn off after ubuntu install and bios problems"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by paddy4 on 2014-04-12
First and foremost I'm 100% sure this issue has nothing to do with ubuntu itself, the issue first began after attempting to dual boot windows 8 and ubuntu. Now my laptop won't shutdown in either ubuntu or windows 8, both hang on the shutdown screens, likely something to do with an acpi issue from what I've been reading and pressing F2 which normally would've taken me into the BIOS screen simply does to grub. After some searching I found this: [https://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/m-p/1067699#M42795](https://forums.lenovo.com/t5/Lenovo-3000-and-Essential/BIOS-for-G580-notebook/m-p/1067699#M42795) which at least let me boot into the BIOS by pressing F12 at startup. However the issue with the hanging on shutdown still remains and I believe both issues are releated.

Anyway from what I understand the issue is something along the lines of the bios being moved from the boot order. This post seems to explain something along the lines of what's happening: [http://www.bios-mods.com/forum/Thread-BIOS-SETUP-MENU-IS-NOT-ACCESSIBLE?pid=60907#pid60907](http://www.bios-mods.com/forum/Thread-BIOS-SETUP-MENU-IS-NOT-ACCESSIBLE?pid=60907#pid60907)

Yet efibootmgr and efibootmgr -v don't return anything and trying to delete the entry return a not found for boot values. It seems to be quite a frequent issue with instaling linux on these laptops as the lenovo forums have a few threads with bios missing issues.

Boot-repair give me this url: [http://paste.ubuntu.com/7239294/](http://paste.ubuntu.com/7239294/)

Thanks in advance for any help!

---

### Post by oldfred on 2014-04-12
You show a UEFI boot of Ubuntu only, no Windows?

One Lenovo user posted this:
 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

Have you turned off secure boot?
Have you updated UEFI/BIOS from Lenovo?

Have you tried 14.04? It does have a lot of updates for UEFI.

---

### Post by paddy4 on 2014-04-19
> **oldfred said:**
> You show a UEFI boot of Ubuntu only, no Windows?

One Lenovo user posted this:
 

Have you turned off secure boot?
Have you updated UEFI/BIOS from Lenovo?

Have you tried 14.04? It does have a lot of updates for UEFI.

Thanks for the reply,

Windows 8 is no longer installed and my bios doesn't give me the option to turn off a secure boot. I've attempted to reflash the bios and it reports that it installed successfully however I don't think it realises that it's been moved. When I press F2 which previously booted me into bios now boots me into grub. 

I've installed 14.04 and boot-repair give me this link: [http://paste.ubuntu.com/7283267/](http://paste.ubuntu.com/7283267/)

Thanks again for the help!

---

### Post by oldfred on 2014-04-19
Not sure what to suggest. Seen several other threads on similar versions of Lenovo with issues.

Boot-Repair reports this:
 LIne 413
efibootmgr -v
Unusual EFI:
SecureBoot enabled.

And this on line 8244

 Wrong GRUB version detected.

I think all the other entries are becuase of above version issue.
But do not know if actual version of grub or that it is related to secure boot version vs non-secure boot.

You show signed kernels installed.

Also some have to totally power down to get system to reset. And that is shutdown, remove battery and hold power switch for a bit to drain capacitors.

      
 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

---

