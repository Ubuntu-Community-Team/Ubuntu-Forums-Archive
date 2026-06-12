---
title: "Failed to allocate mem resources"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by halfthelaw on 2006-08-26
On attempting to boot the LiveCD, I get the error:
Failed to allocate mem resources (some numbers the fly by too quick for me to catch)
It then goes on to the mounting root filesystem step, and either hangs or gives gives caching errors on the CD drive. I've swapped out cables and drives, and removed all PCI cards to no avail. I'm on a PIII/i440BX system.
How can I fix this problem?

---

### Post by murraymints on 2006-08-27
I have the same problem when trying to boot the ubuntu live CD. I get the error message "PCI: Failed to allocate mem resource #6: 2000 @ 90000000 for 0000:01:00.0" and my system also hangs at the mounting root file system step. My system has an Intel DP965LT mainboard with a PCI adaptec SCSI AHA-2940UW card (AIC-78xx)and a PCIe x16 nvidia geforce 6500 128MB graphics card.

---

### Post by fiveseven on 2006-10-06
> **murraymints said:**
> I have the same problem when trying to boot the ubuntu live CD. I get the error message "PCI: Failed to allocate mem resource #6: 2000 @ 90000000 for 0000:01:00.0" and my system also hangs at the mounting root file system step. My system has an Intel DP965LT mainboard with a PCI adaptec SCSI AHA-2940UW card (AIC-78xx)and a PCIe x16 nvidia geforce 6500 128MB graphics card.


I have the exact (EXACT) same error message, down to the numbers, on my new rig. Runs winXP and vista Beta2 fine (running vista Beta 2 atm.) However id like to get ubuntu back on so i feel at home with the PC ;)

Running a DP965LT mobo same as you. I've heard this 965 chipset has incompatibilities that are fixed in the very lastest kernel release, but im not sure what to do. Maybe learn how to run arch or gentoo?

Any info is appreciated, for now im going to continue to scoure google...

//edit - complete system specs below, ive bolded what i think could be relevent...

CPU - Intel Core 2 Duo E6600 [conroe] EM64T @2.40GHz (stock)
**BIOS Version - MQ96510J.86A.1233.2006.0928.1318**
**Northbridge - Intel P965/G965 rev. C1**
**Southbridge - Intel 82801HB (ICH8) rev. 02**
VGA Card - NVidia Geforce 7600GT - 16x PCI-Express
**System RAM - 2x Kingston 1024MB DDR2 1.8v PC2-4300 533Mhz - 4-4-4-12 timings (Dual Channel)**
Sensor Chip - ITE F191
UPS - Poweware 5110 Line-interactive UPS (1000VA/600W)
Optical Drive - Pioneer 111D DVD+-R/RW
HDD - Western Digital WD3200JS 320GB SATA2
HDD2 (backup) - Samsung HD300LJ (300GB)
Case - Antec P150 With 92mm Nexus fan
PSU - Zalman Noiseless 360W/ATX2.2
Keyboard - MS Ergonomic 4000
Mouse - Logitec G5 Laser
Monitor - Samsung SyncMaster 205BW (20" Widescreen)

---

### Post by mrozkarol on 2006-12-07
Egzaktly the same problem.
Mobo: Intel DP965LT
Processor: Intel Core 2 Duo E6400
Memory: 2x512MB 667 GODRAM
Graphics: Gigabyte 7600GS
HDD: Seagate SATAII 250GB 16MB Cache

---

### Post by @once on 2006-12-21
Once again - same problem:
[17179570.528000] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0

Core 2 duo E6300
Intel DQ965GF Motherboard
2 GB RAM
nVIDIA GEforce 6200 
Currently running Win XP 

Since no one has yet posted a fix for this, it either does not exist, or the problem is not real. I have tried booting from 2 live CDs for Ubuntu 6.06 burn't using different burning software, resulting in the same problem. This suggested a problem with the ISO, so I also tried 6.10 (1 disc only!) with a similar (though not same) problem - i.e. the system does not boot. In the latter case it reports some tty error, whose details I have now forgotten.

Any help will be much appreciated!

---

### Post by nobo77 on 2007-02-24
hey guys i have the same exact problem, in a video i was watching earlier, they mentioned trying the alternate cd, so im going to give that a go, ill let you guys know how it goes

---

### Post by BeSerKa on 2007-02-27
Interesting, I have the Exact same message also.

- DP965LT Mobo
- Conroe E6600 Dual core @ 2.40Ghz
- 2 gigs of RAM.

Ive tried different boot parameters such as booting it as a live cd, PCI off, and various other options.

Sounds like we just have to wait until the next kernel release...

---

### Post by Opeth115 on 2007-03-03
Yes me too i have the exact same problem....

I just built myself a new computer with a DP965LT mobo and 2 ghz intel core 2 duo with a 400 gb hard drive and 2 gb ram. And for some reason whenever i boot up linux from the live cd i get these error messages:

[ 46.215450] PCI: Failed to allocate mem resource #6:20000090000000 for 0000:01:00.0

then it says type help for some list of commands and then this error message:

/Bin/sh: can't access tty; job control turned off
 
i need ubuntu for using a computer lol im not satisfied with just windows if anybody has an answer to this please post.

---

### Post by Opeth115 on 2007-03-04
> **nobo77 said:**
> hey guys i have the same exact problem, in a video i was watching earlier, they mentioned trying the alternate cd, so im going to give that a go, ill let you guys know how it goes

how'd the installation go did it work or was it a no go?

---

### Post by Arsanic on 2007-03-05
I have the exact same problem and I am trying to figure out what is wrong.My computer has passed the memtest 6 times and still nothing.I heard that it had something to do with the sata drive.Does everyone else here have a sata drive as well?

---

### Post by linuxyousertoetags on 2007-03-10
yeah sata hard drive i dont really get any errors it says ok... loading the kernel... booting.. or whatever then sits there forever then goes to a black screen i also have Intel DQ965GF dual 2.8 and 2 gigs of ram what is the deal ubuntu? i need you back

---

### Post by linuxyousertoetags on 2007-03-11
** just installed feisty fawn kernel .20 on my intel dq965gf, 2.8 dual core with 2 gigs of ram, radeon x550, 500 gb sata drive and its dual booted with windows media centre!! that is the greatest thing ive accomplished in a longgg time!!

---

### Post by Opeth115 on 2007-03-12
Could you please write a detailed descriptionj of how?  I can boot the feisty cd but the installer always freezes on me...

---

### Post by Opeth115 on 2007-03-13
Please tell us how u managed to do this because i would really appreciate it.  I;ve been trying to install different distro's forever and ubuntu, being my favorite, would really make me happy to have on my computer.

> ** just installed feisty fawn kernel .20 on my intel dq965gf, 2.8 dual core with 2 gigs of ram, radeon x550, 500 gb sata drive and its dual booted with windows media centre!! that is the greatest thing ive accomplished in a longgg time!!

---

### Post by unisol on 2007-03-13
i also receive this message but it does not affect the installation or performance of ubuntu. i asked around for about a year  and no one seems to know the cause.

---

### Post by linuxyousertoetags on 2007-03-13
all i did was booted feisty in live mode, opened gparted, then partitioned my hard drive. after that i went through the install process it took a long time then i restarted and it worked. of course i screwed it all up and now have a white screen

---

### Post by Opeth115 on 2007-03-13
how did u boot gparted form the live cd cuz that's where the sintaller keeps screwing upa s well as teh OPENsuse installer.  It always stops when trying to partition my hard drive.  and what did u do to get it to go to a white screen?

---

### Post by mickmca on 2007-03-30
I'm having the same problem with three different installer discs. The machine is a seven-year old Gateway more than adequate to the system requirements. Does anyone have a clue what's going on?

---

### Post by spectra on 2007-04-11
I'm currently experiencing this problem on my new work machine.  Spec as follows:

**CPU:** Intel Core 2 Duo E6600
**Mainboard:** Intel D975XBX2
**BIOS:** BX97520J.86A.2674.2007.0315.1546
**RAM:** 2GB Kingston 667Mhz 
**Gfx:** XFX NVIDIA 7300LE 256Mb PCI-e
**OS:** Ubuntu Edgy 6.10 x64
**Working Kernel:** 2.6.17.11
**Breaking Kernel:** 2.6.20.4

So to quickly re-iterate, all is fine until I try to run 2.6.20.4 in any config (various reconfigurations, disable mmconfig etc), then it breaks with the above error.  I e-mailed Intel from my work address, and this is the response I got:

[i]Hello Dave,                                                                                                                                                  
                                                                                                                                                             
Thank you for contacting Intel(R) Technical Support.                                                                                                         
                                                                                                                                                             
We regret to inform you that Linux* is not a supported Operating system for the Intel(R) Desktop Board D975XBX2, and Intel(R) Technical Support cannot       
provide assistance or drivers on operating systems that are not supported by the specific motherboard.                                                       
                                                                                                                                                             
Please review the following list for supported Operating systems for your Desktop Board.                                                                     
[http://intel.com/support/motherboards/desktop/sb/CS-008326.htm](http://intel.com/support/motherboards/desktop/sb/CS-008326.htm)                                                                                               
                                                                                                                                                             
We apologize for the inconvenience.                                                                                                                          
                                                                                                                                                             
Please do not hesitate to contact us again if you need further assistance.                                                                                   
                                                                                                                                                             
Sincerely,                                                                                                                                                   
                                                                                                                                                             
Jose Pablo C.                                                                                                                                                
Intel(R) Technical Support[/i]

If anyone knows of a solution, that would be good.  Not being a Developer i'm unable to try and debug the ******* myself.  Intel are obviously too busy employing useless people to care.

---

### Post by MavisPuford on 2007-07-02
I have the exact same problem.  My machine has an Intel Core 2 processor 6600.  I have tried a couple other distros even.  I'm not sure what to do.

---

### Post by bob_c_b on 2007-07-20
Add me to the chorus on this error...

Failed to allocate mem resource #6:20000@90000000, etc...

Intel DP965LTCK
C2D E6420
2x 1GB Kingston DDR2-800
Gigabyte GeForce 7600GS
Onboard Gigabit Intel NIC, Sigmatel Stac Audio
Seagate 7200.10 Sata HDD
TS-ST SATA DVD+/-RW

Install goes well, boots and runs fine so I'm guessing there is a TPM module on the board that doesn't have a Linux driver yet (some boards have been shipping with variants of these since the P865 chipsets). 

If you encounted installation failure with this error I wouldn't be too sure they are linked, might want to try the alternate CD.

---

### Post by picosam on 2007-09-27
I have the same problem too.

---

### Post by h0meb0y25 on 2007-09-28
Same problem on a Gateway desktop
Intel Core 2 Quad Q6600 processor.
I have installed 7.04 on a external HDD, funny thing is it doesnt work on my Gateway desktop but when i plug it in my IBM T60 laptop, it works like charm

Wondering whats wrong with the Gateway desktop I bought 2 weeks back :confused:

---

### Post by tessno_s on 2007-10-01
Hi from Barcelona (Spain)

You don't need use an alternative distro, you have to change a parameter in the main menu when you boot from CD.

I have selected "Install in secure graphics mode", i so have changed with F4 to 1024x7...x16 and the last thing to do is insert with F6, and before splash i have wrote: all_generic_ide

With this you will have no problems to install ubuntu (I've used 7.04 i386)

Bye, and good luck

---

### Post by Sircoelho on 2007-10-15
I'm facing the exactly same problem.

The LIVE CD cant boot, I get this message the Ubuntu continues to load and I get artefacts in my video finaly a definitive black screen

Clevo M550SE
Core 2 Duo T5300
VIA P4M900 / VN896 / VT8237A

---

### Post by h0meb0y25 on 2007-10-15
> **h0meb0y25 said:**
> Same problem on a Gateway desktop
Intel Core 2 Quad Q6600 processor.
I have installed 7.04 on a external HDD, funny thing is it doesnt work on my Gateway desktop but when i plug it in my IBM T60 laptop, it works like charm

Wondering whats wrong with the Gateway desktop I bought 2 weeks back :confused:

UPDATE:

I installed Ubuntu7.10 and problem is gone .. I am able to log into Ubuntu and replying to this message.

Hope upgrading to 7.10 help others.

Cheers.

---

### Post by starglimmered on 2007-10-16
You can force the kernel to reserve this memory so that the problem goes away. To do this, you need to have Grub pass a "reserve=" parameter to the kernel at boot time. One way to achieve this (I don't know if it's the 'correct' way) is to edit your /boot/grub/menu.lst file and locate the first "kernel" line, probably similar to this one:

```

kernel          /vmlinuz-2.6.22-14-generic root=UUID=cf003e9d-d64f-4aac-b0db-20fcf60429a7 ro quiet splash 

```

You need to add reserve parameter to that, and it should be constructed to pre-reserve the memory that is causing the errors. So for the example:

```

Failed to allocate mem resource #6:20000@90000000

```

This is telling us that 20000 bytes (hex) need to be reserved at address 90000000 (hex). This translates to a reserve parameter of:

```

reserve=0x90000000,0x20000

```

The complete kernel line would read:

```

kernel          /vmlinuz-2.6.22-14-generic root=UUID=cf003e9d-d64f-4aac-b0db-20fcf60429a7 ro quiet splash reserve=0x90000000,0x20000

```

Save the file and reboot. Voila! No more error message.

Hope that helps.
Carl

---

### Post by sinn3r on 2007-10-16
yeah I have something very similar :) >>>>
[http://ubuntuforums.org/showthread.php?t=575497]("http://ubuntuforums.org/showthread.php?t=575497")

---

### Post by matthewboh on 2008-02-08
I have the exact same problem with a clean install of 7.10

---

### Post by gotlinuxed on 2008-03-22
I have this same exact problem. I've had it since the beginning; I can't use the onboard video on my mobo, so I use an nvidia card and it doesn't seem to affect me other than that.

DG33TL compact mobo
Q6600 quad core
8 gigs ram.

---

### Post by guitarMan666 on 2008-03-22
Hmm, I get exactly the same message every time I boot (from the hard drive) and everything seems to work fine.

I'm running...

eMachines t4165
Pent IV 1.59GHz
256MB RAM
nVidia TNT w/ 32MB
probably some other things inside (net card, modem card) access the PCI buses too.  I haven't done much poking around to make sure.

---

