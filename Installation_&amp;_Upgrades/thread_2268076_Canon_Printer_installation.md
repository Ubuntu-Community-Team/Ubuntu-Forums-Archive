---
title: "Canon Printer installation"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by prem_333 on 2015-03-06
Hai i am new to ubuntu, I want to install canon LBP 2900 in ubuntu 14.04
I have already installed all drivers but all my efforts are in vain. 
Can any one help me to make my printer to work in ubuntu 14.04 32 bit.Spooler display is as follows

root@Dell-Inspiron-N4010:/home/kumar# ccpdadmin

Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler    : Backend    : FIFO path        : Device Path     : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP2900     : usb         : //Canon/LBP2900?serial=0000A3B0432k     : usb://Canon/LBP2900?serial=0000A3B0432k     


I am waiting for a good response

Thank You,
with regards,
Prem kumar M

---

### Post by MAFoElffen on 2015-03-06
Which version of Ubuntu and what edition?

Canon running in Ubuntu Desktop Edition = plug the usb cable into the printer. Turn it on. Plug the USB into the computer. The USB sense sees the printer ands asks if you want the printer added. Go into the printer setting and make it default dprinter (if that's what you want to do...) Set your other default setting int the printer.

"Where" are you having problems with that?

---

### Post by pdc on 2015-03-06
Hi prem_333

I note that you kindly told us in your post that you have > [SIZE=4]ubuntu 14.04 32 bit[/SIZE] .....thanks for that........very helpful

with most printers one seems to need to do 3 things:

1) establish connection (ie wireless or usb cable!)
2) install drivers
3) register the printer (PPD) with the print spooler.

(and with Canon and Brother's installer scripts, 2) and 3) are done together).

_________

the LBP series use Canon's CAPT driver; for that there are 4 steps:

1) establish connection (ie wireless or usb cable!)
2) install drivers
3) register the printer (PPD) with the print spooler.
4) Register the printer in the ccpd daemon setup file.

___________________________

so the structure of the command for 3) ([SIZE=4]**register the printer (PPD) with the print spooler**[/SIZE]) is ```
sudo /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp://localhost:59787 &#8211;E
```

so for you that would likely be ```
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 &#8211;E
```

______________--

**Register the printer in the ccpd daemon setup file.**

```
sudo /usr/sbin/ccpdadmin -p [Printer Name] -o [Printer Device Path]
```

so if you only had one printer; on a usb connection, the command would likely be:

```
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
```                  ..............whereas if the LBP was the second of two usb printers, the command would be ```
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp1
```

_______________

so to clarify, can you please paste this into a terminal ```
/usr/sbin/lpinfo -v
``` and please copy and paste back the results

________________

post #9 here [http://ubuntuforums.org/showthread.php?t=2135549&p=12605257#post12605257](http://ubuntuforums.org/showthread.php?t=2135549&p=12605257#post12605257) pretty well goes over the same ground;

_______

I note from the command ```
sudo ccpdadmin
``` you got 

```
  Entry Num      : Spooler       : Backend             : FIFO path :                                                      Device Path                                                  : Status
----------------------------------------------------------------------------
                   [0]           : LBP2900                                 : usb : //Canon/LBP2900?serial=0000A3B0432k : usb://Canon/LBP2900?serial=0000A3B0432k                    
```

whereas I get 

```
  Entry Num  : Spooler	      : Backend	          : FIFO path		: Device Path 	: Status 
 ----------------------------------------------------------------------------
                  [0]          : LBP3100 	: ccp 		: //localhost:59787 	: /dev/usb/lp1 :                
```

_________________

...........so I think I am wondering if you registered the printer with the ccpd daemon ........and I wonder if had seen the advice to use > //localhost:59787 in registering the ppd file with the print spooler

---

