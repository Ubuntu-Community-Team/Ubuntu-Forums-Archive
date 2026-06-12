---
title: "Create a FAX server to send and receive fax"
date: 2019-12-14
forum: Installation &amp; Upgrades
---

### Post by dam034 on 2019-12-14
Dear users,

what I want to do has already been requested and documented by many users, but I can't find a step-by-step guide to do it.

I want to do a fax server to:
[LIST]
[*]send a fax by a gui from a pdf
[*]receive faxes ONLY when I want (when I "power on" the fax) and save them in pdf in a folder with their metadatas (time, sender, etc...) in a text file or mysql
[*]check if the phone line is free or busy
[*]store in a text file (or mysql) a list of all calls made or received from that phone line (made/received, number, time, duration)
[/LIST]

Now I have these elements:
[LIST]
[*]an ubuntu server
[*]a raspberry pi 3 b+
[*]a mysql server and database specially created
[*]I can use mysql
[/LIST]

Then I need:
[LIST]
[*]a hardware to connect the phone line to server (usb-rj11)
[*]software to do all
[/LIST]

If possible, I want to create the same software for both ubuntu and raspberry. But now I can use only raspberry.

Can anybody help me?

Thanks

---

### Post by CelticWarrior on 2020-11-23
Finding the hardware - "fax-modem" - and software for Linux nowadays is almost impossible and even if you make it work it'll be painful.
Try [https://www.efax.com/](https://www.efax.com/) or any other similar service.

---

### Post by rsteinmetz70112 on 2020-11-25
This is definitely possible. There are several fax packages for Linux. 

You will first need a fax modem which is recognized by Ubuntu, it can be an internal card, a Serial Port FAX Modem (If you have a serial port) or a USB Fax Modem. Newegg has PCI or USB Fax Modems from about $10. If you're like me you may have several serial port fax modems in a box somewhere. 

Setting them up can be a chore and may require some configuration to turn the fax reception on and off, most of the servers are set receive anytime the computer is on but you can manually stop the server and start it. Creating a GUI for that might might be necessary. All of the packages I've used are essentially set up as a printer to send faxes with a pop up to fill in a cover page (if you want one) set the addressee, destination and the like. To receive faxes they can either store an image file or print the fax to a printer, you might even be able to send the incoming faxes to an email recipient.

This is pretty much a lost art as most people no longer use faxes much although I had a HP Printer Scanner Fax hooked to one of my Ubuntu Computers until the printer died.  You might want to consider that option, you can have the printer receive and print faxes as they arrive.

It's been a long time since I set one up but I used Hylafax which I think is in the repositories. I even had an email to fax gateway because I had a Contractor I had to deal with who refused to get email so I sent him all of the emails by fax.  It made it angry every time.

---

### Post by ActionParsnip on 2020-11-25
Do you send / receive / use Fax a lot? Don't we just use emails now or is this just to see if you can (Casual question here)?

---

### Post by SeijiSensei on 2020-11-25
Use Hylafax: [https://www.hylafax.org/](https://www.hylafax.org/)

It's in the Ubuntu repositories. There are two packages: hylafax-server and hylafax-client.

---

