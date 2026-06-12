---
title: "HP LaserJet4050 Parrallel  - no connection"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by wadesmart on 2007-07-15
Im on Fiesty. I have a HP 4050 LaserJet using a parallel connection. 
I clicked System > Printers > Install new printer. It correctly found my printer, installed using the Suggested Postscript driver. I noticed it was set to default on A4 paper so I changed that to letter. But after that I couldnt print a test page. I cleared the driver and looked at the hpijs driver. Still nothing. Back to postscript. 

I ran lpinfo - v :
wadesmart@wadesmart:~$ lpinfo- v
bash: lpinfo-: command not found
wadesmart@wadesmart:~$ lpinfo -v
network socket
network beh
network bluetooth
direct hpfax
direct hp:/par/HP_LaserJet_4050_Series?device=/dev/parport0
network http
network ipp
network lpd
direct parallel:/dev/lp0
direct canon:/dev/lp0
direct epson:/dev/lp0
direct scsi
serial serial:/dev/ttyS0?baud=115200
network smb

So its seeing my printer. 

If I click properties on my printer on the General tab it says: Status: Ready: open print channel failed; will retry in 30 seconds.....

I cant tell if it is or not. 

However I did notice that under Firestarter on the Events tab Im getting this Blocked Connection:
Port 32801 Source 192.168.0.2 Protocol UDP Service Sun-RPC portmap.

Now, that is my internal ip address. I turned off Firestarter to see if that would help and I still couldnt get access to my printer. 

 A guy is helping me from the ubuntu list asked me to run : echo "^L" > /dev/lp0 and that is supposed to print out a blank sheet of paper but, all it does is post to the screen. 

Wade

---

### Post by linuxwizard on 2007-07-16
This may or may not help

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by wadesmart on 2007-07-16
wadesmart@wadesmart:~$ lpstat -p -d
printer LaserJet-4050 now printing LaserJet-4050-7.  enabled since Mon 16 Jul 2007 09:05:36 AM CDT
        open print channel failed; will retry in 30 seconds...
no system default destination
wadesmart@wadesmart:~$ 

Does this mean it knows the printer is there but it cant access it for some reason? 
What does the "no system default destination" mean?

---

### Post by wadesmart on 2007-07-16
07162007 1651 GMT-6

Ok. I fixed the no system default destination.
I did this: root@wadesmart:~# echo "Printer" >/dev/lp0
and nothing happened except the printer said: Data Received.
I reached over to hit a button and accidently hit GO and it printed out the page. So, it got the information but it just wont print.
 
Why would that be?

wade

---

