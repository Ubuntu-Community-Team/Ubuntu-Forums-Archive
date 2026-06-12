---
title: "Soft lockup on upgrade to 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by gsimpson on 2008-04-27
I have an Acer 4315 laptop supplied with Linux Ubuntu

I upgraded my desktop to 8.04 with no problems

The Acer laptop starts to boot but comes up with error 

"Bug: Soft lockup - CPU#0 stuck for 11s!"

That was with default 2.6.24-16

Booting using 2.6.22-14 results in successful boot up but the network card doesn't work

---

### Post by psyburn on 2008-04-27
Well your not alone in this...
I have an Acer Aspire 5050-3242
I was running okay with Gutsy then Hardy Beta and Hardy Final.
Suspend and Hibernate did horrible things but everything else was fine..

But I was stupid and decided that my suspend and hibernate issues could be fixed with a BIOS update after reading the BIOS changelog.

Well long story short I updated the BIOS to v.3315 and after grub the splash scrren hung. Hmm... downgrade to v.3309, same thing. Booted from alternate AMD64 install CD. Then I saw my error: "Soft lockup - CPU#0 stuck for 11s"

So my laptop cannot use Linux right now. :confused:

Note: My suspend issues were horrible. It seems the IDE controller was still sleeping after waking back up. System was usable for what was in RAM but nothing really worked. Forcing the power off; the next reboot would give me GRUB Error code 17. (AKA /boot/grub/menu.lst cannot be found)
The ReiserFS were unusable at that point.
The more I type this out the more I realize I was going in the wrong direction.

On both cases logs were not getting made so I have no debugging info.

EDIT:
I got lucky and Gutsy Live CD booted

```
ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: b0100000-b01fffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
        I/O ports at 8440 [size=8]
        I/O ports at 8434 [size=4]
        I/O ports at 8438 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8400 [size=16]
        Memory at b0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at a8000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at b0005000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at b0006000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at b0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80) (prog-if 82 [Master PriP])
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0c, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: b0200000-b02fffff
        Prefetchable memory behind bridge: a4000000-a7ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at b0120000 [disabled] [size=128K]
        Capabilities: <access denied>

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 168, IRQ 23
        Memory at b0210000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: a4000000-a7fff000 (prefetchable)
        Memory window 1: ac000000-affff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at b0211000 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at b0211400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at b0211800 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: medium devsel, IRQ 22
        Memory at b0211100 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 010f
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a000 [size=256]
        Memory at b0211c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:04.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Universal Scientific Ind. Unknown device 2102
        Flags: bus master, medium devsel, latency 168, IRQ 21
        Memory at b0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
```

---

### Post by psyburn on 2008-04-27
[COLOR="Red"][SIZE="4"]**_I tried 7.04 Alternate Install CD and got the same lockup._**[/SIZE][/COLOR]

Ubuntu 7.10 Desktop made a successful install as far as I can tell but had the "nothing shows up on screen" issue.

Working on with a 7.10 Alternate CD which doesn't have the same video issue.

This means with the "Desktop/LiveCD" I get a blank screen at boot up. No splash, no login...

Yet with the "Alternate" CD previously I would see the splash screen at boot up and the login screen.

I'll edit with the results.

EDIT:
Success with the Gutsy install off of the alternate CD

---

### Post by Kurppa_ on 2008-04-28
I have the same issue. Acer Aspire 1680 here. Hardy (8.04) installs fine, but after I get to xorg, it halts. When quickly switching to console, I get that same message over and over again. Gutsy (7.10) works fine.

---

### Post by frOzz on 2008-04-29
hi ubuntu community, i have the same issue "Bug: Soft lockup - CPU#1 stuck for 11s!" when i try to use live cd ubuntu hardy heron 8.04 64bits, my laptop is a sony vaio vgn 385.. i already have installed gutsy gibbon

---

### Post by gadfium on 2008-04-30
Same issue here with an Acer Aspire 4315-100508Ci. The machine was factory installed with Gutsy Gibbon, and I believe is fairly original apart from installing software updates as prompted, and converting the hard drive from ext2 to ext3. The bios has not been updated.

I upgraded to 8.04 today by clicking the "Upgrade" button in the desktop gadget that usually prompts me for upgrades. No problems in the upgrade until reboot. I was prompted to replace a couple of files in /etc/modprobe.d, which I did, and a samba file, which I didn't (but I'm not connecting to the network so I doubt that matters). 

On reboot, I get the same recurring error "Bug: Soft lockup - CPU#0 stuck for 11s!" as the first poster in this thread.

If I boot to the older kernel 2.6.22-14, the boot into Gnome works fine but with no network or wireless connectivity. 

I also cannot run "sudo" because it informs me it cannot find the path to "Claire", which is the laptop name. This makes testing various combinations of old and new configuration files in /etc/modprobe.d much more difficult than I'd like, since all files in that directory and the directory itself are root access only.

I can boot from an old Kubuntu Cd, which gives me command line access to the files.

What I'd like is advice on
1) how to get "sudo" working again on the older kernel. This will make following any other advice a lot easier.

2) get my wireless network functional again on the older kernel. Various packages were automatically deleted during the upgrade; will there be a list of those somewhere I should post? 

3) get the newer kernel, 2.6.24-16, booting with network/wireless support and sudo access.

Having 3 work is the most desirable, but I'd settle for 1 + 2. Until then, the laptop is useless to me.

Thanks in advance.

gadfium

---

### Post by gadfium on 2008-04-30
The problems I've encountered with the Acer Aspire 4315 and an upgrade to 8.04 appear to be caused by ndiswrapper. How do I disable this if I boot into the older kernel (or boot to a command line from an old Kubuntu CD)?

See [https://answers.launchpad.net/ubuntu/+question/31430](https://answers.launchpad.net/ubuntu/+question/31430) for a post I found helpful, [http://www.hbclinux.net.nz/ubuntu804.html](http://www.hbclinux.net.nz/ubuntu804.html) for advice on configuring 8.04 on one of these laptops, and [http://www.hbclinux.net.nz/acer4315.html](http://www.hbclinux.net.nz/acer4315.html) is a list of what's wrong with the 7.10 install on these laptops (at least, as sold in New Zealand by Dick Smith) and how to fix it.

The best solution would appear to be to install 8.04 from a CD, not to upgrade. 

If I follow this route, I'll install Kubuntu, not Ubuntu, since that's what I use on my desktop. I'll probably have another fiddle with the existing OS first, so any advice on disabling ndiswrapper and getting WiFi working with madwifi-ng would be appreciated. I will need to back up some data first, and it won't recognise my usbkey since the attempted upgrade (no /dev/sdb exists). I hope it will burn a CD, otherwise I'm a bit stuck.

gadfium

---

### Post by gadfium on 2008-05-01
I'm making progress.

I booted to a command line using my old Kubuntu CD. To disable ndiswrapper, I edited /etc/modules to comment out ndiswrapper. I also edited /etc/hosts and set the hostname to the correct name - either the upgrade had reset it to ACER, or it had never been set to the hostname but that didn't previously matter.

I can now boot to 2.6.24-16, and sudo works. I still need to get the wireless card working. It appears that madwifi-ng is already installed, but the card isn't being recognised. The madwifi site is down at the moment, so I'll wait till tomorrow to tackle that.

gadfium

---

### Post by gadfium on 2008-05-04
All solved for me.

I played around with madwifi, but didn't get it working. My laptop has an Atheros AR5007 chipset, but madwifi misidentifies it as AR5006. There's a sticker on the bottom of the laptop saying AR5BXB63 which means it's an AR5007 chip. The normal madwifi driver therefore doesn't work; there's a couple of patched versions which apparently work for some people but didn't work for me. I tried the madwifi-nr-r3366+ar5007 and madwifi-ng-r2756+ar5007 drivers, and neither worked. One of them hung the kernel on reboot.

I went back to trying ndiswrapper, following the instructions at [http://www.ubuntugeek.com/howto-setup-atheros-ar5007eg-wireless-on-feisty-fawn-with-ndiswrapper.html](http://www.ubuntugeek.com/howto-setup-atheros-ar5007eg-wireless-on-feisty-fawn-with-ndiswrapper.html), and it worked perfectly. At some point, I used System->Administration->Hardware drivers to turn off support for Atheros wireless cards.

Sounds stopped working with the upgrade to Hardy Heron, but that appears to be a fairly common problem with kernel 2.6.24-16. I used the normal update service to upgrade to 2.6.24-17, and the sound started working again.

At this point, everything is working under Hardy Heron that was working under Gutsy Gibbon, as far as I am aware.

I suggest anyone with an Acer Aspire 4315-100508Ci purchased from Dick Smith electronics in New Zealand or Australia NOT upgrade to Hardy Heron unless they feel very comfortable sorting out these sort of issues, or unless they have someone who is comfortable standing by. Keep an eye on [http://www.hbclinux.net.nz/acer4315.html](http://www.hbclinux.net.nz/acer4315.html), and when they have an install CD ready, consider getting a copy and using it.

gadfium

---

### Post by gadfium on 2008-05-07
Today I did the regular update to the latest version of everything, which did not include a kernel update. At some point, possibly at the time the update finished, my wireless connection died. A reboot did not help, but doing a reinstallation of the wireless drivers followed by a reboot did. If I have to do this every few days, it's going to be a real pain.

gadfium

---

### Post by Simon Bridge on 2008-05-11
Re. 4315 + Ubuntu pre-install:
You can expect trouble with this if you upgrade to 8.04. Associated with the odd configuration choices made in the factory.

Clean install works.

See.
[www.hbclinux.net.nz/acer4315-804.html](www.hbclinux.net.nz/acer4315-804.html)

Outstanding issues are:

* Modem: Linuxant drivers kill all sound, and render the laptop unbootable - and still no dailup.

* ACPI: soft-restart and hibernate work in hardy, but suspend will still reboot instead of waking.

* Microphone: seems unstable - at first the mic worked fine (capture on the "digital" channel". However, this mysteriously stopped working - capture just produces a lot of clicks.

This is a huge improvement over Acer's "disabled due to limitations of linux" gutsy install.

---

