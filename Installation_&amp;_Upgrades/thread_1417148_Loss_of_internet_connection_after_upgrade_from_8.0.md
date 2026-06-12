---
title: "Loss of internet connection after upgrade from 8.04 to 8.10"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by lukon on 2010-02-26
Loss of internet connection after upgrade from 8.04 to 8.10

Like the title says, I lost my internet connection after upgrading my Ubuntu system from 8.04 to 8.10.

I used the downloaded automated method. It appeared to work fine on its initial reboot into 8.10. But I noticed the internet icon indicated loss of connection. Even so, I was still able to browse the net through Firefox. But then when I rebooted the next day the opposite was true: the connection icon indicated connection, but Firefox would not actually connect, nor would update manager. It has been like this since.

This is a dual boot machine, and the Windows XP Pro side still connects to the internet as usual, no problems.

So how can I make my new 8.10 system connect to the internet?

Here's more info:

I use a Motorola SB4200 cable modem
([http://broadband.motorola.com/consumers/products/sb4200/default.asp](http://broadband.motorola.com/consumers/products/sb4200/default.asp))
and a Belkin F5D5230-4 router 
([http://www.belkin.com/ca/support/article/?lid=enc&pid=F5D5230-4&aid=12912&scid=220](http://www.belkin.com/ca/support/article/?lid=enc&pid=F5D5230-4&aid=12912&scid=220)).

Computer is an HP DC5000 SFF
([http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML](http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML))
CPU: Pentium 4 2.4Ghz
RAM: 2G
OS Loader: GRUB
Primary IDE 0: Windows XP "C" / Ubuntu "SDA"; Windows XP system; 46.1GB IBM-307045
Primary IDE 1: Ubuntu "SDB"; Ubuntu system; 15.3GB Maxtor 31536H2
Secondary IDE 0: Windows XP "I" / Ubuntu "?"; DVD drive; Sony DVD RW DRU-720A
Secondary IDE 1: Windows XP "J" / Ubuntu "?"; DVD drive; TSSTcorp CDDVDW SH-S202G
PCI SATA/IDE Disk controller board: Masscool XWT-RC018 with VIA Tech BIOS Ver 4.90
([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501402&CatId=1455](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3501402&CatId=1455))
SATA port 0 Master: None
SATA port 1 Master: Windows XP "E" / Ubuntu "SDC"; Windows XP data; 465.76GB WDC WD5001AALS-0
IDE port 0 Master: Windows XP "D" / Ubuntu "SDD"; Windows XP data; 298.09GB Hitachi HDT72503
IDE port 1 Slave: None

---

### Post by jimmysheldon on 2010-04-13
I'm having a very similar problem.

Upgraded from 8.04 to 8.10 in the same automatic way. When i restarted there was no network connection  sign, and i couldnt connect to the internet with firefox/update manager etc

i also have a belkin wireless router though. Were you running your drivers through ndiswrapper? I feel thats where the problem is. Although my drivers show up in ndiswrapper, as does the hardware. They just dont seem to be coming together to actually give me internet.

Any help would be greatly appreciated. Cheers.

---

### Post by jimmysheldon on 2010-04-14
..i rebooted and then it worked again. Very frustrating indeed.

---

