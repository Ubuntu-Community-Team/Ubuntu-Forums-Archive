---
title: "Kubuntu 7.10 breaks stuff - networking, Adept installer"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2007-10-20
I upgraded my working Kubunty 7.04 install to Kubuntu 7.10 overnight.  Silly me.

Before, I had wired networking.  Now I have no networking, and anything Adept-related is quite broken.  Whenever I try to run the Package Manager, I'm told the packaging database is "already in use."  I don't see how that's possible, as this happens even from a fresh reboot, when I haven't yet run anything at all.

I get that nasty little "network disconnected" icon in the menu bar.  When I click on it, I get a window with blank values in all fields, as if I had no networking device of any kind on my system.

Since Kubuntu 7.10 refuses to use my network device, I had to reboot into windows XP to post about this.  Kubuntuforums.net is down or I would post there too.

Not sure if it matters, but here's the hardware involved:

Athlon XP 3200+ CPU, in an Abit NF7-S2.0 motherboard.  I'm using, and have always used, the built-in Ethernet device to connect to the Interwebs.  1 GB RAM, ATI Radeon 9700 Pro video card.  FWIW, I've never had video problems, except that I can't get nearly the level of 3D performance under Kubuntu that I do in Windows (e.g. FlightGear is completely unplayable).

This networking device (Nvidia nForce MCP networking controller)  still works fine in Windows XP Pro (SP2) and worked under Kubuntu 7.04 as well.

I guess my only option for now is to reinstall Kubuntu 7.04.  I kept my  /home in a separate partition.  That saves some pain, but I suppose I will still have to reinstall the myriad plugins I had put in Firefox once I get 7.04 running again.  Nuts.

---

### Post by Tahi_Kiwi on 2007-12-25
Welcome to the club. Although my 7.04 to 7.10 upgrade did not break my networking, the subsequent updates--specifically those in the third week of December 2007--for 7.10 broke my networking, which Ubuntu had originally automatically and seemlessly configured. It's been exasperating trying to get this reported!

One work-around that works for me is to run these two lines from Terminal:

sudo ifconfig eth0 up
sudo dhclient &

It's a minor annoyance.

---

