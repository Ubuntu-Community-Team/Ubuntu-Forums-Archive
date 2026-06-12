---
title: "&quot;pppoeconf&quot; causes computer freeze"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by Brikkah on 2004-12-23
Hello,
Recently I have installed Ubuntu Linux. When I run linux from my hard drive the following command causes the computer to freeze: "sudo pppoeconf". It says that it found 2 ethernet cards: eth0 and eth1, that is right. It ask if that are all the cards, and I click yes. But then nothing happens, and the computer freezes. When i execute the command on the Live CD it works fine and I can internet.
I hope someone can help me.

Thanx

---

### Post by Brikkah on 2004-12-25
It is probably an IRQ problem, here is some more information:
when i boot with the parameter "pci=noacpi" and then try to configure my connection with "sudo pppoeconf" my computer gives a beep and this error shows in the terminal: Localhost kernel: Disabling IRQ #9.
In windows my IRQ are as follow:
> IRQ 0 Systeemtimer OK 
> IRQ 1 Standaardtoetsenbord (101/102 toetsen) of Microsoft Natural 
> PS/2-toetsenbord OK 
> IRQ 6 Standaarddiskettestationcontroller OK 
> IRQ 8 Systeem-CMOS/Real-timeklok OK 
> IRQ 11 Systeem dat voldoet aan Microsoft ACPI OK 
> IRQ 11 NVIDIA RIVA TNT2 Model 64/Model 64 Pro OK 
> IRQ 11 VIA Rev 5 of later USB universele host-controller OK 
> IRQ 11 VIA Rev 5 of later USB universele host-controller OK 
> IRQ 11 VIA AC'97 Audio-controller (WDM) OK 
> IRQ 11 Intel 21041-Based PCI Ethernet Adapter (Generic) OK 
> IRQ 11 Realtek RTL8139/810x Family Fast Ethernet NIC OK 
> IRQ 12 PS/2-compatibele muis OK 
> IRQ 13 Numerieke-gegevensprocessor OK 
> IRQ 14 Primair IDE-kanaal OK 
> IRQ 15 Secundair IDE-kanaal OK 

cat /proc/interrupts gives the following:
  CPU0 
0: 563637 XT-PIC timer 
1: 817 XT-PIC i8042 
2: 0 XT-PIC cascade 
6: 17 XT-PIC floppy 
8: 1 XT-PIC rtc 
10: 19109 XT-PIC uhci_hcd, uhci_hcd, VIA686A 
11: 0 XT-PIC acpi 
12: 29015 XT-PIC i8042 
14: 8851 XT-PIC ide0 
15: 9446 XT-PIC ide1 
NMI: 0 
LOC: 563106 
ERR: 28883 
MIS: 0 


I hope someone can help me now

---

