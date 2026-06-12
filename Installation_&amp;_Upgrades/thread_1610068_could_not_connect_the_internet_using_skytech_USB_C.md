---
title: "could not connect the internet using skytech USB CDMA modem in ubuntu 10.10 (SuperOS)"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by fxlovers on 2010-10-31
please help :(....
i can't connect the internet using Skytech CDMA USB modem in my ubunntu 10.10 (Super OS) i follow the instruction in this thread [http://ubuntuforums.org/showthread.php?t=1609880](http://ubuntuforums.org/showthread.php?t=1609880)

1. Boot w/ out device,
2. connect the device,
3. open the terminal and type..

GC224PA-UUF:~$ usb-devices
...............
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2015 ProdID=0001 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=USB MMC Storage
S:  SerialNumber=000000000002
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
-------------------------------------------
GC224PA-UUF:~$ ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory

GC224PA-UUF:~$ ls -al /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2006-02-14 22:18 /dev/disk/by-id/usb-Qualcomm_MMC_Storage_000000000002-0:0 -> ../../sr1

-------------------------------------------
GC224PA-UUF:~$ grep Qualcomm /var/log/syslog
Feb 14 22:18:02 bagoesh-Presario-V3000-GC224PA-UUF kernel: [ 1030.832258] scsi 6:0:0:0: CD-ROM            Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
-------------------------------------------
GC224PA-UUF:~$ which modem-manager
/usr/sbin/modem-manager
-------------------------------------------
[B]sudo gedit /etc/udev/rules.d/zte_eject.rules
[/B]
[B]SYSFS{idVendor}=="2015", SYSFS{idProduct}=="0001", RUN+=/usr/sbin/eject %k, OPTIONS+="last_rule"
[/B]
reboot....
and the result is nothing :((

i've check what happen and when I type 
GC224PA-UUF:~$ ls -al /dev/disk/by-id/usb 
ls: cannot access /dev/disk/by-id/usb: No such file or directory 
GC224PA-UUF:~$ ls -al /dev/serial/by-id/usb* 
ls: cannot access /dev/serial/by-id/usb*: No such file or directory 

I still can't connect the internet, kindly need help....
:confused:

---

### Post by fxlovers on 2010-11-01
[SIZE=5]closed......[/SIZE]
 
transfer to [http://ubuntuforums.org/showthread.php?p=10055457#post10055457](http://ubuntuforums.org/showthread.php?p=10055457#post10055457)

---

