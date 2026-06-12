---
title: "LiveCD 6.10 causes freezes"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by elitelinuxnoob on 2007-03-02
I have made a copy of Ubuntu 6.10 to try the Livecd but I my computer freezes at the "splash screen" with a corrupted thin line of graphic. I have made made images of 4 different CDs at lower speeds such as 4x and I can't go any lower. I redownloaded ISOs about 3 times to no avial. In InfroRecorder the program Ubuntu recommends I have  my settings with Write method: Session-at-once (SAO) if thats important. Is there another free ISO program you know of? I don't think it's the program but maybe. Everythings works fine in Windows XP X64 with no software/hardware problems. 

System
DFI lanparty nF4 SLI
AMD 64 4000+
2 GB ram
2 WD 160GB Raid 0
2x 7800GTs

---

### Post by Kateikyoushi on 2007-03-02
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by elitelinuxnoob on 2007-03-02
> **Kateikyoushi said:**
> Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

Ok, could you please tell me how I enter these? Do I type Boot: linux noapic Boot: linux pci=irqroute....?

thnak you

---

