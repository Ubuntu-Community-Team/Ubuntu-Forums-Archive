---
title: "IRQ Conflicts - Feisty"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by RevNL on 2007-05-29
6.06 works great on my system but I need more software support so I have to upgrade.
6.10 kernel panics on boot.
7.04 won't work with the NIC, soundcard, or USB.  It seems to be an interrupt conflict:

/proc/interrupts under 6.06:
           CPU0       
  0:     277159    IO-APIC-edge  timer
  1:         10    IO-APIC-edge  i8042
  6:         21    IO-APIC-edge  floppy
  8:          3    IO-APIC-edge  rtc
  9:          0   IO-APIC-level  acpi
 14:        412    IO-APIC-edge  ide0
 15:       2950    IO-APIC-edge  ide1
177:       9500   IO-APIC-level  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4
185:        143   IO-APIC-level  eth0
193:       4724   IO-APIC-level  VIA8233
NMI:          0 
LOC:     276434 
ERR:          0
MIS:          0


/proc/interrupts under 7.07:
           CPU0       
  0:     103178   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  2:          0    XT-PIC-XT        cascade
  6:         35   IO-APIC-edge      floppy
  8:          3   IO-APIC-edge      rtc
 14:        464   IO-APIC-edge      ide0
 15:       6960   IO-APIC-edge      ide1
 16:          0   IO-APIC-fasteoi   uhci_hcd:usb1, eth0
 17:          0   IO-APIC-fasteoi   uhci_hcd:usb2
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb3, VIA8233
 19:          0   IO-APIC-fasteoi   ehci_hcd:usb4
NMI:          0 
LOC:     103046 
ERR:          0
MIS:          0

See the difference?  Why the change? Both of those listings came from a boot from a Live CD.   I've fiddled with all the BIOS options.  No difference.  So far 7.04 is totally unusable.

Help?  Advice?

Thanks!

---

### Post by RevNL on 2007-05-29
I'm going to totally noob this up by admitting that I found the answer shortly after posting the question.  Seriously, though, I searched for several days before bugging everybody.

"maksei" posted a reply to another install question recommending passing cheatcodes to the kernel at boot: "noacpi noapic nolapic irqpoll pci=routeirq ide=nodma".

Second try, "noapic" fixed it.  I haven't looked at /proc/interrupts but usb mouse, usb keyboard, usb drive, sound, integrated nic, etc are all online.  "apic" appeared in proc/interrupts so I figured it must mean something.  Who knows what it does, but apparently it doesn't work right!

I take back all the awful things I said about Ubuntu over the last several days.

---

### Post by rajnshah on 2007-05-30
I am also facing one of the similar problems while booting with livecd, maybe, i will try the cheat codes, thanks for the post

---

