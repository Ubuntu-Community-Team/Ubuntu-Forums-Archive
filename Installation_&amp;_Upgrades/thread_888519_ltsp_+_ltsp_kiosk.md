---
title: "ltsp + ltsp kiosk"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by smadon on 2008-08-13
Hi,

I have installed LTSP which is running fine.
and now, I would like to install and test TSP Kiosk.

if I run the command ltsp-build-client --kiosk  is it going to change my config in my actual LTSP Config ?

Is it possible to have the both running ?

If yes, which command should I run to isntall kiosk without have an impact in my atual LTSP.

I can manage the DHCP server to start the correct conf file on my pxe.

Thanks
smad

---

### Post by smadon on 2008-08-15
Ok, I resolve my problem.

Need to run :

ltsp-build-client --kiosk base=/opt/ltspkiosk
and need to modify a bit in the tftboot, but it work.

Now, I have a new problem with ip-config.

If I want to run my ltsp client from an other subnet,
it stop avec nfs, 
it can't find dhcp details for the client.

I am using a LTSP Server with only one network card, and my DHCP Server is on an other server.
BOOTP and PXE works fine and bring me my initial menu to choose ltsp or kiosk. 

i read in [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-theory.html) that ipconfig contact the DHCP.
It seems to be without success for me :-(
[HTML]
A small DHCP client called ipconfig will then be run, to make another query from the DHCP server. This separate user-space query gets information supplied in the dhcpd.conf file, like the nfs root server, default gateway, and other important parameters.
#

When ipconfig gets a reply from the server, the information it receives is used to configure the ethernet interface, and determine the server to mount the root from.
[/HTML]


it seems to be the same problem for this post : [http://marc.info/?l=ltsp-discuss&m=118537769208061&w=2](http://marc.info/?l=ltsp-discuss&m=118537769208061&w=2)

But no explanation how to solve it.


Any idea will be good, ... :-/

Thanks :-)

---

