---
title: "Can't seem to un-install modeswitch and load an older version"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by bill.denbigh on 2010-10-13
I use a ZTE 626  USB modem to connect to the internet (and yes, i am in the wilds of  nowhere!) which using USB-modeswitch 1.1.0-2 and ubuntu 10.04 works  well.
 
I just upgraded one machine to 10.10 and it included the new modeswitch 1.1.4 which does not work, the modem is never discovered. I searched around and found that this is a bug in the latest modeswitch and apparently if you back down to version 1.1.3 it works.

So, i have two questions, 

first, where can i find version 1.1.3 of modeswitch. I have searched and cannot find older version than 1.1.4 as a .DEB file.

second, i do have a really old version of modeswitch (1.1.0-2)  on my hard-drive and have been trying to load my older 1.1.0-2 version  and am having real problems with it. I remove the 1.1.4 version and its  data using the ubuntu software centre and it looks like it properly is  removed. I then click on the .DEB file that contains 1.1.0-2 and it  opens the software centre and installs it (the data seems to be  automatically loaded as i never have to install that). I then search for  modeswitch and the version that has been  installed is the newer 1.1.4 one, not the older one i clicked on. I am  confused as this computer is not attached to the internet but it seems  to find the newer version from somewhere, uses it and therefore does not  work. I presume the version 1.1.4 is cached somewhere and i am not able to clear it out.

Incidentally, the source of the information that i have so far is here:

[https://bugs.launchpad.net/ubuntu/+s...ch/+bug/626568]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch/+bug/626568")

From reading this, i do understand that there is a problem, After reading this bug fix I tried editing the config file for the modeswitch modems and changing all of them to the format indicated, but no joy.

Any suggestions or help would be gratefully accepted.

Thanks, Bill

---

### Post by alexfish on 2010-10-21
Hi Bill

the device you relate to is not your device 626

however , zte 626 should work , First reinstate the usb_modeswitch as original

see what happens ,Please post back on you own thread , if still a problem

regards

alexfish

---

### Post by bill.denbigh on 2010-10-22
Thanks Alex. Version 1.1.4 of modeswitch definitely does not work.

I have been trying to re-install an older version of modeswitch, but to avail. 

Can you instruct me as to how i can really get modeswitch 1.1.4 off the 10.10 system and then i will install an older version to see if the problem is resolved? I have tried everything i can think of but the system seems to by pass my older 1.1.0 version and installs the (i think defective) 1.1.4 version from some cache or other.

---

### Post by alexfish on 2010-10-23
Hi

may be usb_modeswitch is not the problem

Need some info

1.Name of connection Manager been used
2. is the connection 3g

Boot the system without the device , then connect the device , then from the terminal

Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines which indicate the modem and post only those lines

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*

[COLOR=Black]Code:
[COLOR=Blue]
grep ZTE /var/log/syslog

[COLOR=Black]Code:[/COLOR]

which modem-manager
[/COLOR] 

post all results
[/COLOR][/COLOR]

---

### Post by bill.denbigh on 2010-10-23
1. I am not using a separate connection manager other than the regular Network Manager in Ubuntu to setup a Mobile Broadband connection. I use the wizard to Add a New Mobile Broadband Connection and basically follow the prompts. Since upgrading to 10.10, there is no Mobile Broadband device to select in the wizard.
2. The connection is 3g most of the time. Occasionally it drops to GPRS when i have bad weather and the connection slows down badly. It is still present, just really slow.

So following your instructions...
usb-devices --- directly after i connect the modem gives me ---->
T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=2000 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=usb-storage
I left the modem connected for a few minutes as some times there is a lag to modeswitch regestering the modem and ran it again and the results were identical.

I then coded ----->
ls -al /dev/serial/by-id/usb*
and got ----->
ls: cannot access /dev/serial/by-id/usb*: No such file or directory
I checked the /dev directory and there is no /serial sub-directory. I did find a usb-ZTE in /dev/disk/by-id so i gave that a shot and got ----->
lrwxrwxrwx 1 root root 9 2010-10-24 08:29 /dev/disk/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM -> ../../sr1

grep ZTE /var/log/syslog gave me  ---->
Oct 21 11:19:06 bill-classroom modem-manager: Loaded plugin ZTE
Oct 24 08:22:21 bill-classroom modem-manager: Loaded plugin ZTE
Oct 24 08:28:25 bill-classroom kernel: [  374.555435] scsi 5:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
Oct 24 08:28:57 bill-classroom kernel: [  406.557351] scsi 8:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0

I then tried the same set of instructions on the Ubuntu 10.04 version that i am using the same modem to connect to the internet with right now. This system is an identical desktop machine and has modeswitch version 1.1.0 loaded....

usb-devices   -------->
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

ls -al /dev/serial/by-id/usb*  -------->
lrwxrwxrwx 1 root root 13 2010-10-24 08:58 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-10-24 08:58 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-10-24 08:58 /dev/serial/by-id/usb-ZTE__Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2

grep ZTE /var/log/syslog gave me  ---->
Oct 24 08:58:18 bill-dmmps modem-manager: Loaded plugin ZTE
Oct 24 08:58:19 bill-dmmps usb-modeswitch: switching 19d2:2000 (ZTE, Incorporated: ZTE CDMA Technologies MSM)
Oct 24 08:58:31 bill-dmmps modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Oct 24 08:58:31 bill-dmmps modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Oct 24 08:58:31 bill-dmmps modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Oct 24 08:58:32 bill-dmmps usb-modeswitch: switched to 19d2:0031 (ZTE, Incorporated: ZTE CDMA Technologies MSM)
Oct 24 08:58:36 bill-dmmps kernel: [   34.401464] scsi 7:0:0:0: Direct-Access     ZTE      MMC Storage      322  PQ: 0 ANSI: 2
Oct 24 08:59:11 bill-dmmps modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-8 claimed port ttyUSB2

which modem-manager   -------->
/usr/sbin/modem-manager

Hope this all helps Alex. Thanks for the assist... Bill

---

### Post by alexfish on 2010-10-24
Looks as things may have gone wrong after upgrade / ref usb_modeswitch,
Did you change any rules prior to upgrade

First to see if a network connection can be made 

Code:

[COLOR=Blue]eject -s /sr1[/COLOR]

or

[COLOR=Blue]eject -r /sr1[/COLOR]


if the above works suggest

1. Un-install usb_modswitch and the data , reinstall , cleanup system

or try these if the problem persists try

Code:

[COLOR=Blue]sudo gedit /etc/udev/rules.d/zte_eject.rules[/COLOR]

add this line 

SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

save and exit , reboot 

alexfish

---

### Post by bill.denbigh on 2010-10-24
Nope, no changes of any kind that i know of.

"1. Un-install usb_modswitch and the data , reinstall , cleanup system"

Can you tell me how to do this, i am having huge problems getting the new version of modeswitch off my system. I have tried:

apt-get remove --purge usb-modeswitch

and then once i try to re-install an older version, it re-installs the 1.1.4 version.

I will try the...

SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

and let you know how it goes.

Thanks for the help so far Alex, really much appreciated.

---

### Post by alexfish on 2010-10-24
Hi 

the only place I can find with version 1.1.3 . package  = Sakis3g (0.2.0e) modeswitch embeded

possible to try sakis3g for connection or only prepare the modem IE modeswitching

**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=qhHETPu4H8T-4wbsqKm5Aw&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

see how it goes

also have a look at the menu options with ref to usb_modeswitch

site also seem to have source code for usb_modeswitch , 

Added:

just tested ZTE 626 on upgrade system 10.04 to 10.10 , found no problems

Suggest USB_Modeswitch forum see if they can assist

[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")

alexfish

---

### Post by bill.denbigh on 2010-10-24
I tried all you suggested and the winner was coding:

sudo gedit /etc/udev/rules.d/zte_eject.rules

SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

It worked like a charm.

Incidentally, as soon as i managed to connect to the internet, i ran update manager and the first update was a fix to version 1.1.4 of modeswitch. It may be that i was stuck on a bad version and could not seem to get the fix as i could not connect.

Thanks for all the help Alex, really cool...

---

### Post by takenouchi on 2010-10-30
:KS:KShi mates,
firstly my name is Yusuf Bachtiar from Indonesia
its lucky for me to find this thread
 thank you to bill.denbigh for making this thread
and really many thanks to alexfish for the solution
.......
since 2 years ago I use MAC OS leopard and for ubuntu I just try and after that never use it (sorry for this), but I always follow the development of Linux and especially ubuntu
......
2 days ago I go to ubuntu.com, and really amazed and excited with the new ubuntu, I'm really a fans of Simple, Beautifull, and Easy OS and  Ubuntu 10.10 is one of,
so I installed it on my other laptop (actually its netbook, so i use Ubuntu Netbook Remix 10.10), then its Really Beautiful, but I can't connect my ZTE 627 :(
.....
then i find this thread
what I have done just 
- Right Click on Network Manager, choose Mobile Broadband> Add and you'll find several tabs on it
  1. connetion name : up to you, connect automatically (tick it if you want)
  2. ipv4setting : automatic (PPP)
  3. Mobile Broadband : number : *99#, username, password, apn : depends on your Operator/Provider
  4. PPP setting > configure methode > untick all except PAP

- Open Terminal and type sudo gedit /etc/udev/rules.d/zte_eject.rules
- type the my password
- type this code SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
- reboot my Netbook
- plug in my ZTE 627
- and click the network manager and Connect (or click the connection name on 1 step)
.......
I post this using my new Ubuntu Netbook remix 10.10 and ZTE 627

good job mates, really nice to be a part of Linux Community
(sorry for bad english :P)

---

### Post by bill.denbigh on 2010-10-31
Yusef, i'm living in the Philippines right now, we are neighbors ;-) . Good to see that you you got it working.

One other thing is that once you update your system you may not need the line anymore. There seems to be a bad version of modeswitch-data that gets replaced by an update.

---

### Post by fxlovers on 2010-10-31
i just upgrade my ubuntu to 10.10 (superOS),
i use skytech USB modem, and i can't connect the internet, i follow your instruction, but still can't make connection
[http://ubuntuforums.org/showthread.php?p=10052201#post10052201](http://ubuntuforums.org/showthread.php?p=10052201#post10052201)
:confused:

---

