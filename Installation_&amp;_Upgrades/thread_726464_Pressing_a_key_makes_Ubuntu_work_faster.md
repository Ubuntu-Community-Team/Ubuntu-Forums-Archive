---
title: "Pressing a key makes Ubuntu work faster"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by aw5k on 2008-03-16
I have a really strange behaviour on my Ubuntu system (a Samsung R60 Notebook).
When booting up, for example, the machine freezes and only resumes when I press some key (doesn't matter which one). It's as if the key press is giving the machine a signal to process. I have no explanation for that phenomenon, I am wondering whether anybody else has?
Thanks.

---

### Post by aw5k on 2008-03-16
This is really strange.
As an example:

If I do "ping localhost" I get the first line of output (saying how long the packet took, etc.). However, I have to press some random key to get the next line. I get them all in the correct timing if I let the key pressed down. 

This behaviour is similar to that of a clock. It is as if the keyboard signal acts as a clock. Any ideas?

---

### Post by tgalati4 on 2008-03-17
Press a key, then in a terminal post the output of:

>dmesg | tail -25

---

### Post by aw5k on 2008-03-18
Hi, thanks for your reply.
I did what you said, here's what I get:

root@home:~$ dmesg | tail -25
[  133.572000] Bluetooth: HCI socket layer initialized
[  133.588000] Bluetooth: L2CAP ver 2.8
[  133.588000] Bluetooth: L2CAP socket layer initialized
[  133.652000] Bluetooth: RFCOMM socket layer initialized
[  133.652000] Bluetooth: RFCOMM TTY layer initialized
[  133.652000] Bluetooth: RFCOMM ver 1.8
[  136.936000] [fglrx] Maximum main memory to use for locked dma buffers: 1655 MBytes.
[  136.936000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  136.968000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[  139.436000] [fglrx] total      GART = 130023424
[  139.436000] [fglrx] free       GART = 114032640
[  139.436000] [fglrx] max single GART = 114032640
[  139.436000] [fglrx] total      LFB  = 268173312
[  139.436000] [fglrx] free       LFB  = 253784064
[  139.436000] [fglrx] max single LFB  = 253784064
[  139.436000] [fglrx] total      Inv  = 0
[  139.436000] [fglrx] free       Inv  = 0
[  139.436000] [fglrx] max single Inv  = 0
[  139.436000] [fglrx] total      TIM  = 0
[  159.144000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  166.352000] NET: Registered protocol family 10
[  166.352000] lo: Disabled Privacy Extensions
[  166.352000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  176.796000] ath0: no IPv6 routers present
[  249.140000] ath0: no IPv6 routers present
acb71@blessing:~$ dmesg | tail -25
[  133.572000] Bluetooth: HCI socket layer initialized
[  133.588000] Bluetooth: L2CAP ver 2.8
[  133.588000] Bluetooth: L2CAP socket layer initialized
[  133.652000] Bluetooth: RFCOMM socket layer initialized
[  133.652000] Bluetooth: RFCOMM TTY layer initialized
[  133.652000] Bluetooth: RFCOMM ver 1.8
[  136.936000] [fglrx] Maximum main memory to use for locked dma buffers: 1655 MBytes.
[  136.936000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[  136.968000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 18
[  139.436000] [fglrx] total      GART = 130023424
[  139.436000] [fglrx] free       GART = 114032640
[  139.436000] [fglrx] max single GART = 114032640
[  139.436000] [fglrx] total      LFB  = 268173312
[  139.436000] [fglrx] free       LFB  = 253784064
[  139.436000] [fglrx] max single LFB  = 253784064
[  139.436000] [fglrx] total      Inv  = 0
[  139.436000] [fglrx] free       Inv  = 0
[  139.436000] [fglrx] max single Inv  = 0
[  139.436000] [fglrx] total      TIM  = 0
[  159.144000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  166.352000] NET: Registered protocol family 10
[  166.352000] lo: Disabled Privacy Extensions
[  166.352000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  176.796000] ath0: no IPv6 routers present
[  249.140000] ath0: no IPv6 routers present

Any idea?
For example, when I play this game NIbbles (a Snakes version for Ubuntu), the Snake sometimes suddenly stops (!) and I need to press some key for it to continue. Really weird.

---

### Post by tgalati4 on 2008-03-20
Try running nibbles in a terminal.  When it stops, use alt-tab to switch to the terminal and see if there are any error messages.

Sounds like soda may have been spilled in the keyboard.

---

### Post by aw5k on 2008-03-31
Hmm, it now seems that Nibbles is working just fine.
I only get the problem when booting and shutting down Ubuntu. I really HAVE to press a key to make Ubuntu start. Otherwise, it just stops at some moment. No error messages or anything. If I look at console output at booting stage everything seems just fine except that nothing happens.

Any idea?

---

