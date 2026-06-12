---
title: "HP 5740 driver"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by olecsz on 2005-12-01
good day to all ubuntu users. mabuhay! am looking a deivce driver for my HP deskjet 5740. does anybody have this or any alternate driver will do.

---

### Post by bwog on 2005-12-01
Just to be sure, did you try the system menu, administration, printing?

---

### Post by akiro.yamamoto on 2005-12-01
I got this from the linux-printing site:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5740](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_5740)
Hope that helps...

---

### Post by bugi on 2005-12-01
You just need **hplip** package. It is already in the Breezy repo :-) Install it, then restart hplip and cupsys and add your printer in the system -> administration -> printing section :KS

---

### Post by David Haas on 2005-12-02
I have an HP DEskjet 5740. I installed it in a minute with the Gnome Printing Manager, mentioned by bugi. First select the printer from the list under HP and then click " Install Driver" to select the PPD file. I get to the PPD files by clicking through the directories to the HP directory. The steps to this directory are:  /usr/share/cups/model/foomatic-ppds/HP. The PPD file is HP-DeskJet_5740-hpijs.ppd.gz.
When this file is selected and installed, an unzipped copy is placed in /etc/cups/ppd.
David

---

### Post by skjantzen on 2005-12-24
[QUOTE=David Haas]I have an HP DEskjet 5740. I installed it in a minute with the Gnome Printing Manager, mentioned by bugi. First select the printer from the list under HP and then click " Install Driver" to select the PPD file. I get to the PPD files by clicking through the directories to the HP directory. The steps to this directory are:  /usr/share/cups/model/foomatic-ppds/HP. The PPD file is HP-DeskJet_5740-hpijs.ppd.gz.
When this file is selected and installed, an unzipped copy is placed in /etc/cups/ppd.
David[/QUOTE]

I did exactly what you said but got the following error:

Missing asterisk in column 1 at 1:'/usr/share/cups/model/foomatic-ppds/HP/HP-DeskJet_5740-hpijs.ppd.gz'

Any idea what this is about and how to fix it?

---

### Post by skjantzen on 2005-12-26
I got it working. I just restarted my computer and the default selections that I had made when adding the printer yesterday must have taken effect and it printed off the test page that had been spooled.

Thanks for the help.

Scott

---

### Post by ledong on 2007-05-22
dgfsgdg

---

