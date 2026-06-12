---
title: "CD-Rom doesn't mount at install"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by refused777 on 2005-02-16
Hey guys,

I'm trying to install Warty 4.10 on my PC, but it doesn't seem to want to mount my CD-ROM during install. I have had this problem before when installing Red Hat 9.0, and it was something to do with an incorrectly configured DMA. However, typing in "linux ide=nodma" at boot doesnt seem to work.

The drive is a Samsung SC-104 if that helps.

Thanks in advance.

---

### Post by gump on 2005-02-16
I'm having the exact same problem with a Plextor 716A dvd burner.  Does anyone have a suggestion?

---

### Post by gump on 2005-02-16
I figured it out...It is in how you have it configured in the bios.  I have a WD Raptor and a Plextor IDE DVD burner.  I had the SATA Controller set to auto.  I changed it to IDE..and it worked.  Your bios is probably different...you'll just have to tinker :wink:

---

### Post by gmc on 2005-02-19
I had a similar problem when I installed Ubuntu onto my Dell CP233 Laptop. What I did (and it's kludge) but...

1. Boot the Ubuntu install CD

2. Hit ALT-F2 and type in the following command but do not press [ENTER]

    *echo "using_dma:0" > /proc/ide/**hdc**/settings*
    (note: my cdrom is /dev/**hdc**, you're maybe different)

3. Hit ALT-F1, and when the system starts loading device drivers, watch until it loads the "ide_generic" driver and then quickly move onto step 4.

4. Hit ALT-F2, and now press [ENTER]

This will turn off DMA access for your CDROM drive and should allow you to continue with your install. After the system is fully installed, reboot and you should be good to go... 

Hope this helps

---

### Post by Zenbob on 2005-02-21
Sweet, that *gmc* trick worked for me.

---

### Post by psypher on 2005-02-28
WOW!! Damn I was sceptcial but that WORKED!. Been struggling the whole day with this, trying all kinds of switches on boot but no luck. I had this problem with a Dell latitude CPi.  Can someone pls exaplain why saying "linux nodma" at the biginning of the install does not fix this problem? Or is it just a bug and "linux nodma" should have worked. 

THANKS ANYWAY DUDE!!

---

### Post by alastair on 2005-02-28
You might have been able to do this using the arg. :

linux ide=nodma

---

### Post by psypher on 2005-03-01
nope tried that already and tried it again now. Same thinsg. as soon as the ide and cd detection is done the cd files copy over the installation freezes.

---

