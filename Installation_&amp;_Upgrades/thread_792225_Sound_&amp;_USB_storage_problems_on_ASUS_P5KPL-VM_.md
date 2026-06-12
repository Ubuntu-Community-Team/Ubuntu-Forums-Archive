---
title: "Sound &amp; USB storage problems on ASUS P5KPL-VM M'board"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by flatus on 2008-05-12
Just a quick log for anyone struggling to get sound and USB storage to work under Ubuntu 8.04 on an ASUS P5KPL-VM mother board.  Two weeks ago, I had never used linux and started a project to set up a file server/secondary storage/bit toirrent manager.  My first attempts with Debian were abandoned as I could not get the motherboard resources (network, sound & USB ) to work properly.  I moved to Ubuntu and at least the network started happening and I could get updates, emails etc.  But USB and sound just would not work.  No /usr/sd* was being created for a sub drive and the sound would occasionally chirp but then not stop.  Dmseg would report that it could not allocate an address to a plugged in key during boot up.  I went through the process of compiling source and installing (A big learn for me in its own right!) and still no joy.

After many late nights and complaints from the wife that I was ignoring her.  I struck gold last night when I reflashed the BIOS on the motherboard.  It seems the linux drivers published by ASUS require the newest bios which was not shipped with the board I bought new only 2 weeks ago.  Now net, sound and USB-storage all work as advertised.

The bios I flashed up to is version 0802 and is available 
here: [http://dlsvr01.asus.com/pub/ASUS/mb/socket775/P5KPL-VM/P5KPL-VM-ASUS-0802.zip](http://dlsvr01.asus.com/pub/ASUS/mb/socket775/P5KPL-VM/P5KPL-VM-ASUS-0802.zip)

The network drivers (Attansic) that come with the MB and are on the ASUS site are old and it seems the set in Ubuntu 8.04 work so  I have not touched that sleeping dog.

I hope this helps someone whose sufferinga s I was.

Regards

Flatus

---

