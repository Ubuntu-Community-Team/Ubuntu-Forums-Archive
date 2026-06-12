---
title: "laptop drivers"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joelswatson on 2009-03-24
hi,

i been on google again, and this time with luck.

ive been looking for a linux driver database, or just looking for linux drivers for my laptop, but all i can find atm, is my nvidia driver (no surprise there)

can anyone help me

ive got a acer aspire 7720g laptop

thanks

---

### Post by Sprut1 on 2009-03-24
> **joelswatson said:**
> hi,

i been on google again, and this time with luck.

ive been looking for a linux driver database, or just looking for linux drivers for my laptop, but all i can find atm, is my nvidia driver (no surprise there)

can anyone help me

ive got a acer aspire 7720g laptop

thanks

What drivers do you need? What is not working? What is working?

---

### Post by joelswatson on 2009-03-24
heya these are the ones im looking for ubuntu 9.04 64bit

avermedia a310
  AVerMedia DVB-T BDA Video Capture(A310)

intel wireless wifi link 4965agn
  Intel(R) Wireless WiFi Link 4965AGN Drive

broadcom netlink gigabit ethernet
  BCM5786
  BCM5787M
  BCM5787

hdaudio soft data fax modem with smartcp
  Capabilities:  Soft Data Fax Modem with SmartCP      
  Controller:    CAXHWAZL                                 
  Daa Type:      SMART                                     
  Codec:         LSD                                      
  Hardware type: ICH  

ricoh ohci compliant ieee1394 host controller


ricoh memory / sd/mcc /xd-picture card controller (5 in 1)
  RICOH R5C83x/84x Flash Media Controller Driver

ENE CIR Receiver

thanks

---

### Post by overdrank on 2009-03-24
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by jmmL on 2009-03-24
So you've actually installed jaunty? Or are you just looking around before making the leap?

Your intel 4965agn should work out of the box (mine does, and always has)
I'd be very surprised if your ethernet didn't as well; I've heard bad things about broadcom's wireless drivers (although I've also heard these are now fixed), but nothing about their wired ones, so I assume all is fine there.

I think I have the same ricoh card reader as you, and although I've personally never tested it, someone with the same model laptop as me said that it works fine for SD and MMC cards, but has issues with xD cards.

---

### Post by joelswatson on 2009-03-24
hi,

nah i havent installed ubuntu 9 yet, cause im waiting for it to come out of alpha phase, and become a full release, so i am just looking around for some games / apps i will want to run, and some device drivers,
the main 2 drivers i am looking for is the avermedia driver (for my hd tv turner) and the broadcomm wifi driver, cause i dont have physical access to my 2 access points, as they are both in the roof, so before i install ubuntu 9 i would want to have the driver, any other devices that dont work after the install will be ok, cause i will have a dual boot system set up with vista ultimate and as long as the wifi is driving, i can hunt down the drivers on google.

does anyone know of a site or ftp server that has a database of linux drivers (like [www.driverguide.com](www.driverguide.com) for windows drivers)

thanks

> **jmmL said:**
> So you've actually installed jaunty? Or are you just looking around before making the leap?

Your intel 4965agn should work out of the box (mine does, and always has)
I'd be very surprised if your ethernet didn't as well; I've heard bad things about broadcom's wireless drivers (although I've also heard these are now fixed), but nothing about their wired ones, so I assume all is fine there.

I think I have the same ricoh card reader as you, and although I've personally never tested it, someone with the same model laptop as me said that it works fine for SD and MMC cards, but has issues with xD cards.

---

### Post by joelswatson on 2009-03-24
heya,

i have found this driver, from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) can anyone comfirm that it is the correct working driver for my wifi card under linux?

thanks

---

### Post by RAOF on 2009-03-24
It is not.

The reason why you won't find any database of linux drivers like driverguide.com is because all the drivers are included in the kernel.

Basically, you don't ever need to worry about installing drivers (with the possible exception of some non-free drivers, for which you'll want to check System->Administration->Hardware Drivers).  

Either you already have the drivers you need, or those drivers don't exist yet (or, sometimes, aren't stable yet).

---

### Post by inportb on 2009-03-24
Indeed. Or if you want us to do some digging for you, you might want to run a live session and post us the output of *lspci*. This has the added benefit of letting you try Ubuntu too.

> **joelswatson said:**
> nah i havent installed ubuntu 9 yet, cause im waiting for it to come out of alpha phase

The release that you speak of is Ubuntu *9.04*, not Ubuntu 9, not Ubuntu 9.4.

---

### Post by joelswatson on 2009-03-24
> **inportb said:**
> Indeed. Or if you want us to do some digging for you, you might want to run a live session and post us the output of *lspci*. This has the added benefit of letting you try Ubuntu too.



The release that you speak of is Ubuntu *9.04*, not Ubuntu 9, not Ubuntu 9.4.

heya,

lol, yeh i know its not 9, but 9.04, i was too lazy to put in the .04 cause people would know what i was talking about.

but ill runt aht lspci when i get home from work, and post my results.

thanks

---

### Post by inportb on 2009-03-24
The reason I mentioned *lspci* is that it tends to be a lot more specific than marketing names ;)

---

### Post by joelswatson on 2009-03-25
heya, cheers for everyone's help, but stupid question, how do i run the lspci command?

do i just open a terminal windows and type lspci? or do i have to do something else?

i know bits about linux but not heaps,

thanks

joel

> **inportb said:**
> The reason I mentioned *lspci* is that it tends to be a lot more specific than marketing names ;)

---

### Post by nystire on 2009-03-25
Yes, opening a terminal and running the command should work :)

---

### Post by joelswatson on 2009-03-25
ok cool, ill do it when i get home from work, and post the results, (2 1/2 hours)

thanks

---

### Post by joelswatson on 2009-03-25
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
ubuntu@ubuntu:~$ lspci

---

### Post by scaine on 2009-03-25
I don't see your Avermedia device in there.  I take it this is an Acer laptop with the A310 built in?  I don't think anyone has produced a driver for that model, but I'll have another hunt and see what I can find.  TV tuner cards often require a couple of files to be copied to /usr/share/firmware (or is it /lib/firmware?) before they are recognised.  I had to do so for my USB Nova TV tuner.

EDIT :
Right, it looks like you're definitely out of luck with the A310 :
[http://www.minihowto.org/linux_help_howto/data/20071118142443/index.html](http://www.minihowto.org/linux_help_howto/data/20071118142443/index.html) outlines that drivers have not been written for this device yet, although I'm not sure how up to date that site actually is.

And [http://www.linuxtv.org/wiki/index.php/AVerMedia](http://www.linuxtv.org/wiki/index.php/AVerMedia) outlines that the A310 isn't supported by the standard linux DVB drivers project and that AverMedia themselves don't provide any linux support (other than for one of their products, and even then with license restrictions).

Sorry.

EDIT 2 :
[http://ubuntuforums.org/showthread.php?t=421110](http://ubuntuforums.org/showthread.php?t=421110)

You never know, adding those drivers that are attached at the bottom of the first post *might* get you up and running.  But it's a long-shot...

---

