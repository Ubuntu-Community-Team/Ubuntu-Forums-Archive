---
title: "Making Netgear WG511 work"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gt24 on 2010-04-20
My wireless card does not work in Lucid.  Let's see why...

The key is the System Log, the kern.log.  You can keep this up to see new entries.

> Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.236096] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.236173] pci 0000:06:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.236258] pci 0000:06:00.0: supports D1 D2
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.236267] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.236280] pci 0000:06:00.0: PME# disabled
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.237993] p54pci 0000:06:00.0: enabling device (0000 -> 0002)
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.238030] p54pci 0000:06:00.0: PCI INT A -> Link[C195] -> GSI 11 (level, low) -> IRQ 11
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.238059] p54pci 0000:06:00.0: setting latency timer to 64
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.238464] p54pci 0000:06:00.0: firmware: requesting isl3886pci
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.252978] p54pci 0000:06:00.0: Cannot find firmware (isl3886pci)
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.252998] p54pci 0000:06:00.0: firmware: requesting isl3886
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.287165] p54pci 0000:06:00.0: PCI INT A disabled
Apr 20 22:12:33 sparkie-zombie kernel: [ 4701.287193] p54pci: probe of 0000:06:00.0 failed with error -2
Cute. However, note that this wireless card needs a firmware uploaded and that the kern.log says it cannot upload the firmware.  Simply enough, it wants the isl3886 firmware which isn't part of Ubuntu at the moment.

Remove the PCMCIA card if you haven't already.

It took me a while, but I found where the firmware must be.  I also found out where you can get the firmware.  So... I got firmware 2.13.12.0.arm and put it in the right place.  That didn't work...

> Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.984201] pci 0000:06:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.984291] pci 0000:06:00.0: supports D1 D2
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.984300] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.984314] pci 0000:06:00.0: PME# disabled
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.986088] p54pci 0000:06:00.0: enabling device (0000 -> 0002)
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.986124] p54pci 0000:06:00.0: PCI INT A -> Link[C195] -> GSI 11 (level, low) -> IRQ 11
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.986154] p54pci 0000:06:00.0: setting latency timer to 64
Apr 20 22:17:39 sparkie-zombie kernel: [ 5007.986276] p54pci 0000:06:00.0: firmware: requesting isl3886pci
Apr 20 22:17:39 sparkie-zombie kernel: [ 5008.022850] phy4: p54 detected a LM86 firmware
Apr 20 22:17:39 sparkie-zombie kernel: [ 5008.022863] p54: rx_mtu reduced from 3240 to 2376
Apr 20 22:17:39 sparkie-zombie kernel: [ 5008.022873] phy4: FW rev 2.13.12.0 - Softmac protocol 5.9
Apr 20 22:17:39 sparkie-zombie kernel: [ 5008.022883] phy4: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
Apr 20 22:17:40 sparkie-zombie kernel: [ 5009.144127] phy4: Cannot boot firmware!
Apr 20 22:17:40 sparkie-zombie kernel: [ 5009.144270] p54pci 0000:06:00.0: PCI INT A disabled
Apr 20 22:17:40 sparkie-zombie kernel: [ 5009.144329] p54pci: probe of 0000:06:00.0 failed with error -110

Note I have version 1 of this card.  The key is... get an older version!

The main site is here...

[http://wireless.kernel.org/en/users/Drivers/p54](http://wireless.kernel.org/en/users/Drivers/p54)

You can get older firmwares here...

[http://daemonizer.de/prism54/prism54-fw/](http://daemonizer.de/prism54/prism54-fw/)

You need to download the SoftMac PCI 2.12.0.0.arm file.

It should be in your Home directory, Downloads directory.  Copy that file (as sudo) into the following directory as the following name

/lib/firmware/isl3886pci

Now, put the card back in.  It works!

> Apr 20 23:00:37 sparkie-zombie kernel: [  398.760098] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
Apr 20 23:00:37 sparkie-zombie kernel: [  398.760177] pci 0000:06:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
Apr 20 23:00:37 sparkie-zombie kernel: [  398.760263] pci 0000:06:00.0: supports D1 D2
Apr 20 23:00:37 sparkie-zombie kernel: [  398.760273] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 20 23:00:37 sparkie-zombie kernel: [  398.760286] pci 0000:06:00.0: PME# disabled
Apr 20 23:00:37 sparkie-zombie kernel: [  398.762055] p54pci 0000:06:00.0: enabling device (0000 -> 0002)
Apr 20 23:00:37 sparkie-zombie kernel: [  398.762089] p54pci 0000:06:00.0: PCI INT A -> Link[C195] -> GSI 11 (level, low) -> IRQ 11
Apr 20 23:00:37 sparkie-zombie kernel: [  398.762309] p54pci 0000:06:00.0: setting latency timer to 64
Apr 20 23:00:37 sparkie-zombie kernel: [  398.762435] p54pci 0000:06:00.0: firmware: requesting isl3886pci
Apr 20 23:00:37 sparkie-zombie kernel: [  398.787479] phy5: p54 detected a LM86 firmware
Apr 20 23:00:37 sparkie-zombie kernel: [  398.787492] p54: rx_mtu reduced from 3240 to 2376
Apr 20 23:00:37 sparkie-zombie kernel: [  398.787502] phy5: FW rev 2.12.0.0 - Softmac protocol 5.5
Apr 20 23:00:37 sparkie-zombie kernel: [  398.787512] phy5: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
Apr 20 23:00:38 sparkie-zombie kernel: [  399.803537] phy5: hwaddr 00:09:5b:ea:ad:ce, MAC:isl3886 RF:Frisbee
Apr 20 23:00:38 sparkie-zombie kernel: [  399.824399] phy5: Selected rate control algorithm 'minstrel'
Apr 20 23:00:38 sparkie-zombie kernel: [  399.833545] Registered led device: p54-phy5::assoc
Apr 20 23:00:38 sparkie-zombie kernel: [  399.852166] Registered led device: p54-phy5::tx
Apr 20 23:00:38 sparkie-zombie kernel: [  399.853272] Registered led device: p54-phy5::rx
Apr 20 23:00:38 sparkie-zombie kernel: [  399.858948] Registered led device: p54-phy5::radio
Apr 20 23:00:38 sparkie-zombie kernel: [  399.858983] p54pci 0000:06:00.0: is registered as 'phy5'
Apr 20 23:00:38 sparkie-zombie kernel: [  400.122029] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 20 23:00:45 sparkie-zombie kernel: [  407.417056] wlan0: deauthenticating from 00:13:10:72:85:cb by local choice (reason=3)
Apr 20 23:00:45 sparkie-zombie kernel: [  407.419304] wlan0: direct probe to AP 00:13:10:72:85:cb (try 1)
Apr 20 23:00:45 sparkie-zombie kernel: [  407.422420] wlan0: direct probe responded
Apr 20 23:00:45 sparkie-zombie kernel: [  407.422440] wlan0: authenticate with AP 00:13:10:72:85:cb (try 1)
Apr 20 23:00:45 sparkie-zombie kernel: [  407.424265] wlan0: authenticated

The summary is that you need to download the right firmware for your Netgear card and place it in the right directory or else it won't work.  I suppose ndiswrapper could work for this card (it has in the past) but this shows that you don't have to use that.  Still, rather confusing to know what to do.

(Also not quite sure where this firmware file is officially.)

However, my wireless card works for now which makes me happy!  Hope these tips help you out too.

---

