---
title: "Boot Error With Dual Boot Windows 7"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by m47h3us on 2011-10-26
I have a strange issues not sure if it's my motherboard with some settings it does not like but it will only boot into grub when it tries to boot cd first.

At the moment as a temporary fix I've set CDROM as first boot but it makes post a lot slower.

I have had one issue where it was not booting at all into grub but this was due to a Flexnet thing in the MBR.

System is following:
Motherboard: Gigabyte GA-Z68A-D3-B3
CPU: i5 2500K @ 4.2Ghz
RAM: 4GB
Graphics: ATI HD4870X2
OS: Windows 7 x64 & Ubutnu 11.10 x64

IF you need any more info just ask and all hope would be appreciated.

---

### Post by oldfred on 2011-10-26
Tis strange.

I would check some BIOS/UEFI settings. I assume you are booting with BIOS but new motherboards also have a UEFI mode.

Some have turned off fastboot or quickboot, changed from auto to LBA,  removed a boot from a device (foppy, firewire) that does not exist, Udated BIOS, changed to 3GB/s ports from 6GB/s, or AHCI mode settings.  May be others with the newest systems.

---

### Post by m47h3us on 2011-10-26
Ah yes I fixed it was on AHCI and now its on raid and boots fine, well Linux is but windows is not happy woops

---

### Post by oldfred on 2011-10-26
RAID is not a good setting unless you really are running RAID. It also writes metadata to the drive that then interferes with standard installs.

I turned on AHCI on my system and Ubuntu still worked but my old XP stopped working - no loss. Windows 7 already has the AHCI drivers.

---

### Post by m47h3us on 2011-10-26
Do you think its a problem with grub not liking AHCI

---

### Post by m47h3us on 2011-10-26
OK, now I've set it back to AHCI and turned quick boot off and it works fine not sure why that is, must have been missing some checks or something.

---

### Post by oldfred on 2011-10-26
Glad that worked & good to know what does work.:)

---

