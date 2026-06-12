---
title: "Install problems 20.04, 20.10, 21.04 with USB vs Radeon R9 380"
date: 2021-06-23
forum: Installation &amp; Upgrades
---

### Post by gwesty on 2021-06-23
Hi All,

Having an "interesting time" trying to get ubuntu to install on a machine I've just put together.

Mobo: GA-970
Processor: FX-8370
Memory: 16gb Crucial
SSD: Kingston 480gb

Booting any of 20.04, 20.10, 21.04 via UEFI from a memory stick (8gb Kingston) connected to USB2 port with my Radeon R9 380 gives me a load of "AMD-vi: Completion-wait loop timed out" and "AMD-Vi: Command buffer timeout" problems and X fails to start.
I found quite a few solutions suggesting to turn off IOMMU, when I try that I get lots of USB device not recognized errors and the installer fails to find the memory stick (and the keyboard and mouse stop responding).
Tried USB3 and USB2 ports, same issue.
I do have options in the BIOS for "Legacy USB support" (Enabled, Disabled, Auto) XHCI hand-off (enable or Disable) and EHCI hand-off (enable or disable), I think I've tried with all of those combinations with no luck. 
Booted Clonezilla and dropped a windows image onto the box and everything works fine so I can be fairly sure the hardware is ok
If I swap the Radeon for a (much older and let capable) Nvidia based card I have spare then the install works fine.
Once installed I swap out the Nvidia  card for the Radeon and it all stops working.
If I disable IOMMU on the installed system with the Radeon then it boots and X loads but I have no USB devices... (keyboard and mouse...).

Found a kernel.org post circa 2018 suggesting adding mem_encrypt=off to the kernel boot parameters but that doesn't seem to work either.

Anyone got any ideas what I could try to get this working?

---

### Post by MAFoElffen on 2021-06-24
EDIT: I stand corrected by oldfred in the next post (#3).

---

### Post by oldfred on 2021-06-24
Have you updated UEFI to latest available and updated SSD firmware also?

Some other similar threads:
GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0 uses this boot parameter: amd_iommu=on iommu=pt  & UEFI settings
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by gwesty on 2021-06-25
Hi OldFred,

The motherboard has the most recent bios update but I suspect this might not be the same as  having the latest UEFI. I have no idea how to update UEFI if that's the case but I'll have a look.

The SSD will also be running the firmware it came from the factory with.

I'll have a look at the threads you provided and see what occurs, thanks.

---

### Post by gwesty on 2021-06-25
OldFred, you are the man. Excellent searching skills.

All USB 2 and 3 ports working AND external AMD GPU... AT THE SAME TIME.

For the record, the fist link posted above seems to be a successful solution for me, copied and pasted below for ease of reference.

[COLOR=#000000]Edit Grub config:[/COLOR]
[COLOR=#000000]`sudo nano /etc/default/grub`[/COLOR]
[COLOR=#000000]Edit the line that looks like this:[/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
[COLOR=#000000]Add "amd_iommu=on iommu=pt" to the end of it so now the line now looks like this:[/COLOR]
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amd_iommu=on iommu=pt"[/COLOR]
[COLOR=#000000]Update grub:[/COLOR]
[COLOR=#000000]`sudo update-grub`[/COLOR]
[COLOR=#000000]once you have done that reboot the system and hit DEL / Delete key to enter BIOS/EUFI setup:[/COLOR]
[COLOR=#000000]Ensure IOMMU is enabled, XHCI handoff is enabled, EHCI handoff is disabled, USB Legacy support is enabled. OS type I have set to Windows8 but I have CSM enabled "Compatibility Support Module" so Linux will boot via BIOS emulation instead of UEFI.[/COLOR]

---

### Post by oldfred on 2021-06-25
Glad that worked. Please change to Solved so others can find a solution.

I do not have AMD system, but saved some notes as common question.

UEFI replaced BIOS.
But many manufacturers still call it BIOS as that is what they think users understand.
One of the better explanations of UEFI:
[https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface)
Old BIOS:
[https://en.wikipedia.org/wiki/BIOS](https://en.wikipedia.org/wiki/BIOS)

---

