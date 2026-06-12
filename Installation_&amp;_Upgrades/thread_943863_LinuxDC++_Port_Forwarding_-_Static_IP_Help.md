---
title: "LinuxDC++ Port Forwarding - Static IP Help"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by stepbystep on 2008-10-10
:confused:I need help configuring direct connect in DC++.

:-({|=My only problem is, is that I don't understand the last instruction from this link and need step by step help.


[http://portforward.com/english/routers/port_forwarding/Dynalink/RTA1025W/default.htm](http://portforward.com/english/routers/port_forwarding/Dynalink/RTA1025W/default.htm)

:-kIt asks for: Put a dot into the **User defined radio button**. Enter the name of the program into the User defined box. It doesn't really matter what you put into this box, but something that will remind you why these ports are being forwarded would be a good idea. Enter the ip address to forward these ports to into the **Forward to Internal Host IP Address** box. If you are forwarding ports so you can run a program on your computer, you should enter your computer's ip address into that box. Use the Protocol drop down box to select the protocol type of the ports you are forwarding. If you are forwarding a single port, enter that port number into the **External Port Start, External Port End, Internal Port Start and Internal Port End boxes**. If you are forwarding a range of ports, enter the lowest number of the range into the **External Port Start and Internal Port Start boxes.** Then enter the highest number of the range into the External Port End and Internal Port End boxes. When you are finished, click the Apply button.

And that is it! You are done! 

:confused::?:That's the part I dont understand? I don't know what to enter in all those boxes?

I use "Dynalink RTA1335-4 Port Modem/Router.

Any help appreciated.=D>[-o<

---

### Post by stevensheehy on 2008-10-12
Just put linuxdcpp for the app name and the IP address of the machine running linuxdcpp. Then in the four port boxes put the port you have specified in linuxdcpp's preferences for TCP. Then do the same in the next row for UDP.

---

### Post by stepbystep on 2008-10-14
thanks heaps for that. Thunderbirds are gooooooooooo!!!!!!!!!!!!!!!!!!!!!:lolflag:

---

