---
title: "Cannot Install on Acer Travelmate 506DX"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by steve.7 on 2007-11-03
hello,

I have big troubles installing ubuntu on my ACER Travelmate 506 (Celeron 440Mhz).

It stops with that screen:
[[IMG]http://img401.imageshack.us/img401/3940/dsc06397fi0.jpg[/IMG]](http://imageshack.us)
[http://img401.imageshack.us/img401/3940/dsc06397fi0.jpg](http://img401.imageshack.us/img401/3940/dsc06397fi0.jpg)

Any ideas?

Thank you!

---

### Post by steve.7 on 2007-11-03
i evenn tried the 
live acpi=off
option.

did nothing change...

strange.

---

### Post by steve.7 on 2007-11-03
i even can type something, but nothing happens.

i tried the 
ACPI=off NOAPIC
switch.

no change....

too sad, i cannot even bootup!

---

### Post by kentl on 2007-11-05
Please post it as a bug: [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

I've done it for my Acer Aspire 1640Z, we can only hope for the best after that. I'm going back to Feisty for 6 months or something like that. :-)

---

### Post by grinias on 2007-11-08
Maybe you should try 
```

pci=routeirq

```
instead of  
```

acpi=off

```?

---

### Post by tcdrewiv on 2008-03-24
I have a Travelmate 506dx from 1999.  It had only 64mb ram and a 4GB hard drive and windoze 3.11

Before throwing it away I thought it would be fun to see what distros would work on this dinosaur. 

I added an additional 128mb ram (the limit) but left the HD at 4GB

I have installed ubuntu ( all versions since 6.04) with no extra boot settings **using the alternate CD** but it is  sluggish. The live CD will not work. You need to install using the alternate CD. Xubuntu runs well usining xfce4. **or**  If you look on the archive.ubuntu site you can download  the mini iso for the dist. you want .  Its only 10mb, select the cli (command line install) and the do a "sudo apt-get xubuntu-desktop" or whatever flavor of ubuntu you need. 

 Debian(gnome) etch and lenny install and run good (use net install method).

if you want speed and ease of use..... use puppy 2.17 or 3.01 It takes about 4 minutes from the time you insert the CD to surfing the internet.  If you need to set up ndiswrapper for your wireless card it will take you an extra 3-5 minutes.  Absolutely the fastest way to get that acer working.

---

