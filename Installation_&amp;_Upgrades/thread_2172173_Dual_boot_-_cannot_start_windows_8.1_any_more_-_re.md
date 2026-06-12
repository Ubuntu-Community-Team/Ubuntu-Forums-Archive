---
title: "Dual boot - cannot start windows 8.1 any more - rebooting to grub"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by istvan3 on 2013-09-03
Hi !

I successfully created a dual boot system on my 64 SSD harddisk.
[LIST]
[*]I installed Windows 8.1 through USB
[*]Then installed Ubuntu 13.04
[*]repaired GRUB with boot-repair to get Ubuntu into the boot menu
[/LIST]

I could boot into Windows and also Ubuntu.

After 2 days, now I cannot boot into Windows 8.1 any more.
[LIST]
[*]always, when I select the Windows entry, my system reboots back to the grub menu
[*]also when I try the second Windows entry in the grub menu (which has uefi loader in the name) it does not work
[/LIST]
- I tried boot-repair in Ubuntu. Don' work. Here is the outout: [http://paste.ubuntu.com/6059618/](http://paste.ubuntu.com/6059618/)
- I tried to use other [COLOR=#000000]bootmgfw.efi files (as shown in [/COLOR][http://paste.ubuntu.com/6059618/](http://paste.ubuntu.com/6059618/))

What I did between "it works" and "it does not work any more" is:

[LIST]
[*]adjustments for SSD in ubuntu (changed swappiness, changed booting with "noatime", chromium now don't use cache on disk, like written here: [https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-BIOS-and-UEFI:-set-it-to-AHCI](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-BIOS-and-UEFI:-set-it-to-AHCI))
[*]In windows I installed the Sandisk Utility to check the SSD and started it (showed S.M.A.R.T attributes). [http://kb.sandisk.com/app/answers/detail/a_id/9328/](http://kb.sandisk.com/app/answers/detail/a_id/9328/))
[*]No settings in BIOS ( I am using UEFI startup) were changed.
[/LIST]


What else can I check?

I know, Windows 8.1 is a preview and maybe buggy (like it cannot make an ethernet connection yet (no IP settings detected...)) but my dual boot worked.

---

### Post by istvan3 on 2013-09-05
**[COLOR=#ff0000]Problem solved.[/COLOR]**

The problem was: I have the Shuttle DS47 Mini PC with Intel NM70 Chipset. In BIOS, I set the IGD Memory Size to 1024M instead of 512M.
When 1024M was select - so from my 4GB, the integrated graphics card took 1 GB - Windows blocked loading. Ubuntu was working fine.
After switching back to 512M, Windows also booted correctly.

Now I also found a newer BIOS version from the Shuttle website and installed it.
(logged in in Windows, downloading from Shuttle website, unzip and execture the 64 bit program version)
BIOS version before:  04/10/2013
BIOS version now:  september 2013 date

Now also Windows works with IGD Memory Size Select of 1024M.

---

