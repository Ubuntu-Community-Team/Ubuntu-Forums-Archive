---
title: "realvnc free edition"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by mwthrane on 2006-10-19
Hi

Ive been reading these forums for quite awhile now. But now i have a question i couldnt find anywhere else. So here i am.

Im trying to install RealVNC free edition on Ubuntu.But im getting some errors. I downloaded the .RPM file from their site and converted it to a .deb file. And from what i can see that worked fine. Heres what happens when im trying to install:

sudo dpkg -i vnc_4.1.2-2_i386.deb
dpkg: regarding vnc_4.1.2-2_i386.deb containing vnc:
 xvncviewer conflicts with vnc
  vnc (version 4.1.2-2) is to be installed.
dpkg: error processing vnc_4.1.2-2_i386.deb (--install):
 conflicting packages - not installing vnc
Errors were encountered while processing:
 vnc_4.1.2-2_i386.deb

Could someone help to install this software? I only need the viewer part of the software.

Thanks in advance.

---

### Post by h4rdwire on 2006-10-19
based upon my knowledge and reading your errors, either use what you got and if u dont want to, uninstall/remove the current vnc packages on your computer.

---

### Post by az on 2006-10-19
What's wrong with all the vnc packages inthe repositories?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vnc&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=vnc&searchon=names&subword=1&version=dapper&release=all)

There is no need to get VNC from upstream.

And the vnc server is installed by default.

---

### Post by mwthrane on 2006-10-19
You were right. Some sort of VNC was installed. I fired it up but when i press connect after entering the information i got some weird errors. It seems to be an old version aswell. SO i installed xvnc4viewer from the pacage manager and fired that up. I enter the IP address and i get this error:
Thu Oct 19 22:27:20 2006
 CConn:       connected to host xx port 5900
 CConnection: Server supports RFB protocol version 4.0
 CConnection: Using RFB protocol version 3.8
 CConnection: No matching security types
 main:        No matching security types

How to fix this?

---

### Post by mwthrane on 2006-10-19
I didnt know VNC was preinstalled.

---

### Post by Technophobia on 2006-10-19
VNC in installed in Ubuntu once you format. 

type vncviewer + ip in terminal

---

### Post by mwthrane on 2006-10-19
main:        unable to resolve host by name: Success (0)
I know the ip is corrent because i can connect fine on my windows machine.

---

### Post by mwthrane on 2006-10-19
Ah, i forgot the space after the +.
But nothing happens.. terminal just hangs.

---

### Post by h4rdwire on 2006-10-19
i'm running Kubuntu and used the VNC client that came with it, ran TightVNC Server on my windows machine and i couldn't connect from my kubuntu on my laptop.

---

### Post by recrispi on 2007-03-26
I also have the same problem when I try to connect to a VNC server:

> linux:~$ vncviewer ip.server.number. -log=CConnection:stderr:100

VNC Viewer Free Edition 4.1.1 for X - built Jan  6 2007 00:46:26
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Mon Mar 26 16:16:46 2007
 CConnection: reading protocol version
 CConnection: Server supports RFB protocol version 4.0
 CConnection: Using RFB protocol version 3.8
 CConnection: processing security types message
 CConnection: Server offers security type RA2(5)
 CConnection: No matching security types


How can I find the security types accepted by my VNC client and update them to connect to the server?

Thanks.

---

### Post by recrispi on 2007-03-29
OK, I found the solution for my problem: The server had installed the enterprise edition and the client had the free edition. Aparently both aren't compatible with each other (although the realvnc page says they are compatible). I installed the free edition on the server and then I could connect painlessly.

I hope this can save headaches for anyone who find the same problem as me.

---

### Post by jlindbergh on 2007-10-30
Thank you so very very much! You just did save me further headaches! :)

---

