---
title: "[SOLVED] ACPI issues with Gutsy - booting issues in general"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by jacksmash on 2008-05-12
Hi,

I justed install 7.10 today. 

When I would first boot the system, the boot process would take forever. I pressed ALT+F1 to see what was taking so long. The boot would chug at these points:

"wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)"

Then... it would slow down again at this point:

"Loading ACPI Modules"

So, after doing some research, I tried the acip=off, noapic boot options. This caused the boot process to move really quickly, but with some pnpbios errors. So, I tried adding pnpbios=off to the boot, and it got rid of those errors - but it seems my system is a tad unstable right now.

Anyhow, I'm really not a techie - so I don't understand a lot of these messages.

THe other problem (of course) is that I now have no battery monitor, wireless, etc.

Here is my lspci output:

```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7930
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7932
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7934
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7936
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7937
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 7942
01:05.2 Audio device: ATI Technologies Inc Unknown device 793b
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
08:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

Any suggestions as to how to improve my situation would be appreciated.

Cheers.

---

### Post by dstew on 2008-05-12
You probably just need to install the proprietary (restricted) Atheros hardware abstraction layer (HAL) for your WiFi card. You should be able to find it and activate it in the System --> Administration --> Restricted Drivers menu item. You probably don't need those kernel options. I am not sure if you should take the kernel options out before or after you activate the Atheros HAL though...

---

### Post by jacksmash on 2008-05-14
Ok, so I was able to get wireless working no prob with Wifi-Radar (I used ndiswrapper to install the driver).

So, I tried disabling those options from the boot menu, and rebooted the system. Here are two things I noticed:

1. When I reboot from Ubuntu, the startup screen hangs (before even getting to the grub menu). I have to power the computer off and on again to get it to work.

2. When I do boot into Ubuntu, the process is still quick. So it seems you're right about not needing those kernel options.

Problem is, I've done a lot of searching on #1 and can't come up with anything helpful. Am I going to be stuck with this problem?

---

### Post by jacksmash on 2008-05-14
I decided to mark this thread as solved since the original question was answered. I'll start another to follow-up with my next problem.

---

