---
title: "Dual booting on an Acer Aspire 1 A114-32-C1YA"
date: 2018-12-30
forum: Installation &amp; Upgrades
---

### Post by meshica7 on 2018-12-30
Hello all

Here's hoping that everyone is having a splendid holiday season.
I recently purchased an Acer Aspire 1 A114-32-C1YA which I intend to interface with my Line 6 Helix effects processor (as of yet there is no Linux support for the editing software for this unit). I am running Ubuntu 18.04.1 on an old Macbook Pro and it runs a little sluggish at times so I was planning on dual booting the Acer. The Acer has Windows 10 S pre-installed and I will be upgrading to the Home edition (apparently it's the only way to download and run non Microsoft Store software). This is actually my 1st foray into the world of Windows aside from using a PC at work. The full Windows wipe and Ubuntu install seems like a fairly straight ahead procedure, but I have no clue as to a dual boot. Is it fairly easy? And if so (or if NOT) could someone point me to an online tutorial written for non Windows folk? I appreciate everyone's time and consideration!
[https://line6.com/helix/]("https://line6.com/helix/")
[https://www.acer.com/ac/en/US/content/model/NX.GVZAA.003]("https://www.acer.com/ac/en/US/content/model/NX.GVZAA.003")

---

### Post by ubfan1 on 2018-12-30
Take a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  There may be Acer specific workarounds for vendor non-UEFI mods, but try a straight install first.  Without special hardware like Nvidia, even leaving secure boot enabled should work.

---

### Post by oldfred on 2018-12-30
What are actual specs on your hardware?

The Windows 10s is some sort of crippled Windows that only can install apps from Windows store. Not sure then what else is locked down.
[https://www.techradar.com/news/windows-10-cloud-release-date-news-and-rumors](https://www.techradar.com/news/windows-10-cloud-release-date-news-and-rumors)

All models of Acer have unique "trust" requirement once Ubuntu is installed.
Update UEFI from Acer to be sure to have latest UEFI. And check that your model has the "trust" setting in UEFI. 
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
      [/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
       One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot) 
    
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

### Post by meshica7 on 2018-12-31
> **oldfred said:**
> What are actual specs on your hardware?




```
**Processor**

Intel®

Processor Type

Celeron®

Processor Model

N4000

Processor Speed

1.10 GHz

Processor Core

Dual-core (2 Core&#8482;)


**Display & Graphics**

Graphics Controller Manufacturer

Intel®

Graphics Controller Model

UHD Graphics 600

Graphics Memory Technology

DDR4 SDRAM

Graphics Memory Accessibility

Shared

Screen Size

14"

Display Screen Type

LCD

Display Screen Technology

ComfyView

Screen Mode

Full HD

Backlight Technology

LED

Screen Resolution

1920 x 1080


**Memory**

Standard Memory

4 GB

Memory Technology

DDR4 SDRAM

Memory Card Reader

Yes

Memory Card Supported

SD


**Storage**


Flash Memory Capacity

64 GB


**Network & Communication**

Wireless LAN Standard

IEEE 802.11ac

Ethernet Technology

Gigabit Ethernet


**Interfaces/Ports**

HDMI

2 USB 2.0 Ports
1 USB 3.0 Ports
Network (RJ-45)

[B]

Software[/B]

Windows 10 Home

64-bit Architecture
```

---

### Post by oldfred on 2018-12-31
Sounds like a standard lightweight system. 
With 4GB of RAM should be decent, but Celeron is a lower cost CPU.

---

### Post by meshica7 on 2018-12-31
Thanx everyone. I should be receiving the Acer this coming Friday..I'll keep ya posted

---

