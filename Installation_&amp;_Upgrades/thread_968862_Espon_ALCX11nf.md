---
title: "Espon ALCX11nf"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by greeklad231 on 2008-11-03
Hi please help, I have a Epson ALCX11nf printer connected to a windows network, and I have installed Ubuntu on one of my machines everything works fine, except the Epson printer I just cannot get it to print, I tried the following thread:
sudo apt-get install libcupsys2-dev build-essential
tar -zxvf Epson-ALCX11-filter-1.1.tar.gz
cd Epson-ALCX11-filter-1.1/
./configure
sudo make install
[ sudo apt-get install bc ] # this should already be installed on Heron
sudo apt-get install libstdc++5

when i go to install printer driver i found the epson alcx11 listed it install but when i try to print i get the following message: Printer Epsonalcx11 requires the **pstoalcx11.sh** program but it is not currently installed. Please install it before using the printer.

Please help as Im new to Linux and I am at a loss, please

Thank you

---

### Post by ltkermit on 2008-11-10
I am getting the exact same error, only my problem started after upgrading to 8.10, it worked fine in 8.04.  My other printer still works fine (Xerox 8560) Anyone have any ideas?

Ubuntu 8.10
Intel P4
Connected to printer via LAN

---

