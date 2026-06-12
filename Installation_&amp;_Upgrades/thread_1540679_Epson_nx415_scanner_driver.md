---
title: "Epson nx415 scanner driver"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by archik1989 on 2010-07-28
Hello, everyone!

I've been searching how to install a scanner on ubuntu.

I found a lot of info how to install the printer, but couldn't find about the scanner

So, my printer works just fine, but I can't get my scanner worked

Model: Epson Stylus NX 415
```


lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 002: ID 0b05:1751 ASUSTek Computer, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04b8:0851 Seiko Epson Corp. 
Bus 002 Device 003: ID 04f2:b033 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```please help, 

ubuntu 10.04


sane 0.996 says no devices available

I think that I just need to enable my driver somewhere. I just don't know what I need to configure, where is the file conf for the scanners. Also, I want to know, the driver for my scanner installed or not? maybe it did, but still disabled. it just mine thoughts...


I used this link to get my printer worked: 

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

There is a .deb package and my question is "Does this pack include driver for my scanner?"

P.S. Sorry for my english...still learning

---

### Post by lechien73 on 2010-07-28
I seem to recall that you need to install libsane-extras to get Epson scanners working.

Firstly switch off the printer, then type:

```
sudo apt-get install libsane libsane-extras
```

When this has been installed, switch your printer back on and see if xsane works.

---

### Post by archik1989 on 2010-07-28
I turned off my printer, installed what you said
(By the way, libsane was installed, but libsane-extras was not)
then turned on printer, ran xsane >the same problem :-(

what do you mean by switching off printer? you meant that I needed to do that by pressing OFF button on my printer, right? or you meant that i needed to switch it off by the console???

if so, could you please explain how can i switch it off by the system..

thanks

---

### Post by robert shearer on 2010-07-28
On this page...
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
that you got the printer driver from, if you keep scrolling down you will find the section for the scanner driver.

You need to search through all the models (several sorts lumped in each group so check carefully- yours is there !

select it then scroll down to the questionnaire and fill it in and hit next.

That will take you to the download page
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

and scroll down to..
deb package  	
iscan-data_1.0.1-1_all.deb

down load this then scroll further to..
DEB 32bit package [libltdl7] **(for Ubuntu 8.10 or later)**  	
iscan_2.25.0-1.ltdl7_i386.deb

download it then navigate to where you down loaded them and double click on the **first download** and **after** it installs do the same for the second.

It will install and after it has you can find it in Applications=>Graphics=>imagescan! for Linux

**NOTE- these are the 32bit** packages.
If you are running 64bit ubuntu then use the 64bit packages from the same page.

Ok, think that covers it..happy scanning.

---

