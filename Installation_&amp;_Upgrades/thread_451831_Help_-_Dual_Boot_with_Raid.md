---
title: "Help - Dual Boot with Raid"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by ozmaen on 2007-05-22
Hi,

I have X64 windows on my system, and would like to dual boot feisty.

The problem I have is that the feisty install cannot detect my raid configuration

I'm running my raid off of an Adaptec raid card with 2 x raptors installed. My other 3 drives all run off of my nforce sata controller on my mobo.

I have tried using the instructions for fakeraid to get this installed, but feist/fakeraid only detects the 3 drives running off of the mobo ports, and doesn't see the Adaptec raid controller.

I also tried installing feisty on one of the other drives and pointing grub to it instead of the main raid drives as an alternative, but I always got GRUB error 22 or 15 when trying that. I think that although I have pointed grub to HD(x) for the boot, the order that my bios loads up the drive withs the adaptec raid card throws the drive order out 

Any suggestions on getting this to work?

---

### Post by igloocentral on 2007-05-24
Try my debug guide: [https://help.ubuntu.com/community/FakeRaidDebug](https://help.ubuntu.com/community/FakeRaidDebug)

attach your results here in this thread.

---

