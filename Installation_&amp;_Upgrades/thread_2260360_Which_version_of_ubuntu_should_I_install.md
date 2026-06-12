---
title: "Which version of ubuntu should I install"
date: 2015-01-11
forum: Installation &amp; Upgrades
---

### Post by urso2 on 2015-01-11
I'm curious about installing Ubuntu to dual boot on my Windows 7 box.

I'm going to load - 
 - Oracle DB 11g 
 - SQL*Plus
 - jdk1.8.0_25
 - ruby
 - maven
 - IntelliJ
 - Appium

I plan on using this environment to get up to speed doing automation software testing on a Linux environment.

Is Ubuntu the right Linux flavor to support these tools/applications?
Which version of Ubuntu should I install?
How much space do I need to allocate?
What are the system/hardware requirements for the suggested version of Ubuntu?

Many thanks for any feedback, suggestions or advice.

---

### Post by sudodus on 2015-01-11
Please specify also your computer hardware, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant advice.

---

### Post by urso2 on 2015-01-11
> **sudodus said:**
> Please specify also your computer hardware, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant advice.

Thank you for such a quick reply:

- System Manufacturer:[COLOR=#0000ff] Gigabyte Technology Co., LTd.[/COLOR]
- System Model: [COLOR=#0000ff]GA-78LMT-USB3 (x64-based PC)[/COLOR]
- CPU: [COLOR=#0000ff]AMD FX&#8482;4100 Quad-Core Processor (4 CPUs), ~3.6 GHz[/COLOR]
- RAM: [COLOR=#0000ff]4GB RAM
- [/COLOR]GRAPHICS CHIP/CARD:[COLOR=#0000ff]  ATI display adapter (0x9616) / ATI Radeon 3000 Graphics
- [/COLOR]Network Adapter:[COLOR=#0000ff] Realtek PCIe GBE Family Controller

[/COLOR]Additional Information:
I am not using wifi (for this box) but have a direct Ethernet connection to the modem.

I attempted to run wubi (as administrator) to install Ubuntu-14.04-desktop-amd64 but it failed and the log file  is littered with errors associated with downloading the ISO file (which I already have on my machine) and permission errors.  I may not be understanding how to use the tool correctly, but at this point it appears not to be a viable option for installation.

Thanks Again

---

### Post by sudodus on 2015-01-11
The computer is powerful enough for any version and flavour of Ubuntu.

I suppose that you need a graphical desktop environment (and not a server with a simple text screen). In that case it is also important to know about your graphics card.

You might want to try different desktop environments. It is easy for testing purposes to install standard Ubuntu and then install

```
sudo apt-get install lubuntu-desktop xubuntu-desktop kubuntu-desktop
``` and then select desktop environment at the login screen.

I would suggest that you download (or get via torrent) **ubuntu-14.04.1-desktop-amd64.iso** This is the newest version with long time support, LTS.

How much disk space? Ubuntu can be installed in 8 GB, but you want space for the programs and input/output files. I don't know what sizes they might be. Maybe 40 GB would be enough. Do you intend to hibernate? in that case you need at least 4 GiB swap (base 2, the same as the RAM size), otherwise you may need only 1 GB swap unless you expect that some of the tested programs will need more memory than you have in RAM.

How much RAM? It depends on how you intend to test the those programs. For normal purposes 4 GiB RAM is enough to avoid heavy swapping.

I hope you can get tips from someone who knows more about the programs that you want to test :-)

---

### Post by MAFoElffen on 2015-01-11
+1 with sudodus'es recommendation's, and...

Are you going to dedicate the whole machine as a test environment to connect to as a server? Or as an all-in-one closed system environment where you are doing the develpoement, connections and analysis on that same box? 

Because on the same box, a closed system, you can do Oracle 11g local db. Connections are the same port, but through localhost.

I see you have set up a template to put together a dev suite to develop mobile apps, where you are going to need a GUI. The java framework is to drive the dev suite. I'm assuming based in JavaFX on code library API's?

Having said that, leads me to think that you want to use other's API's and hook to slim down your development time right? So while you are at it... You might also want to add in an optio of testing NetBeans and Oracle Application Builder... Those two have native hooks to Oracle (go figure that  they promote using their own dB), so less work to make that connection to work. Oracle Application Builder is geared to quickly developing mobile app's hooked to their own db.. 

Sorry, I do Dev, am back in school (to document my skills), am studying for my Oracles Certs  and am on the Server Team. So I've been through this process for myself and others.

What you are planning is on a good foundation hardware wise, but adding all those together, add more RAM by at least 8GB as a good comfortable start. 

Running even the local db version is going to take a chunk, the IDE suite is going to take a chunk. The modile emulation is going to take a chunk... Dev in Java itself adds it's own, taking up stacks with each instance hungry until you you tune your code. So when you run what you've made, running on top that all... Yes, I run 24GB on my dev station, but I find that 8GB RAM would probably do you well with what you are trying to do. I don't think that 4 would do you well with that. (just past experience)

As a slice, I would think about 60-80GB space.

---

### Post by urso2 on 2015-01-12
Thanks to both of you.
Actually the server sounds perfect, I'm not a big fan of GUI(s) and IDE(s) are a necessary evil. In a perfect world I would code in vi, as it is I'll use the vi emulator in IntelliJ.

I'm looking to go on the cheap for now, so I'll try what I've got and upgrade the RAM later.
Hoping 60G will do me.

Cheers!

---

### Post by sudodus on 2015-01-12
If you prefer the server, then install from the Ubuntu Server iso file **ubuntu-14.04.1-server-amd64.iso**

Please post back, when you have tried for a while and share your results! Then, if things are working, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Good luck :-)

---

