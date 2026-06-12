---
title: "parallel port printer not recognized by CUPS"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by michaelbg on 2006-11-12
Hi,

I use ubuntu dapper 6.06.

I have two printers connected, one a multi-function on a usb port and a printer on the parallel port. The parallel port printer works fine in windows and not in ubuntu. (USB printer works in both.)

I looked at linuxprinting.org ([http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1](http://www.linuxprinting.org/~till/printing-tutorial/tut.html#1_1)) 
and tried the advice there.

lpinfo -v gives
network socket
network beh
network bluetooth
direct usb://hp/officejet%205500%20series?serial=MY56AG12VH96
direct hp:/usb/officejet_5500_series?serial=MY56AG12VH96
network http
network ipp
network lpd
network smb

so no direct parallel

Then I did the second step, 
cat /proc/sys/dev/parport/parport*/autoprobe*
which gave 
CLASS:PRINTER;
MODEL:HL-760 series;
MANUFACTURER:Brother;
COMMAND SET:PCL5,PJL;

which seems ok. If this had failed, the website suggested reloading the modules, but they seem loaded. So now what do I do? if I manually add the printer 
lpadmin -p Brother -E -v parallel:/dev/lp0 -m HL-760.ppd
it complains about the ppd file
lpadmin: Unable to copy PPD file!
but it does seem to add the printer, since it is in my printer list but 
it still doesn't work. 

What should I try next?

Thanks,
Michaël

---

