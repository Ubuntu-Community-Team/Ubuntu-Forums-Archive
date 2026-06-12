---
title: "Printing"
date: 2004-11-11
forum: Installation &amp; Upgrades
---

### Post by kenw on 2004-11-11
Hi
Can anybody point me in the right direction please.
I have just downloaded and installed Ubuntu and I cannot get my printer to work.
It is an Epson Stylus C42UX I have installed it as a Epson Stylus, New Stylus Colour and New Stylus Photographic.
In all three cases it has been recognised properties show Stylus C42 it has appeared in all the correct places in  configure printer. But when I try to print a test page it shows 'test page sent to printer' it appears in the job queue but the printer just produces blank sheets and keeps going till it runs out of paper.
I have made sure it is not listed as network printer.
Any help would be greatly appreciated
Thanks
kenw

---

### Post by kamstrup on 2004-11-12
How exactly did you install it? Through Computer->Sys.Conf.->Printing ?

---

### Post by kenw on 2004-11-12
Hi
First go round I let Ubuntu detect at install.
The other times:- computer-sys config-printing-new printer-printer connection (chose local printer)-manufacterer-model-apply-print test page.
It works fine with Xandros2.5 and Suse 9.1
kenw

---

### Post by kamstrup on 2004-11-16
I just asked because I initially had problems myself because I installed my printer through some hacks before I discovered that i had Computer->Sys.Conf.->Printing...

Is it a usb, serial or parallel port printer? You can check if you have the appropriate modules loaded with:

lsmod | grep lp

If you could post the output of that command..?

---

### Post by teumima on 2005-02-27
Hi

I have exactly the same printer and problem

I typed:

"lsmod | grep lp"

and this is what I got:

"usblp                  12032  0
usbcore               104292  6 usblp,ehci_hcd,usbhid,ohci_hcd
lp                     10436  0
parport                37320  2 parport_pc,lp"

What do I need to do?

Thanks

---

### Post by kleeman on 2005-02-27
Try installing using kprinter (you will need to install this using apt-get). The printer you have is listed exactly in the kprinter database.

---

