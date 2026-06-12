---
title: "Upgraded to 8.04, now gameport is not working, help!"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by harlock74 on 2008-08-11
So this is what is happening.  I upgraded my system to 8.04 and now my gamepad (Sidewinder doesn't work). It was working 100% under 7.04 - linux games, Cedega, mame, etc.

Right now if I ls /dev/input I see a js0 there. But, look at what I get when I do:

cat /dev/input/js0 
cat: /dev/input/js0: No such device

jstest /dev/input/js0
jstest: No such device

Things are loading like they were before the upgrade:

lsmod | grep gameport
gameport               16008  4 analog,sidewinder,ns558,snd_cmipci

But I don't see my gameport here:

lspci
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0c.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)


I've looked at various How-to's for gameport/gamepads, but no luck.

any ideas?  Thanks!

Note:  Gameport is in a SoundBlaster card.  Sound works 100% on system.

---

### Post by harlock74 on 2008-08-12
Can anybody help me? :(

---

