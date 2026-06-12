---
title: "AuzenTech X-Fi Forte 7.1 x86 Driver Install Error"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by jeremyofmany on 2010-07-08
I am new to Ubuntu/Linux.
I have the X-Fi Forte 7.1.
According to this page:
[http://www.alsa-project.org/main/ind...ndor-AuzenTech]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-AuzenTech")
It is unsupported by the ALSA SoundCard Matrix.

I am running Ubuntu 10.04 AMD x64 Desktop.
I installed Wine 1.0.1 (latest stable).
I launched the installation through Wine.  This is what happened:

> 
 Unhandled Exception
Error Number: 0x80020005
Setup will now terminate.This error message appeared just as the InstallShield Wizard was  finishing preparation.

I am currently back in Windows so I am unable to provide any debug  information.
Any ideas on how I could get my sound card driver installed?
If I'm currently SOL, let me know.


Cheers,
Jeremy

---

### Post by Mark Phelps on 2010-07-09
You can't install device drivers through Wine; so, there's no point in trying.

Wine uses specially-written "DLLs" that translate MS Windows system calls into Linux system calls, enabling you to run SOME MS Windows programs.  But it still uses the standard Linux device drivers, not MS Windows device drivers.

I'm using the bluegears B-enspirer 7.1 sound card in Ubuntu 10.04 and it uses the same chipset as some of the Auzentech cards.  So, your card might work with the default sound drivers.

Also, you could Google for OSS (Open Sound).  They had Linux drivers for my card long before ALSA finally incorporated them.

---

### Post by jeremyofmany on 2010-07-10
> **Mark Phelps said:**
> I'm using the bluegears B-enspirer 7.1 sound  card in Ubuntu 10.04 and it uses the same chipset as some of the  Auzentech cards.

I Googled your sound card and it uses  the C-Media chipset which is supported by ALSA.  The Forte uses the  emu20k2 chipset which is not supported according to the Wiki site I  linked to above.

> **Mark Phelps said:**
> So, your card might work with the default  sound drivers.

If that were the case, my sound would  work out of the box like my Ethernet does.
My sound does not work.
When  I check for drivers, nothing for my sound card appears.

> **Mark Phelps said:**
> Also, you could Google for OSS (Open  Sound). They had Linux drivers for my card long before ALSA finally  incorporated them.

I registered and posted on the OSS Forum.  Even they could not tell me for certain whether their driver would work with my card.

During my attempt to install the driver, the Console in Ubuntu when pressing Alt-Ctrl-F1 just gives me an empty black window.  It no longer prompts for my credentials.

I have removed Ubuntu from my system.  I realize it is not Ubuntu's fault for not working with my sound card - it is the manufacturer's for not designing a Linux-compatible driver.


Cheers,
Jeremy

---

### Post by bcschmerker on 2010-07-11
> **jeremyofmany said:**
> I am new to Ubuntu/Linux.
I have the X-Fi Forte 7.1.
According to this page:
[http://www.alsa-project.org/main/ind...ndor-AuzenTech]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-AuzenTech")
It is unsupported by the ALSA SoundCard Matrix....

I am currently back in Windows so I am unable to provide any debug  information.
Any ideas on how I could get my sound card driver installed?
If I'm currently SOL, let me know.


Cheers,
JeremyIn fact, [Creative Technology, Limited](http://www.creative.com/), has been uncooperative with the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) concerning drivers (snd-emu20k2) for the Creative® CA20K2-series PCI-Express audio chips under LinUX, and development of the driver is therefore at a standstill.  I am still, for this very reason, running Creative's older SB0350 Sound Blaster® Audigy 2™ ZS (snd-emu10k2, for CA0102 chipset) on my hybrid Everex® mid-tower (upgraded to an all-AMD® rig using the Gigabyte® MA78GM-S2HP with Advance Micro Devices® Athlon™ X2 5800+ MPU) under Ubuntu® 10.04-LTS; and plan to reserve an [Auzen® X-Fi Forte 7.1](http://www.auzentech.com/) (CA20K2 chipset, unsupported in LinUX as of July 2010) for my [eMachines®/Acer® EL1210-09 slimline](http://www.emachines.com/) (running Microsoft® Windows™ 6.0.6002 as of July 2010) on account of this driver availability issue.

---

### Post by bcschmerker on 2011-02-21
> **bcschmerker said:**
> In fact, [Creative Technology, Limited](http://www.creative.com/), has been uncooperative with the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) concerning drivers (snd-emu20k2) for the Creative® CA20K2-series PCI-Express audio chips under LinUX, and development of the driver is therefore at a standstill....
Update:  As of February 2011, the [eMachines®/Acer® EL1210-09 slimline](http://www.emachines.com/) is down for a failed controller board on the stock Hitachi® hard disc drive, and therefore since replaced by an [Asus® CM1630-06](http://usa.asus.com/) running [Microsoft® Windows® 7.0.8001](http://windows.microsoft.com/).  I am not switching my Everex® (running Ubuntu® 10.04.2-LTS) from the Creative® SB0350, as the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) has made only limited headway in supporting basic multichannel sound on the Creative® CA20K2 PCI-Express x1 audio chip; should I get a CA20K2-based audio card, it is better supported on the CM1630-06 on account of Creative Technology's supporting the CA20K2 only under Microsoft® Windows XP and 6-up.

---

