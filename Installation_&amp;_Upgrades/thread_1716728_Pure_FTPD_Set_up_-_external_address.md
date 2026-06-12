---
title: "Pure_FTPD Set up - external address"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-28
I am attempting to setup pure-ftpd and I am getting an error when I test from an external address using passive mode.

ERROR: Server returned unroutable private IP address in PASV reply

The issue is the Ubuntu server does not know it external IP address.   How do I set this up.   I checked /etc/network/interfaces and the external ip address is not displayed.  How do I set this up?


I tested the ftp connection using [http://ftptest.net](http://ftptest.net) and I get the following test log.

       Status: Resolving address of 190.240.183.140 
       Status: Connecting to 190.240.183.140 
       Status: Connected, waiting for welcome message 
       Reply: 220---------- Welcome to Pure-FTPd [privsep] [TLS] ---------- 
       Reply: 220-You are user number 1 of 50 allowed. 
       Reply: 220-Local time is now 11:39. Server port: 21. 
       Reply: 220-This is a private system - No anonymous login 
       Reply: 220-IPv6 connections are also welcome on this server. 
       Reply: 220 You will be disconnected after 15 minutes of inactivity. 
       Command: CLNT [http://ftptest.net](http://ftptest.net) on behalf of 190.240.183.140 
       Reply: 530 You aren't logged in 
       Command: USER xxx
       Reply: 331 User xxx OK. Password required 
       Command: PASS ********** 
       Reply: 230-User xxx has group access to: xxx   fuse       plugdev    
       Reply: 230- video      dip        tape       floppy     cdrom      fax        
       Reply: 230- dialout    adm        
       Reply: 230 OK. Current directory is /home/xxx
       Command: SYST 
       Reply: 215 UNIX Type: L8 
       Command: FEAT 
       Reply: 211-Extensions supported: 
       Reply:  EPRT 
       Reply:  IDLE 
       Reply:  MDTM 
       Reply:  SIZE 
       Reply:  REST STREAM 
       Reply:  MLST type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*; 
       Reply:  MLSD 
       Reply:  AUTH TLS 
       Reply:  PBSZ 
       Reply:  PROT 
       Reply:  UTF8 
       Reply:  TVFS 
       Reply:  ESTA 
       Reply:  PASV 
       Reply:  EPSV 
       Reply:  SPSV 
       Reply:  ESTP 
       Reply: 211 End. 
       Command: PWD 
       Reply: 257 "/home/xxx" is your current location 
       Status: Current path is /home/xxx 
       Command: TYPE I 
       Reply: 200 TYPE is now 8-bit binary 
       Command: PASV 
       Reply: 227 Entering Passive Mode (192,168,1,185,254,105) 
       Error: Server returned unroutable private IP address in PASV reply 
     


THE RESULTS FROM TEST.

       Error: Server returned unroutable private IP address in PASV reply 
       
[LIST]
[*]Make sure the server is configured to allow passive mode connections.
[*]If the server is behind a NAT router, _[COLOR=Red]make sure the server knows its external IP address[/COLOR]_.
[*]The range of ports used for passive mode must be opened in all involved firewalls.
[*]The range of ports used for passive mode must be forwarded by all involved NAT routers.
[*]Try uninstalling all firewalls and plug your computer directly into your modem, thus bypassing the router.
[/LIST]
     
I also have a filezilla forum report on this.

[http://forum.filezilla-project.org/viewtopic.php?f=2&t=19853&p=77677#p77677](http://forum.filezilla-project.org/viewtopic.php?f=2&t=19853&p=77677#p77677)


Spindler

---

