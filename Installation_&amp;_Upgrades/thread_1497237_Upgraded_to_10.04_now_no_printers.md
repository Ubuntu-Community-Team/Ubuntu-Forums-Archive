---
title: "Upgraded to 10.04 now no printers?"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by ronaldprettyman on 2010-05-30
Ok I upgraded the Ubuntu 10.04, and afterwards I can't print. Cups won't detect printers, hp-setup won't, hp-probe won't. Tried rebooting, reinstalling HPLIP, & CUPS. Installed latest version of HPLIP. did a purge of HPLIP and CUPS, and reinstalled, rebooted. Nothing

but this whole time my printer shows up under
lsusb

Any ideas?

---

### Post by bumanie on 2010-05-30
I had this problem during testing of 10.04 and uninstalled the printer and then went into Printing under Administration and searched for a printer, the driver downloaded and it has worked since. It may not work for you, but worth a try.

---

### Post by ruudschellekens on 2010-05-30
What worked for me was typing this:

```
sudo apt-get install --reinstall cups
```

into a terminal (Applications -> Accesoires -> Terminal).

I found that hint here:
[http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/](http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/)

---

### Post by jcglt on 2010-05-30
Same here, my Canon iP90 worked on my laptop with Karmic Koala (did not work as well as under Windows XP as I had lost some functionalities like ink level). It stopped working after upgrade to Lucid Lynx. The printer was recognized, the printing tasks were considered as completed in a fraction of a second but nothing was actually done.
I eventually downloaded TurboPrint2 [http://www.turboprint.info/](http://www.turboprint.info/) and tested it, it worked perfectly as soon as installed, and I got some functionalities I had lost, like ink level, a very nice print preview...
Well I tested it a few days (maximum 30 days allowed) and paid for the licence, I'm very satisfied.

---

### Post by greenchilli on 2010-06-02
On Ubuntu 10.04 the best way to setup network printer is with CUPS web interface. I could never print to this same network printer in the office before.
First you'll need the correct driver.
Locate the PPD driver file for printer - In my case Gestetner DCs424 driver (Search Google for drivers)

Point your browser to [http://localhost:631](http://localhost:631) - For CUPS Interface

Go to the Administration/Printers section.

Then Add Printer - Choose "Internet Printing Protocol (http)" using socket URI e.g. socket://158.155.40.243:9100

Describe the printer. Select "Share This Printer"

Then Provide a PPD File: choose the PPD driver file you saved on disk earlier (In my case it was a file named "Gestetner-DSc424-pxlcolor-Gestetner.ppd")

Add printer and you're done.

(You might have to tweak the printer settings using System/Administration/Printing GUI afterwards. The default settings in my case was to print in color - I had to change it to Grey-scale because our company have disabled color printing on this particular printer)

It worked for me.

---

