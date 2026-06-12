---
title: "Asus M3A78-T drivers"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Kuraboy on 2008-10-30
Hi!

First of all, I am very happy that Ubuntu 8.10 worked out of the box for my system with graphics, ethernet and sound working directly or by just accepting a non-free drivers. (My system AMD Phenom X4 9950 BE, the above mentioned motherboard with integrated GPU).

That dose not happen for WinXP. I needed to insert CD to install drivers and reboot 3 times!!!

So I am very happy and would like to thank the whole open-source community and especially the Ubuntu guys :D

I have only one question: 
Asus have just released Linux drivers for my motherboard, are they better than the shipped ones? Or are they the same drivers?

here is a link for the drivers, just choose Linux when it asks for OS type:

[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3A78-T](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=M3A78-T)

---

### Post by lemming465 on 2008-11-01
Vendor drivers are usually older than what Ubuntu or Fedora are running.  If things are working, I'd avoid them.  BIOS updates might be worth considering, however.

---

### Post by sunoccard on 2008-12-25
i just got this MOBO updating the BIOS isn't necessary unless you run into trouble, i wouldn't touch it if things are running smoothly.

---

### Post by yther on 2009-01-18
OK, I realize this thread was originally started a few months ago, but to you folks who have this board, how's your experience been so far?

I'm planning on building a system based on this with an eye to being affordable now and upgradable in the future, so for example:

[list=][*][This board]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131331") (link to NewEgg if you want the gritty details)
[*]8GB memory (2x 4GB), leaving 2 slots for upgrade to 16GB later
[*]Inexpensive HDD for system, 2x slightly more expensive HDDs for all my data, in a RAID setup providing about 1TB redundant storage
[*]Quad core processor if I can afford it (reviews have said the Phenom II can be used but requires a BIOS update, however I wouldn't be able to do that without another processor on hand)
[*]Cooler Master Cosmos 1000 case[/list]

System will be used for hosting one or two virtual machines running WinXP for a couple of games, plus either WINE or another VM for OCR projects using FineReader.  (It's nice to be able to background OCR of a 1,000-page book and go play!)  Also normal multimedia use, Linux-based games such as Civ:CTP, DVD burning & viewing, possibly format conversion as well.  As usual, in the future I'll probably want to do more than I imagine now, so that's why I want a system that can be expanded later.  :)

My only concern right now is the on-board ATI graphics.  I'd rather have NVIDIA, but the boards I found with those chipsets don't seem to be as good.  Could anyone speak of their experiences with the ATI Radeon HD 3300?  Any difficulties?

Thanks for any feedback!

---

### Post by BryKKan on 2009-04-20
I can't say I know anything about ubuntu (I got linked here because I wanted to try it on my new build, and was concerned about drivers), but I do have a similar hardware config to what you posted. From what I've read, the Phenom IIs are recognized on BIOS version 0502 and up (they're on 0802 now), and that even the prior versions will boot with them with enough funcionality to flash the BIOS. I'm waiting on my RMAed hard drive to come in tomorrow before I bother to test it, so I'll post again tomorrow after I try it out.

---

### Post by SR_ELPIRATA on 2009-04-21
I have a M3A78-T board too. It has been working great on this end. I installed the Ubuntu ATI drivers (restricted drivers section) and sometimes I get windows slowly redrawn, but since this is not a clean install (rather Im using a drive I was using before with a nvidia card and chipset).

I'm running a x2 7750 2.7, with just 2 gigs of ddr2 800 and what can I say, it runs nice. Tested some 1080p demo I have and at first ran it with 60% usage on both cores, but after the ATI driver is now to 20% and 60% on the other.

I have some VMs set but I dont use them often so I cant help you with that.

BTW, not sure if you guys noticed, but the amd/ati site doesnt have separate drivers for the built in HD3300.

ELP:)

---

### Post by vivedekananda on 2009-04-23
> **SR_ELPIRATA said:**
> 
BTW, not sure if you guys noticed, but the amd/ati site doesnt have separate drivers for the built in HD3300.


Look under integrated/motherboard.

---

### Post by caveman59330 on 2009-04-23
I originally bought my Asus M3a78-T last August and have not had any seriuos problems I did update the Bios version to 0902 and have noticed Asus puts out Bios updates for it very often. The problems I have had are minor like it freezes up the Post during discovery of USB devices when I have my UPS hooked up via USB but whateve. I have not gotten to overclock to anything over 2,9 without becoming unstable but it has enough power so it is mostly for fun. heres the specs incase anyone is interested.

Apevia X-Cruiser Black ATX Mid Tower Case[B]
Arctic Cooling Low Profile 60 MM CPu Fan 
[/B]AMD Phenom 9950 2.6 GHz Black Edition 140 W Quad Core Processor
Mushkin XP 4 GB Ascent with eVCI Technology 240 pin DDR2 SDRAM 1066 PC28500
RAIDMAX HYBRID 2 RX-630SS 630W  SLI Ready CrossFire Ready Modular LED Power Supply
H.I.S Radeon X850 XT 256 MB Quad Channel GDDR3 With IceQ II Cooling Technology
Seagate 640 GB 7200 RPM Sata 3 32 MB cache HDD
Western Digital 500 GB 7200 RPM Sata 3 16 MB Cache HDD
SimpleTech 1 TB Turbo USB external HD
2 Masscool  Hard Drive Cooling fans with Dual 50 MM fans one for each HDD
LG 22x Sata 3 DVD +R Burner 
Apevia x2 120 MM Fans  Blue one on front and other on back for case cooling 
Apevia x2 80 MM  Fans Blue one on top and other is side fan again for case cooling
TrippLite Smart 1000 LCD UPS

---

### Post by caveman59330 on 2009-04-23
I originally bought my Asus M3a78-T last August and have not had any seriuos problems> I did update the Bios version to 0902 and have noticed Asus puts out Bios updates for it very often. The problems I have had are minor like it freezes up the Post during discovery of USB devices when I have my UPS hooked up via USB but whateve. I have not gotten to overclock to anything over 2,9 without becoming unstable but it has enough power so it is mostlyy for fun. heres the specs incase anyone is interested.

Apevia X-Cruiser Black ATX Mid Tower Case[B]
Arctic Cooling Low Profile 60 MM CPu Fan 
[/B]AMD Phenom 9950 2.6 GHz Black Edition 140 W Quad Core Processor
Mushkin XP 4 GB Ascent with eVCI Technology 240 pin DDR2 SDRAM 1066 PC28500
__RAIDMAX HYBRID 2 RX-630SS 630W  SLI Ready CrossFire Ready Modular LED Power Supply
H.I.S Radeon X850 XT 256 MB Quad Channel GDDR3 With IceQ II Cooling Technology
Seagate 640 GB 7200 RPM Sata 3 32 MB cache HDD
Western Digital 500 GB 7200 RPM Sata 3 16 MB Cache HDD
SimpleTech 1 TB Turbo USB external HD
2 Masscool  Hard Drive Cooling fans with Dual 50 MM fans one for each HDD
LG 22x Sata 3 DVD +R Burner 
Apevia x2 120 MM Fans  Blue one on front and other on back for case 
Apevia x2 80 MM  Fans Blue one on top and other is side fan 
TrippLite Smart 1000 LCD UPS

---

### Post by SR_ELPIRATA on 2009-04-29
> **vivedekananda said:**
> Look under integrated/motherboard.

Thanks, Im downloading the driver right now :)

Any of you ran the super_pi test that was on the Community Cafe section?

I ask because I read some then and noticed that my Black Edition had a better score than many Phenoms and I couldnt figure out why.

ELP

---

### Post by Mark Phelps on 2009-04-29
> **Kuraboy said:**
> I have only one question: 
Asus have just released Linux drivers for my motherboard, are they better than the shipped ones? Or are they the same drivers?
The Linux support drivers are simply ATI video and realtek audio.  

If your video and audio are working OK, I would leave well enough alone.

---

### Post by SR_ELPIRATA on 2009-05-01
Well downloaded them windows drivers and got the same behaviour than with the Asus DVD... after reboot resolution/colors get screwed up and catalyst says that its incompatible or something. I wonder if I'm the only one with this behaviour.

I did a roll back and its working fine with I guess a driver for a similar ATI card.

ELP

---

### Post by SR_ELPIRATA on 2009-06-03
Btw, what linux version drivers are you guys using? I used envyng and says that my current 8.543 are both the compatible and recommended, but I've seen the ati.amd site that says there's a 9.5 version, I was wondering if any of you tried them on Ubuntu.

ELP

---

