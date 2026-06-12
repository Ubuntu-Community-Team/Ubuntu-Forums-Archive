---
title: "Installing network printer via terminal (CUPS)"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by Timothytech on 2010-09-01
So i have tried using cups, as it appears to be the only way. i did an lpinfo -v and it only shows a bunch of printers, 

network ipp
network socket
network lpd
direct scsi
network http
direct parallel:/dev/lp0
network smb
network beh
network dnssd://Lexmark%20T644._printer._tcp.local/
network dnssd://Lexmark%20T644._ipp._tcp.local/
network dnssd://Lexmark%20T644._pdl-datastream._tcp.local/
network dnssd://Deskjet%206940%20series%20%5B8D8F41%5D._pdl-datastream._tcp.local/
network dnssd://Deskjet%206940%20series%20%5B356AF2%5D._pdl-datastream._tcp.local/
network dnssd://Lexmark%20T632._ipp._tcp.local/
network dnssd://Lexmark%20T632._printer._tcp.local/
network dnssd://Lexmark%20T632._pdl-datastream._tcp.local/
network dnssd://Lexmark%20T632%20(2)._ipp._tcp.local/
network dnssd://Lexmark%20T632%20(2)._printer._tcp.local/
network dnssd://Lexmark%20T632%20(2)._pdl-datastream._tcp.local/
network dnssd://Lexmark%20T630%20(3)._ipp._tcp.local/
network dnssd://Lexmark%20T630%20(3)._printer._tcp.local/
network dnssd://Lexmark%20T630%20(3)._pdl-datastream._tcp.local/
network lpd://10.7.102.39/

now the printers i need are lexmark t616's. which appear to be unavailable, i added 
"Listen 10.7.102.255 so it would listen in on that network ip. now im completely noob at cups right now so im not sure exactly what to do. 

i then use the command 

 lpadmin -p NET505 -E -m /home/timothy/Downloads/opt616.ppd \ -v socket://10.7.102.65

and it gave me an error, can someone please help me, the printer is a lexmark t616 i found the drivers online and have the gz file in the directory above then gunzip'd them. is there an easier way to do this or is my command wrong?

---

### Post by wbar2 on 2010-11-21
Does the printer have a USB connection that it could use for installation? If so, you can install the printer while it is hooked up to the USB port. Then, copy that printer and change its URI to "socket://IPADDRESSOFPRINTER".

---

### Post by efflandt on 2010-11-21
You probably need -P (captial P) to point to the ppd file.  I think -m is for some sort of System V "script".

Otherwise maybe you could configure it using: **w3m [http://localhost:631](http://localhost:631)**

I don't know if socket://10.7.102.65 will automatically determine protocol or queue name, but if that does not work, you could try socket://10.7.102.65:9100 which is a JetDirect thing, but worked for my Lexmark C543dn when my system could no longer find it by name on the WAN side of a wireless router (wireless on my wireless/modem/router stopped working).  Can you ping that IP or see anything with **w3c [http://10.7.102.65](http://10.7.102.65)** (although, you may not see much without graphics)?

---

