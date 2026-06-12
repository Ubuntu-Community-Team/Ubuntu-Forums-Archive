---
title: "reliance zte mg880 data modem problem"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by khirodpatra on 2009-12-05
HI
I try to use my reliance zte mg880 modem on UBUNTU 8.04 server ,but kernel does not detect as a modem and there is no /dev/ttyUSB0.It detect as a storage device.Please help me to solve this problem 

Some other information related to this Modem

$lsusb

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0b97:7772 O2 Micro, Inc. 
Bus 005 Device 002: ID 0b97:7761 O2 Micro, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 15ca:00c3  
Bus 004 Device 001: ID 0000:0000  
[COLOR=Blue]Bus 003 Device 003: ID 19d2:fff5 [/COLOR] 
Bus 003 Device 002: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:8140 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
---------------------------------------------------------------------
sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttyS0 first, /dev/modem is a link to it.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   USB0 USB1 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

----------------------------------------------------------------------

dmesg|grep "ZTE"
[   26.047111] scsi 4:0:0:0: CD-ROM            ZTE      USB Storage FFFE 2.31 PQ: 0 ANSI: 2


Kind Regards
Khirod Patra

---

