---
title: "PPPoE connection behind a router during Feisty installation"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by piricoco on 2007-08-30
Hi to all!

Some months ago I've installed kubuntu feisty on my notebook HP nc8430; specs:

CPU: Intel Core2 Duo "Merom" t7200 @2GHz
RAM: 1GB @667MHz
Video: Ati Radeon Mobility x1600 bus 128bit 256MB VRAM
Display: 15,4" @1680x1050
HDD: Fujitsu MHV2080BH PL 80GB 5400rpm
DVD unit: LG HL-DT-ST DVDRAM GMA-4082N
Ethernet: Broadcom NetXtreme Gigabit
WiFi: Intel PRO/Wireless 3945ABG

I needed to follow this [HOWTO]("http://ubuntuforums.org/showthread.php?t=414194&highlight=Many+people+are+having+problems+installing+Ubuntu+7.04") to correctly install kubuntu (same for ubuntu), due to a bug not present in the latest beta!
I succeeded on this because I was connected to the internet (to download the updates) by an optical fibre ISP, through a router directly linked to the original ISP gateway (no information, like userid/password, needed); I used the automatic ethernet configurator of the alternate installer.
Now, I need to re-install the system, but I can connect to the net by another ADSL provider: I have a Wireless router ([Linksys WRT54GC]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1115416825655&pagename=Linksys%2FCommon%2FVisitorWrapper")) and the original ISP modem.
I configured the router to connect to the internet with PPPoE, specifing my username/password (saved in the router memory) and in Windows XP I succesfully connect to the internet, either by ethernet or by wifi (I use WPA2 personal with AES) boards.
My problem is: when I try to connect to the internet by the ethernet board, apt-get update can't resolve internet addresses. First, automatic configuration finishes successfully...I also tried manual configuration and I inserted the machine IP address (the first one possible, which is the same assigned by the automatic configurator), the default gateway address, the subnet mask and my provider DNS.
Is PPPoE not supported by default? Or where I go wrong?

---

### Post by Pumalite on 2007-08-30
Set your router to give DHCP. Ubuntu will recognize it instantly.

---

### Post by piricoco on 2007-08-31
Hi!
Thanks for the response...my router is yet configured to give me automatically an IP address by DHCP server, and I know that it correctly works because I use it in Windows XP (just like now).

:confused:

---

### Post by piricoco on 2007-09-01
Up, please!!! :confused:

---

### Post by Pumalite on 2007-09-01
You probably have to go to 'Network' or 'Network Tools' ( I don't use KDE) and enable your driver.

---

### Post by piricoco on 2007-09-01
> **Pumalite said:**
> You probably have to go to 'Network' or 'Network Tools' ( I don't use KDE) and enable your driver.

The problem is that I can't reach KDE because of server X can not start, due to the Ati x1600 bug in feisty that I mentioned above...do I have to do something in the shell?

---

