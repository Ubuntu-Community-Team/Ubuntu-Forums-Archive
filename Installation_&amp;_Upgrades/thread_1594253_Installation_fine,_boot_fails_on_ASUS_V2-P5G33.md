---
title: "Installation fine, boot fails on ASUS V2-P5G33"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by hakimoto on 2010-10-12
[FONT=Tahoma]Hello everyone,

I've only just joined the forums. I have 10.04LTS running nicely on my laptop (I am writing this on it actually) and wanted to install it on my desktop machine, too. The desktop machine used to have OpenSolaris and Win7 on it. With the demise of OpenSolaris I switched to Ubuntu and am very happy indeed. Only, on the desktop, I can install 10.04LTS but it won't boot properly:

The machine is a ASUS V2-P5G33 barebone with Core2Duo E8400, 4 GB RAM, 2x 320 GB SATA HDDs, LG DVDRW, Nvidia 9600GT via DVI, USB keyboard and Logitech trackball via a PCI PS/2 card.

Windows 7 runs off the second harddrive. The first one used to have OpenSolaris on it, it's that one I've installed Ubuntu on.

It went like this:

1. Booted off CD
2. Installed with 20 GB /, 2 GB swap, rest /home all Ext4 on sda
3. Skipped updating and download of language packs at the end
4. Rebooted to HDD
5. Booted the first item in grub (2.6.32.-21-generic)

The machine will boot for a while, then display:[/FONT]

[FONT=Fixedsys]udev open /dev/null failed: no such file or directory

[FONT=Tahoma]The display will go blank and the machine has to be powered off hard.

(/dev/null exists, I booted into failsafe mode previously and checked, I've done this all several times round by now)

Editing the grub boot lines to exclude "quiet splash" in all cases and adding the following doesn't help:

nomodeset -> hangs at setting sensors limits
irqpoll -> /dev/null complaint, blanks, freezes
xforcevesa -> [/FONT][/FONT]/dev/null complaint, blanks, freezes
noapic -> /dev/null complaint, blanks, freezes
noacpi -> /dev/null complaint, blanks, freezes
nomodeset xforcevesa -> hangs at setting sensors limits
nomodeset and a combination of any or all of the above -> hangs at setting sensors limits

EXCEPT:

nomodeset xforcevesa noapic noacpi nosplash irqpoll -> this will boot into graphical mode, where the ubuntu logo with the five dots appears, the five dots will turn red and then it will freeze

The keyboard becomes unusable at all of the above.

I have the following notable items set in my BIOS, in case it's useful:

SATA enhanced, AHCI mode, CPU Ratio Auto, C1E off, MaxCPUID off, Vanderpool on, CPUTM off, Exec Disable Bit on, PECI off, SpeedStep off, Mem. remap on, Init PEG first, Internal gfx off, PEG Control auto, HD Audio on, Marvel GBit LAN on, Firewire on, J-Micron PATA off, Ser/Par off, Plug n Play OS yes, USB hispeed, EHCI handoff on, USB legacy on, ACPI Version on, ACPI APIC on.

I'm really at a loss here at how to proceed.

I'd previously used the failsafe console to upgrade the kernel, updated the machine and was manually able to start X after using a bootline with nomodeset xforcevesa noapic noacpi nosplash irqpoll set. Not really pretty.

If anyone has anything they can point me to, I'd be very happy to hear about it.

Thanks and best regards,

Hakim

---

