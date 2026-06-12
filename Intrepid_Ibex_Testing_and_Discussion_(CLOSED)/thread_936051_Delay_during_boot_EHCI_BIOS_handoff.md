---
title: "Delay during boot: EHCI: BIOS handoff"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2008-10-02
I have an eight seconds long delay during booting:

```

kernel: [    1.240902] pci 0000:00:00.0: Enabling HT MSI Mapping
kernel: [    9.240018] pci 0000:00:02.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
...
kernel: [   11.488022] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

```

As you can see, USB 2.0 started fine and I have no problems with my USB devices.

I googled for "EHCI: BIOS handoff" and found following advice: disable USB legacy support in the BIOS, disable USB2.0.

USB is disabled for Keyboard and Mice (I have no USB legacy option), setting USB support to USB1.1 removed the delay and my USB2.0 devices didn't work.

"WTF?" My devices work fine so what's this delay all about?

---

### Post by MacUntu on 2008-10-02
The first and last *bump*, I promise!

---

### Post by MacUntu on 2008-10-06
Had to compile a new kernel to make it go away (seems to be there for ages but never noticed it because usplash was working).

/drivers/usb/host/pci-quirks.c

Changed the waiting time for BIOS handoff to 500ms instead of 5000ms. 

I'm still thinking about reporting this as a bug since USB2.0 is working flawlessly and I don't see a reason to wait five seconds EVERY boot if I know in advance that BIOS handoff will fail.

---

