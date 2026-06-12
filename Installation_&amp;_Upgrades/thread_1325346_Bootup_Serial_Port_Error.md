---
title: "Bootup Serial Port Error"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by aem389 on 2009-11-13
I have little experience with linux and Ubuntu was working fine before upgrading to the 9.10. Now, when the computer is starting up, I get error messages on screen, one after the other:

kernel: [  108.576130] serial8250: too much work for irq18

I discovered that I should check kern.log, and in it I found out the following, which I believe is relevant to the error:

kernel: [    0.626737] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

kernel: [    0.626835] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
kernel: [    0.627228] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

kernel: [    0.626923] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
kernel: [    0.627354] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

kernel: [    0.627519] serial 0000:02:03.0: PCI->APIC IRQ transform: INT A -> IRQ 18
kernel: [    0.627624] 0000:02:03.0: ttyS2 at I/O 0xce08 (irq = 18) is a 16450
kernel: [    0.627692] 0000:02:03.0: ttyS3 at I/O 0xce10 (irq = 18) is a 8250

kernel: [    0.627712] Couldn't register serial port 0000:02:03.0: -28

To the best of my knowledge, I do not have an external serial port, but I do have a modem card. I did not have this error before the upgrade. I also have the following messages related to IRQ18

kernel: [    0.721669] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
kernel: [    0.721721] ehci_hcd 0000:00:1a.7: PCI->APIC IRQ transform: INT C -> IRQ 18
kernel: [    0.721737] ehci_hcd 0000:00:1a.7: setting latency timer to 64
kernel: [    0.721740] ehci_hcd 0000:00:1a.7: EHCI Host Controller
kernel: [    0.721794] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
kernel: [    0.725691] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
kernel: [    0.725705] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xefffd000
kernel: [    0.740009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
kernel: [    0.740092] usb usb1: configuration #1 chosen from 1 choice
kernel: [    0.740122] hub 1-0:1.0: USB hub found
kernel: [    0.740131] hub 1-0:1.0: 4 ports detected


kernel: [    0.810182] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
kernel: [    0.810223] ohci_hcd 0000:02:02.0: PCI->APIC IRQ transform: INT B -> IRQ 18
kernel: [    0.810233] ohci_hcd 0000:02:02.0: setting latency timer to 64
kernel: [    0.810237] ohci_hcd 0000:02:02.0: OHCI Host Controller
kernel: [    0.810268] ohci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 4
kernel: [    0.810281] ohci_hcd 0000:02:02.0: irq 18, io mem 0xefeff000
kernel: [    0.872074] usb usb4: configuration #1 chosen from 1 choice
kernel: [    0.872102] hub 4-0:1.0: USB hub found
kernel: [    0.872111] hub 4-0:1.0: 2 ports detected


kernel: [    0.993306] uhci_hcd 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18
kernel: [    0.993312] uhci_hcd 0000:00:1d.2: setting latency timer to 64
kernel: [    0.993315] uhci_hcd 0000:00:1d.2: UHCI Host Controller
kernel: [    0.993347] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 11
kernel: [    0.993371] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f900
kernel: [    0.993450] usb usb11: configuration #1 chosen from 1 choice
kernel: [    0.993480] hub 11-0:1.0: USB hub found
kernel: [    0.993487] hub 11-0:1.0: 2 ports detected


kernel: [    1.120011] usb 1-4: new high speed USB device using ehci_hcd and address 3
kernel: [    1.283735] usb 1-4: configuration #1 chosen from 1 choice
kernel: [    1.580008] usb 8-1: new low speed USB device using uhci_hcd and address 2
kernel: [    1.757564] usb 8-1: configuration #1 chosen from 1 choice
kernel: [    2.040094] usb 10-1: new low speed USB device using uhci_hcd and address 2
kernel: [    2.229021] usb 10-1: configuration #1 chosen from 1 choice

---

### Post by achusonline on 2010-04-14
can anyone help with this?? i am having the same problem too...

---

