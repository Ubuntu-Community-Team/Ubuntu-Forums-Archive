---
title: "How do I get my printer working on a Asus wl-500g?"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by divel on 2005-03-26
<flatter>Thanks everyone for the excellent community supporting Ubuntu</flatter>

I'm running Hoary, and I have problems setting up my printer that is connected to the parallell port on my Asus wl-500g. It is a Brother HL-720, and the driver is shown in the list of possible drivers.

My router has 192.168.1.1 as IP, but I can't figure out how to get it printing? What do I need to input in the printer setup to get it working?

Regards 
Thor

---

### Post by kperkins on 2005-03-27
Are you trying to print to this over your lan, or is it just local  (ie. are you printing just from your Asus machine)? 
Do you have a mixed lan (ie windows and linux machines), samba, what?

---

### Post by divel on 2005-03-28
[QUOTE=kperkins]Are you trying to print to this over your lan, or is it just local  (ie. are you printing just from your Asus machine)? 
Do you have a mixed lan (ie windows and linux machines), samba, what?[/QUOTE]

Sorry about the lack of detail in my post. The printer I am trying to use is connected to the parallell port of my wireless router (Asus wl-500g). I note when I install it with windows that it creates a local port on the machine that points to the IP-address at my router with specifics on what port to use (my router also has a USB port). So I guess I'm trying to print over LAN.

Divel

---

### Post by kperkins on 2005-03-30
Never having had a router with a parallel port, I'd have to say that I haven't got any idea.  You could try setting it up like you did in Windows, with the Gnome print manager.  Using the router's IP address, and the port #.

---

### Post by divel on 2005-04-08
\\:D/  Got it working! I had to go through the CUPS interface on [http://localhost:631](http://localhost:631)
You need to enable changes through the web-interface by following the steps found at [http://ubuntuforums.org/showthread.php?t=20176](http://ubuntuforums.org/showthread.php?t=20176)

Then - enter socket://192.168.1.1:9101/ as the connection string. The port number (9101 in this case) might vary depending on wethether you are using the USB-port or the parallell port and wetether you are using custom firmware or not. Give both of them a try.

---

### Post by limatho on 2005-11-04
Hi Divel,

Can you elaborate a bit on how you did connect to the WL-500g ?
I have exactly the same problem.
My printer is connected to the USB port, so I assume the port number is 
different. What should it be, and how did you obtain your port number (9101)?

Isn't it enough to just launch Menu System > Administration > Printing and put all the info there ?

Thanks in advance...

---

### Post by limatho on 2005-11-04
Well I found it out finally by myself.
In fact it is quite simple - as most things are ...

Using ubuntu you don't have to go through the pain of cups; just use the following procedure:

System > Administration > Printing
Select Network Printer - Unix Printer (LPD)
Host:    10.0.0.10 (provide your own IP address here of course)
Queue:   LPRServer

That's it !!! :) 

Happy printing...

---

### Post by kxs on 2006-11-26
Wow, that`s great! Thanks! I`ve got my Epson Stylus CX3650 working with router too. I only had to change IP to router`s default 192.168.1.1
this forum rocks :)

---

### Post by kodacy on 2008-01-06
> **limatho said:**
> Well I found it out finally by myself.
In fact it is quite simple - as most things are ...

Using ubuntu you don't have to go through the pain of cups; just use the following procedure:

System > Administration > Printing
Select Network Printer - Unix Printer (LPD)
Host:    10.0.0.10 (provide your own IP address here of course)
Queue:   LPRServer

That's it !!! :) 

Happy printing...

Thank you fro the delailed explanation it worked for me.:KS

---

### Post by k3str3l on 2008-04-29
using Feisty and am trying to get my printer working (Brother HL-5040) on my brand new Asus wl-500gp router/print server and am having trouble.

I have tried the settings you gave:
Select Network Printer - Unix Printer (LPD)
Host: 192.168.1.1  (provide your router IP address here of course)
Queue: LPRServer

but printing a test page doesn't work.
I saw another post that mentioned using the socket / raw / hp jet direct - but I that is because it is supposed to print on port 9100 - but that didn't work either.

This post is more recent, so I thought I'd ask if anybody has any other ideas...

Thanks!

---

