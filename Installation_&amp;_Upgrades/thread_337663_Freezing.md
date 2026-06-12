---
title: "Freezing"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Sense on 2007-01-13
I just received my new computer in parts, because I choosed to assamble it by myself. The following specifications are usefull when solving this problem:
mainbord:Asus M2NPV-VM
graphics: nVidia GeForce 6150 (onboard)
proccessor: AMD Athlon 64 3800+
ram: 2x Kingston ValueRam KVR667D2E5/512 (512MB, ECC) 
harddisk: Maxtor DiamondMax 7 160GB _**SATA**_-II (the cable is in SATA1(out of 4))
old harddisk: Seagate Baracuda 80GB _IDE_(with my old installation on it)(Primary Slave)

When I was finished, I tried to install Kubuntu 6.10 amd64 with the default desktop cd(burned by myself), but because I forgot to insert the CD I booted up into my old installation. THat worked fine for a short time, until suddenly the computer freezed. I thougt it was because OS don't run very smootly on a harddisk wich(is that correct english?) is slave.
I booted the second time with the install CD, but that stopped at the splashscreen. I reseted the computer and removed quit and splash from the boot options. Then the computer stopped at the following two messages:

```
[{numbers}.{numers}] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
[{numbers}.{numbers}] ata2: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
```

I tested the Ubuntu 6.06 i386 CD and booted into the safe mode and removed splash form the boot options. Then I got the following errors:

```
[{numbers}.{numbers}] ..MP-BIOS bug: 8254 timer not conected to IO-APIC
[{numbers}.{numbers}] Kerneld panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the noapic option
[{numbers}.{numbers}]
```

I changed 'ACPI APIC support' in the BIOS to disabled and now the Ubuntu CD ws booting. The Kubuntu CD ws also working, so I tried to install. But when the installation program came to the point were you have to select te harddisk, it freezed. The second time I tried it also freezed. And with the old installation I had for freezes and one kernel panic. What should I do? And what is the use of APIC?
It would be a waste if I should go back to my old computer from '98.

EDIT: Maybe it's useless, but when I do dpkg-reconfigure xserver-xorg on my old installation, discover doens't recognize my onboard video.

---

### Post by dtfinch on 2007-01-13
ACPI and APIC are entirely different. Try the noapic kernel option at boot, as it suggested. If that makes the freezes go away, then as root after you install, add noapic to the "# defoptions=" line in /boot/grub/menu.lst and run update-grub to make it permanent.

I have a system that had similar apic related freezes. It's probably 3-4 years old though.

---

### Post by Sense on 2007-01-14
I know it's different. I will try your suggestion. But now I've got other problems. After the beep at start-up the CPU fan stops. I didn't changed anything in the BIOS, but removed the digital audio cable(from one DVD player to mb) and the cables(IDE and power) to the old harddisk and on dvd player. I tried again after disabling Qool'n'Quiet in the bios, but that didn't changed anything. My parents say, i should mail the vendor, but that's a webstore(not a very large) and I don't think they are able to solve it on distance. BUt maybe they do. Otherwise we're going to bring it to the nearest computer store, they solve also computer problems and sell computers with Ubuntu preinstalled, so the knowledge is available.
I could try your suggestion, but I'm afraid the proccessor will burn  if I'm arrived at the installer.

EDIT: The problem with the CPU fan is solved. When I saw the temperature raising in the BIOS, the CPU fan started. It is Qool'n'Quiet
But with also with noapic added to the boot options it's still freezing, altough it isn't at one point, but on different stages.

---

### Post by Sense on 2007-01-14
With the options 'noapic' 'nolapic' added and AMD Live! disabled in the BIOS, the computer freezes and beeps at after the six stept, when te installation starts.

EDIT: I think I've got the problem. I think that X11 has got trouble with handling the onboard graphics. I'm going to download the alternate cd, and search for work arrounds for onboard.

---

### Post by Sense on 2007-01-15
It's solved! The installation with the alternate CD succeeded, and I'm now on my new installation, and it hasn't frozen at all!
But now a other small problem. Because X doens't recognize my graphics, the selected driver is vesa, can I safely install the nvidia drivers without messing X? And are there any options to let X recognize it?

---

