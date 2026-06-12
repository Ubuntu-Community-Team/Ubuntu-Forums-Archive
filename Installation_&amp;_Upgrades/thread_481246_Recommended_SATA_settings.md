---
title: "Recommended SATA settings?"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by JimNSB on 2007-06-22
I'm making another attempt to install Ubuntu on a new 965P system (details of last weekend's *crash-n-burn*: [http://ubuntuforums.org/showthread.php?t=475740](http://ubuntuforums.org/showthread.php?t=475740)).

I spent a good amount of time researching it, but I'm still unsure if the culprit is the 965P chipset, the JMicron controller-chip, the SATA/IDE setup (or BIOS settings) on these boards, or some combo of these things.  I've read that the '*fix*' (which they say was introduced in the *Edgy* release) still results in sporadic installation failures, and also that using the Live/Desktop disk _seems_ to have a higher success rate than the 'Alternate' disk (which I had used).

So I'm wondering if my decision to leave the mobo's SATA settings at their *default* values was part of the problem.  I have a lone 320gb SATA HD connected to SATA-II0 (controlled by the Intel ICH8 chip; access-mode set to LBA; no RAID), and a PATA optical drive plugged into IDE-1 (master, no slave, controlled by the JMicron chip). The board is a Gigabyte GA-965P-DS3 rev3.3, with a C2D E6600 and two 1gb sticks of G.Skill RAM running in dual mode.  

Here's the BIOS settings in question ...*defaults* (which I used) in brackets:[LIST]
[*]*SATA AHCI mode:* [Disabled]  _AHCI_
[*]*SATA Port0-3 Native Mode:* [Disabled] _Enabled_ (*Disabled = ports work in IDE Legacy mode; my HD is connected to Port0*)
[*]*Onboard SATA/IDE Device:* [Enabled] _Disabled_
[*]*Onboard SATA/IDE Ctrl Mode:* [IDE]  _AHCI_ _RAID/IDE_
[/LIST]

Would changing any of these give me a better chance of success?

Also, since the Desktop CD booted fine on my PATA optical drive I didn't bother with the RAID drivers for the JMicron chip.  I don't plan to plug anything into those SATA ports (or setup a RAID array), but the single IDE port that my optical drive uses _is_ controlled by that chip.  Should I be loading the RAID driver (or adding it to the .iso) before installing Ubuntu?

I should add that I scrubbed (wrote zeros to) the HD, but did _not_ reinstall Win2k; to simplify things I'm _only_ going to install Ubuntu (single-boot) using the Desktop CD.

TIA

---

### Post by 67GTA on 2007-06-22
As for the SATA settings, Ubuntu still ignores any changes you try to make. Sata drives have their own settings, and Ubuntu does not interfere with them. You can't even change DMA or I/O settings. They will go back to default.

---

### Post by JimNSB on 2007-06-22
> **67GTA said:**
> As for the SATA settings, Ubuntu still ignores any changes you try to make. Sata drives have their own settings, and Ubuntu does not interfere with them. You can't even change DMA or I/O settings. They will go back to default.

I thought I'd seen a number of posts here discussing AHCI settings.  Perhaps I'm thinking of that other 4-letter acronym that begins with 'A' (of course the name escapes me right now!) ...the 'power-management' one.

But I'm *pretty* sure these posts involved AHCI, SATA (SCSI), and HD's.

---

### Post by 67GTA on 2007-06-22
Your probably thinking of ACPI. That controls the power management. The BIOS usually controls that. If your BIOS gives the option, you can turn those settings off and control them with Ubuntu. The SATA  settings will not change. You can try to change your SATA settings with this command "sudo hdparm -l /dev/sda" but they always go back to default, or give some error message. This is a known bug with Ubuntu. If you have an IDE or ATA drive, you can tweak anything.

---

### Post by JimNSB on 2007-06-23
OK; located that thread: [http://ubuntuforums.org/showthread.php?t=388546&highlight=AHCI](http://ubuntuforums.org/showthread.php?t=388546&highlight=AHCI)

It _does_ discuss AHCI settings, and advises to leave them at *default*.

...which is bad news because that's exactly what I did, and Ubuntu wouldn't install (using the *Alternate* CD).

---

### Post by Breepee on 2007-06-23
I'm interested also, because  I have the same board and I also can't get Feistyy to run, not even the LiveCD.

I was advised, in order to install Windows, to leave all on default and put the jmicron on AHCI. That works for Windows, but sadly not for Feisty. I also havnt a clue, so I hope that this thread can shed some light on the matter.

---

