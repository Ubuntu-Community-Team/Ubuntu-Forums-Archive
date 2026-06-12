---
title: "Does printing support have to be installed separate from the Kubuntu install?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by marekvf on 2007-08-12
Does printing support have to be installed separately from a normal Kubuntu install?

---

### Post by linuxwizard on 2007-08-12
Depends on what kind of printer you have. Some you have to do more configuration than other some you might have to install drivers. Also is the printer supported or not supported in linux. I have 3 HP printers i can install all in about 10 minutes after install of Kubuntu. What make/model are you wanting to install ?

---

### Post by marekvf on 2007-08-13
Hi,
Thanks for your quick response.  I have two printers in question: an HP DeskJet 1120C and an HP Laserjet 4200dtn.  But what puzzles me is that my kubuntu linux system had no lp commands available until I installed CUPS support.  That just seemed strange to me.  Now I do have the lp command but I get a scheduler not responding error.

Thanks for your help

---

### Post by linuxwizard on 2007-08-13
Did you try installing the printer first and you had problems ? As far as I know CUPS is installed by default. Look over this link for HP setup and see if anything might help. I know it shows Dapper Edgy & Feisty basic same setup just a general guide.

[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)






Both work Perfectly

[http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_1120C](http://www.openprinting.org/show_printer.cgi?recnum=HP-DeskJet_1120C)  Recommended Driver hpijs 

[http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4200](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4200)
Recommended Driver  Postscript

---

### Post by marekvf on 2007-08-14
Unfortunately, I did not install Kubuntu on the system.  When I got my hands on the system I couldn't find any printing commands and only when I installed CUPS did I get an lp command.  You mentioned installing the printer.  Does that require anything more than getting the driver?

---

### Post by linuxwizard on 2007-08-14
When i said install printer i mean to add printer

Follow This you will have to do this for each printer

Some printers will be automatically detected by Kubuntu; for those that are not, choose K-Menu->System Settings->Printers then choose Add->Add Printer/Class and run the Printer Install Wizard.

---

