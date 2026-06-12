---
title: "Ubuntu on H77 chipset motherboard"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by tkwinfo on 2012-06-03
Hi,

     I have used Ubuntu for 1 - 2 years. I am now running Ubuntu 11.04 (32 bit) on a 2007 system with "core-2-due" CPU, Intel P35 chipset motherboard with 2GB memory and nVidia GeForce 8500GT display card. I have fine-tuned my Ubuntu system so that it works smoothly with my favorite applications.

     However, I am planning to buy a new computer with the following config :

Intel i5 2400,
Intel H77 chipset motherboard (ASUS P8H77-M) with 8GB ram (with SATA III and USB 3.0),
500/1T GB SATA harddisk (planning only, not yet choose the model. Perhaps WD),
nVidia GeForce GT 630 display card,

     I want to know that could my fine-tuned 32 bit Ubuntu 11.04 system be just moved to the harddisk of my new i5 2400 H77 chipset computer and it would boot up the new computer ? i.e. Could my fine-tuned Ubuntu recognizes the i5 2400, H77 chipset, SATA III, USB 3.0 etc ? If not, could I add some drivers / kernel modules to my Ubuntu system to make it work with my new computer ? (I have experience in moving Ubuntu system from one harddisk to another harddisk, but with the same CPU and motherboard.)

     Moreover, if my attempt to move my existing Ubuntu 11.04 system to the new computer fails, would the most current Ubuntu 12.04 (32 bit) system be able to be installed to my new computer with the mentioned config ?

     Thanks for any suggestion.

Regards
Lawrence

---

### Post by oldfred on 2012-06-04
You should be able to just plug in old drive and boot. Since you will still have nVidia, that should work. The two issues are video & wireless when going from one system to another.

But you really do not want to move old system to shiny new hardware. New hardware will run 64bit much better if more than 3GB of RAM. I am using 64 bit since 9.10 on my dual core Intel system. You can copy settings from /home over, but everything is now gnome3 not gnome2 based so a lot of internal settings have changed. I install the default and then only copy a few mostly other software, hidden settings from my old installs to my new install.

You also have some other new system issues but probably can ignore them as it should work in legacy or BIOS mode. New systems are UEFI but will default or allow you to set to boot in BIOS mode.

With UEFI you need to partition hard drive with gpt not MBR(msdos) partitioning. I use gpt with BIOS just because gpt is newer and slightly better than the 30 year old MBR partitioning scheme. 

The main issue I have had installing on my system is I have to use nomodeset to boot with my nVidia until I get the proprietary nVidia drivers installed.

---

### Post by tkwinfo on 2012-06-05
Hi oldfred,

     Thanks for the advices. I shall try the new system with Ubuntu in the coming few weeks. Hoping my old Ubuntu OS could be booted in the new system. I shall report any findings.

Regards
Lawrence

---

### Post by tkwinfo on 2012-06-11
Hi oldfred and All,

     I have just set up my new hardware system using i5-2500, ASUS P8H77M motherboard and 8GB ram. Wonderfully, when I plug in my old Ubuntu 11.04 (32 bit) drive, my new hardware boots OK with it. I could use my previous installed programs the same way as that in my old hardware.

     However, my old Ubuntu does not work 100% perfect with my new hardware, it seems could not see my new SATA 3 harddisk in my new system. I think it may need some tweaking before it works 100% perfect.

     Furthermore, I have tried to install Ubuntu 12.04 amd64 in the new SATA 3 harddisk in my new system. Ubuntu 12.04 amd64 seems work great with my new hardware. I am planning to slowly transfer my installed programs in the old Ubuntu 11.04 (32 bit) into my new Ubuntu 12.04 amd64 OS.

     I have tried to copy single large files (>50GB) between drives using both my old Ubuntu 11.04 (32 bit) and my new Ubuntu 12.04 amd64. The 64 bit Ubuntu 12.04 works much much faster than the 32 bit Ubuntu 11.04 (nearly 24 hours vs 24 minutes for the copy time !).

     As my new SATA 3 harddisk is only 1T (< 2T), I have used the old MBR partition scheme for my new harddisk and leave the GPT partition scheme for the next upgrade of my software and hardware.

     Thanks Ubuntu and helpful people in this forum.

Regards
Lawrence

---

### Post by ianp5a on 2012-10-12
Regarding trasferring your software.
Excuse me if you already considered this but you can automatically transfer one or any number of your old apps using the File->Sync function in the Software Manager.
In your old system, be sure to use this File->Sync function. Then in the new setup you will see a list of the apps in your old system under File->Sync. Pick any that you want install in the new one and it will do it all for you.

---

