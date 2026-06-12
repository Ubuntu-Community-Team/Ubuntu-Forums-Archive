---
title: "Ubuntu Installer Freezes On Install!"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by dhav211 on 2005-04-08
Well I just downloaded Ubuntu Hoary Hedgehog Final today and I put in the install CD, restart the computer and after it to find my network or something it just stops, the screen is all blue. On my parent's computer it keeps going on and says something like "Configuring Network with DHCP" or something like that. Anyways I got the Warty install X86 CD and tried to boot that and that got past that part.

Anyways here are some of my parts in my computer if you need it...

Pentium 4 3.20 GHz
250 GB Sata HDD (sorry don't have much other info on it)
Intel(R) 82915G/GV/910GL Express Chipset Family (I think thats my GFX Card)
1 GB ram
Any other parts I should post just ask.

Also the ubuntu logo, when you put in the installer cd, is all mess up on my computer but its perfect on my computer.

Thanks!

---

### Post by Seattle_Mike on 2005-04-08
I think I have the same problem as you so I'm joining you.  Ubuntu 5.04 install crawls very slowly while installing and freezes when partition chooser question appears (56%).

My computer: P4 2.4 GHz, 1Gig ram, 2 x 120GB SATA Seagate ICH5,
60 Gb Maxtor ATA ide, 80 Gb Maxtor USB, ATI Radeon 9200 64Mb 
display card, Hauppauge TV Card. 

In my case it's not critical to install (I have installed Ubuntu with Kubuntu on my PIII backup computer) but would like to install
it on the above system. 

Thanks for support and big thanks for providing such a fine 
distribution.

---

### Post by dhav211 on 2005-04-08
[QUOTE=Seattle_Mike]I think I have the same problem as you so I'm joining you.  Ubuntu 5.04 install crawls very slowly while installing and freezes when partition chooser question appears (56%).

My computer: P4 2.4 GHz, 1Gig ram, 2 x 120GB SATA Seagate ICH5,
60 Gb Maxtor ATA ide, 80 Gb Maxtor USB, ATI Radeon 9200 64Mb 
display card, Hauppauge TV Card. 

In my case it's not critical to install (I have installed Ubuntu with Kubuntu on my PIII backup computer) but would like to install
it on the above system. 

Thanks for support and big thanks for providing such a fine 
distribution.[/QUOTE]
 Appears this person has the same problem as you, Seattle_Mike, [http://ubuntuforums.org/showthread.php?t=24978&highlight=sata](http://ubuntuforums.org/showthread.php?t=24978&highlight=sata)

His question never got answered.

---

### Post by Seattle_Mike on 2005-04-09
dhav211 - I see the other problem but still think you are the closest.
I presume that you are running the ICH5 SATA support but you can
verify that (Are you running WINDOWS also?) by looking at System
Control/Device manager to determine the SATA chipset.  If you are
not running Windows run a self-boot Knoppix, Gnoppix where you can issue a 
"dmesg | more" from a root prompt to see what you have. 


For any Ubuntu system folks reading this thread:
On my configuration above, I have installed (WinXP, WIN2K) and am
running a Debian SID partition (my working main system) using a kernel Gnoppix 2.4.21-cdv which has been an lifesaver for my ability to run linux ... Thank you very much Gnoppix folks! My motherboard is an ASUS P4P800 with integrated ICH5 SATA.  (This is one of the earliest SATA support systems). 

I have tried desperately to roll my own kernel (2.4 or 2.6) without success. 

Would it help if I remove the 60Gb ATA ide and the 80Gb USB leaving only the 2 ICH5 SATAs and then install Ubuntu?

At the risk of making too long an entry - here is my dasd listing from a dmesg on my 2.4.21-CDV boot:
Uniform Multi-Platform E-IDE driver Revision: 7.00beta4-2.4
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 00:1f.1
PCI: Enabling device 00:1f.1 (0005 -> 0007)
ICH5: chipset revision 2
ICH5: 100% native mode on irq 18
    ide0: BM-DMA at 0xef90-0xef97, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0xef98-0xef9f, BIOS settings: hdc:DMA, hdd:DMA
ICH5-SATA: IDE controller at PCI slot 00:1f.2
ICH5-SATA: chipset revision 2
ICH5-SATA: 100% native mode on irq 18
    ide2: BM-DMA at 0xeeb0-0xeeb7, BIOS settings: hde:DMA, hdf:pio
    ide3: BM-DMA at 0xeeb8-0xeebf, BIOS settings: hdg:DMA, hdh:pio
hdb: Maxtor 6Y060P0, ATA DISK drive

---

### Post by dhav211 on 2005-04-15
[QUOTE=Seattle_Mike]dhav211 - I see the other problem but still think you are the closest.
I presume that you are running the ICH5 SATA support but you can
verify that (Are you running WINDOWS also?) by looking at System
Control/Device manager to determine the SATA chipset.  If you are
not running Windows run a self-boot Knoppix, Gnoppix where you can issue a 
"dmesg | more" from a root prompt to see what you have. 


For any Ubuntu system folks reading this thread:
On my configuration above, I have installed (WinXP, WIN2K) and am
running a Debian SID partition (my working main system) using a kernel Gnoppix 2.4.21-cdv which has been an lifesaver for my ability to run linux ... Thank you very much Gnoppix folks! My motherboard is an ASUS P4P800 with integrated ICH5 SATA.  (This is one of the earliest SATA support systems). 

I have tried desperately to roll my own kernel (2.4 or 2.6) without success. 

Would it help if I remove the 60Gb ATA ide and the 80Gb USB leaving only the 2 ICH5 SATAs and then install Ubuntu?

At the risk of making too long an entry - here is my dasd listing from a dmesg on my 2.4.21-CDV boot:
Uniform Multi-Platform E-IDE driver Revision: 7.00beta4-2.4
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH5: IDE controller at PCI slot 00:1f.1
PCI: Enabling device 00:1f.1 (0005 -> 0007)
ICH5: chipset revision 2
ICH5: 100% native mode on irq 18
    ide0: BM-DMA at 0xef90-0xef97, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0xef98-0xef9f, BIOS settings: hdc:DMA, hdd:DMA
ICH5-SATA: IDE controller at PCI slot 00:1f.2
ICH5-SATA: chipset revision 2
ICH5-SATA: 100% native mode on irq 18
    ide2: BM-DMA at 0xeeb0-0xeeb7, BIOS settings: hde:DMA, hdf:pio
    ide3: BM-DMA at 0xeeb8-0xeebf, BIOS settings: hdg:DMA, hdh:pio
hdb: Maxtor 6Y060P0, ATA DISK drive[/QUOTE]


Sorry for not replying to this thread.

Anyways, yes I am running Windows XP on this computer and I can get Fedora Core 3 running (no sound though). So far Fedora Core 3 is the only linux distro I've had any luck with on this computer.

---

### Post by kleeman on 2005-04-15
I had exactly the same problem: The installer and livecd would always freeze when the network was being configured for dhcp. I lodged a bug report on this at

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6142](https://bugzilla.ubuntu.com/show_bug.cgi?id=6142)

The cause in my case was that I had an Intel onboard network card (Yukon gigabit) the module of which (sk98lin) is broken in the present hoary kernel (It works fine for warty). If this is your problem it can be solved by downloading the driver patch from the vendor (see bug report) and executing their script (easy). Of course this is hard if you can't boot into your system ;-). To get around this I installed warty and then upgraded to hoary via the usual procedure (see the howto on this forum). I then executed the script BEFORE rebooting.

---

### Post by ipggi on 2005-05-13
I was having a simular problem as you guys with the install grinding to a halt on a P4P800 MB. My solution was to do a simple flash of my motherboards BIOS to the most recent available version. After that everything worked without a hitch.

[Go here to grab the ASUS Windows BIOS update program](http://www.asus.com.tw/support/download/selectftp.aspx?l1_id=1&l2_id=11&l3_id=0&m_id=1&f_name=Asusupdt60501.zip~zaqwedc)

[Then go here and select your exact motherboard.](http://www.asus.com.tw/support/download/download2.aspx?item=p4p800&type=like&file_type=All)
Then you will see a list of drivers and BIOS revisions as well as a DOS updater if you prefer using that (for a boot cd or floppydisk).

Hope this helps..

---

