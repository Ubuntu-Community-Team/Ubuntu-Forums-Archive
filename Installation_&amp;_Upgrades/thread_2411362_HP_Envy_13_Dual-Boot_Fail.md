---
title: "HP Envy 13 Dual-Boot Fail"
date: 2019-01-29
forum: Installation &amp; Upgrades
---

### Post by sean7311 on 2019-01-29
Hello,

I'm having some trouble with getting my Windows 10 laptop to boot Ubuntu from a USB. Hardware wise it's a HP Envy 13 i5-8250U with GeForce MX150 graphics card running Windows 10. I've created a bootable USB using Rufus (Ubuntu 18.04) and I've tried both MBR (legacy mode enabled) and GPT (legacy disabled) partition schemes, all with quick boot and secure boot disabled but the same issue occurs. When I try to install Ubuntu, the ubuntu logo will appear but after approx 5 seconds, it returns a black screen then starts with the usual windows 10 boot. I've tried moving around the boot order, I've double (and triple checked) that the iso was downloaded correctly and installed correctly on the USB so I'm looking for something to try next, it's quite a specific issue and no one else seems to have the exact issue I am so any help would be great!

---

### Post by oldfred on 2019-01-29
With nVidia, you need nomodeset to boot installer & then first boot of install or until you add the nVidia driver from the Ubuntu repository. 
You only should be installing in UEFI boot mode since Windows is UEFI. See link in my signature below for more UEFI info.
If you convert to MBR(msdos) you destroy Windows as it is UEFI boot and only boots from gpt with UEFI.

Have you updated UEFI from HP? And if SSD, updated firmware?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[URL="https://ubuntuforums.org/showthread.php?t=2407615"]https://ubuntuforums.org/showthread.php?t=2407615
      [/URL]
 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309) 
    [URL="https://ubuntuforums.org/showthread.php?t=2407615"]
[/URL] 

    [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by sean7311 on 2019-01-29
Thanks for giving me a hand. I checked HP Support Assistant and the Windows updater. All firmware is up to date and I tried changing the boot parameter to nomodeset. This didn't work, in the script that followed, it flagged up "stdin: invalid argument". But, the rest of the time it had the same issue that it gives up with ubuntu and resorts back to windows 10

---

### Post by oldfred on 2019-01-29
It sounds like you added the nomodeset to wrong place or typo on entry?

If booting in UEFI mode, you get grub menu, and then e for edit.
You can replace the quiet splash on the linux line with nomodeset.
But some systems need additional parameters also.

---

