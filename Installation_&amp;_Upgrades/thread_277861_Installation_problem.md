---
title: "Installation problem"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by Kinny on 2006-10-15
Newbie here and I REALLY want to install Ubuntu. I built a machine using an Intel board/Intel Dual Core processor/250GB drive/512 RAM. Hard drive has not been formatted yet (if that matters).

When the installation begins, it only gets to:

"Uncompressing Linux ... Ok, booting the kernel." and dies. I'm using a Ubuntu CD v. 6.06 LTS.

I did find this on the forum -> [http://ubuntuforums.org/showthread.php?t=105460](http://ubuntuforums.org/showthread.php?t=105460), but didn't understand the solution.

Be patient with me ... I don't want to have to install a microsoft os.

---

### Post by adwait on 2006-10-15
What the solution there means is that when you boot from the CD, for the first 30 sec. it gives you an option about what to do before using the defualt options. So press F6 and then use one of the options there to see which one works for you.

---

### Post by Kinny on 2006-10-15
Upon reboot, I pressed F6 and change the boot options line to one of the follow (one at a time):

Boot: linux noapic 
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

Hangs with --> Assume root bridge [\_SB_.PCI0] bus is 0

with:

boot: linux acpi=off 

I get --> Kernel panic - not syncing:VFS: Unable to mount root fs on unkown-block(8,1)

---

### Post by gn2 on 2006-10-15
Try booting entering "noapic nolapic"

Worked for me on three different PC's in similar circumstances.

---

### Post by Kinny on 2006-10-15
Same hanging point (Assume root bridge [\_SB_.PCI0] bus is 0) when using the combination suggested by gn2.

A couple messages above the hanging point:

ACPI: Looking for DSDT  ... not found
....
BIOS bug, local APIC #0 not detected!...

---

### Post by Kinny on 2006-10-15
Using boot:linux acpi=off noapic nolapic, I'm getting this error -

Kernel panic - not syncing:VFS: Unable to mount root fs on unkown-block(8,1)

Does the drive have to be partioned before installing Ubuntu?

---

### Post by Kinny on 2006-10-16
Anyone else has any suggestions? Or should I move on to anyother distro?

---

### Post by Kateikyoushi on 2006-10-16
No, the live cd should boot without a partitioned hard drive.
What is the chipset on that motherboard ?

---

### Post by Kinny on 2006-10-16
The motherboard is Intel D946GZISSL Socket 775 Motherobard and the processor is Intel Core2 Duo E6300 1.86Ghz Socket 775.

---

### Post by Kateikyoushi on 2006-10-16
Core2 CPUs are quite new and the supporting chipsets as well.

Read [this page]("https://wiki.ubuntu.com/Core_2_Duo_Support") on the ubuntu wiki for more information.

---

### Post by gn2 on 2006-10-16
> **Kinny said:**
> The motherboard is Intel D946GZISSL Socket 775 Motherobard and the processor is Intel Core2 Duo E6300 1.86Ghz Socket 775.

You seem to be suffering from the hardware newer than software problem......

I would suggest trying another Distro, my personal favourite is PCLinuxOS

---

