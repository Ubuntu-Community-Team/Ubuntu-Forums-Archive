---
title: "Moving to New machine"
date: 2021-02-06
forum: Installation &amp; Upgrades
---

### Post by werth.clinton on 2021-02-06
I am just getting into linux,  so I bought an old $50 dell poweredge T110. I just have one 4tb drive running Ubuntu. Well know I want to learn more,  so I bought a clean dell T320 so I could play around with more ram and virtual machines. 

Anyways, I removed the hard drive from my old machine, put it into the new one and I'm getting "No boot device available". I thought it would just boot up right away, but it seems I'm missing something.  Thanks for your help

---

### Post by SeijiSensei on 2021-02-06
Look in the BIOS and make sure the drive is marked as the boot device.

---

### Post by werth.clinton on 2021-02-06
So that makes sense,  buy i don't see a drive option. In the bios boot manager I see 3 options: 
Normal
HL-DT-ST DVD+/RW GHBON
EMBEDDED NIC 1 BRCM MBA SLOT 0100 V20.2.0

I've been looking for a different bios menu but this is all I find

**Update - I went through the dell lifecycle controller  and found a system bios settings with Boot settings and a BOOT sequence. 
under boot sequence I only have 2 options:
1. Embedded SATA Port Optical Drive E: HL-DT-ST
2. Embedded NIC 1Port 1Partition 1: BRCM MBA Slot

there is a section for Hard-Disk Drive Sequence, but it's greyed out

---

### Post by Impavidus on 2021-02-07
BIOS of UEFI? If the old computer was from 2012 or before, it was probably booting using bios. The OS would be installed in bios mode. The new computer may be using uefi. You could try setting it to legacy mode (which emulates bios), or fresh install Ubuntu.

---

### Post by CelticWarrior on 2021-02-07
I think Impavidus in on the right track but the situation is likely to be the other way around. A D[COLOR=#000000]ell Poweredge T110 is a very old server being sold at eBay for as little as &#8364;75.

Plus it has RAID controllers. Just transplanting a drive with Ubuntu installed won't work. Drives must be configured before installing Ubuntu.[/COLOR]

---

### Post by werth.clinton on 2021-02-07
Thanks for the reply. So I checked and it is booting with bios. I think you're on to something with configuring the drivers. 
I believe my issue is that the hard drive is not being recognized.  I put a blank drive in and put a USB with the Ubuntu iso to just try a wick install and see what's up. 
The machine read the usb drive and started the install,  but then it failed because it said no drive was detected.
I then connected my hard drive via an external USB driver dock. And it seems to try booting, but I get this rescue grub command line.

---

### Post by oldfred on 2021-02-07
Do you have this now obsolete video?

The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)
[https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0](https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0)

---

### Post by SeijiSensei on 2021-02-09
Certainly looks like the drive is not being recognized by the system. Have another cable? Another free SATA port?

---

### Post by werth.clinton on 2021-02-09
Well you're all going to love this. I opened up the case. Checked everything out and found that the h310 perc card was not inserted into the mother board. Inserted it in and now I'm good to go. 
Thanks again event

---

