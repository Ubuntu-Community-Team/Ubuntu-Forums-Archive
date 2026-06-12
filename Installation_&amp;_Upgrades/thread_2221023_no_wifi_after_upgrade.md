---
title: "no wifi after upgrade"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by night116 on 2014-04-30
I upgraded from ubuntu 13.10 to 14.04 today the upgrade went well but now I have no wifi that works, it see's the connections available but never connects to them. it will connect via network cable, but not wifi.
I had to revert back to the old version of ubuntu to use for daily use.
Toshiba Qosmio
Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
800.000 MHz
memory 32349mb
network controller: 
intel dual band wireless AC 7260
ethernet contoller: qualcomm atheros AR8161  gigabit ethernet rev10

---

### Post by djdispencer on 2014-04-30
I have the exact same problem after upgrading from ubuntu 12.04 to 14.04.

I have a "Sitecom WLA-1001 usb adapter" for my wifi-connection.
 In ubuntu 12.04, I had to upgrade the driver for this device ('Realtek rtl8192cu'), (i found the solution for this problem here **[http://miphol.com/muse/2013/09/-realtek-8192cu-driver.html](http://miphol.com/muse/2013/09/-realtek-8192cu-driver.html)) **but in Ubuntu 14.04 it just doesn't connect and its not selectable. Weird, because during the upgrade the internet connection was fine.

I also reverted back to 12.04 for now.

---

### Post by night116 on 2014-05-01
I found my answer myself and am posting it for others using the same chip set.
I went to [http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm](http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm) and downloaded the correct firmware for my device "Intel® Dual Band Wireless-AC 7260", and unpacked it to the desktop. then copied iwlwifi-7260-8.ucode over the old one using gksudo nautilus, to /lib/firmware, then rebooted and bingo were up and running again.

---

### Post by djdispencer on 2014-05-02
Thanx, I also found a solution for my Sitecom WLA1001 USB wifi adapter with a "Reaktek rtl8192cu"-chipset :

First of all I did a clean install instead of the update (takes about 20 minutes) and then followed these instructions:
[URL="http://forum.ubuntu-nl.org/index.php?topic=83046.0"]
http://forum.ubuntu-nl.org/index.php?topic=83046.0[/URL]
Old driver/firmware problem, everything seems to work fine now, 

only downside was that I had to join github.com for downloading the updated repository's and files, it's free but still yet another account and password to remember.

It works, I'm also (re)posting this answer for others

---

