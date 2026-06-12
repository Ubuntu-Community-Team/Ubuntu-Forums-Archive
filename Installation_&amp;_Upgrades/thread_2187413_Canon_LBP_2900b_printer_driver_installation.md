---
title: "Canon LBP 2900b printer driver installation"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by ece.tamilarasan on 2013-11-12
I want to know how to install driver for canon LBP 2900B in Ubuntu 12.04.3 lts...
Please give me the link to download driver for it and also installation procedure in linux

---

### Post by heir4c on 2013-11-12
[http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download](http://www.canon-europe.com/Support/Consumer_Products/products/printers/Laser/i-SENSYS_LBP2900.aspx?DLtcmuri=tcm:13-1060371&page=1&type=download)
Scroll to the bottom and click on "Accept&Download". Choose for "safe file".
Go to the Download folder and rightclick on it and choose "Unpack here" (or something like that, I have a Dutch version of Ubuntu).
Than you see a folder with the name: Linux_CAPT_PrinterDriver_V260_uk_EN
Double click and choose in the folder for the 32bit or 64bit folder, than choose the folder Debian. 
FIRST you doubleclick on the second .deb file to install: cndrvcups-common_2.60-1_amd64.deb
And than the first .deb file to install: cndrvcups-capt_2.60-1_amd64.deb

(I install always first gdebi to install downloaded .deb files. So if you will do that than open a terminal en type: sudo apt-get install gdebi
When you install now the .deb files you rightclick on the file and choose: "Open with:" and than choose "GDebi PackageInstaller"
It's easy and if there is a problem than you get a message/error.)

---

