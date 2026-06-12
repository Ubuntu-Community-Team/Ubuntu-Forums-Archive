---
title: "Get working HP network printing in Edgy and Dapper"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Extr3me on 2006-10-30
OK, I have used both Ubuntu Dapper (6.06) and Edgy Eft (6.10) on my laptop in work now for about 4 months and I absolutely love it. I will be using this OS  for my workstation when it arrives!!

It took me a while to get network printing (e.g. printing directly to a printer with a network address) to work as I am on a university network.  I finally got it all going rather easily, but you have to avoid the defaults that Ubuntu uses.

I am printing to a mono HP Laserjet 4000 and a Colour HP Laserjet 4600dn but I can't see why this wont work with any HP network printer.  Both printers are apparently not supported to work with network printing by HPLIP (or HPIJS if you are using Edgy Eft).

The trick is to use the HP JetDirect protocol for the connection to the printer.  Be careful to use either the IP address directly of the printer or the bare web address.  E.g. don't include the 'http://' or any other pre-leading network type info, as this can lead to confusion later.

Also, don't use the Ubuntu recommended Postscript printing driver as it just don't happen.  Use the hplip (if you are using Dapper) or hpijs (if you are on Edgy Eft).  They are both the same driver, not sure of the need to change the name but there you go.

Using this configuration, I have no problems printing in Colour or Mono from all the Ubuntu software!!  Works just great once you get it going.

Extr3me

---

### Post by standards on 2006-11-09
hey, thanks! i was having a tough time printing on our networked printer too.

---

### Post by philipgoodfellow on 2006-11-19
Thanks,

I can confirm this method gets an HP OfficeJet 6310 working on Edgy over Ethernet.
All done from the graphical interface.

---

### Post by jackn on 2007-07-16
Extr3me, I can't get my client machine, a laptop, to print to my server machine (a desktop), which has an HP Deskjet 5740 attached.

I've followed the standard instructions for network printing, using IPP. 

lpstat -p -d on the client side gives me:

[CODE]lpstat -p -d
printer DeskJet-5740 is idle.  enabled since Tue 17 Jul 2007 01:14:41 AM CEST
        Connecting to 192.168.0.1 on port 631...
system default destination: DeskJet-5740

which seems nice, but no printing takes place...

I don't know whether this is due to my HP model, Deskjet 5740.

I did go ahead and try to follow your instructions, assuming that the printer wouldn't follow IPP, but that wouldn't work either. 
When I set the protocol on the client machine to jetDirect, it didn't work. Also, although I gave it a detailed internet address, it would only show "ipp" whenever I checked the properties again. And the printer would show as paused as soon as I tried to print. 
I don't know whether indieed I need jetDirect, as opposed to IPP.

I'd need something more detailed in order to follow your advice. I don't know whether I should also change something on the server machine. And I don't know what to do about the pausing problem I've mentioned.

Can you please help?

Thanks,
Jackn

---

