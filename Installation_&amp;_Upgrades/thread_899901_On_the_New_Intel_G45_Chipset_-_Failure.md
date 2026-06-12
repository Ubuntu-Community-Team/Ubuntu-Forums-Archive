---
title: "On the New Intel G45 Chipset - Failure"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Quantumstate on 2008-08-24
Hello, trying to install Ubongo on a new Asus G45 mobo ([P5Q-EM](http://www.asus.com/products.aspx?l1=3&l2=11&l3=761&l4=0&model=2413&modelmenu=1)). 

With the Hardy live CD, whether I choose live mode or install, it always dumps out to (initramfs) with no apparent error.   When I cat casper.log it says:
"Unable to find a medium containing a live filesystem."

I read somewhere that kernel 2.6.24 (Hardy) does not recognize this SATA2 controller.  So must install Ibex alpha4, with 2.6.26, and indeed it installs and runs.  

Unfortunately Ibex is extremely limited in what you can do with it.  Adept crashes instantly and Synaptic and many other tools are not installable.  There's no kcontrol, nor network settings manager, nor any other sort of system settings app.  WTF?

If only I could install Kubuntu Hardy with kernel 2.6.26.

Looks like I'm flummoxed.  Do I have to install Winduhs to record TV?

---

### Post by botfish on 2008-09-08
In the BIOS try setting the operation of the SATA drives to AHCI. The BIOS default is IDE.

Please let me know how this goes as I would like to buy a Asus P5Q-EM and install Ubuntu 8.04 on it.

Also check out:
[http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450](http://www.ubuntuhcl.org/browse/product+asus_p5q?id=6450)

---

### Post by fusionisthefuture on 2008-09-08
amen quantam, i see youre posting on the AV science forums too about this board, and i would greatly like to hear your results with it in linux, especially running mythtv.

---

### Post by Junkieman on 2008-09-09
Thanks botfish for the tip, i had a similiar issue installing Hardy but on an intel chipset. The change you suggested works, it picks up the filesystem. Hope this info helps.

---

### Post by cmsj on 2008-09-29
You'll almost certainly need to use Intrepid on this machine. Try the Ubuntu Alpha 6 version (not Kubuntu, at least not for the installer)

---

### Post by fusionisthefuture on 2008-09-29
i got my asus p5q-em with this chipset working just fine out of the box with ibex alpha 6.  i didnt have to edit anything, screen came up at correct res over hdmi.

---

### Post by Junkieman on 2008-09-30
> **fusionisthefuture said:**
> i got my asus p5q-em with this chipset working just fine out of the box with ibex alpha 6.  i didnt have to edit anything, screen came up at correct res over hdmi.

great stuff! however i'll have to wait until the e1000e network driver issue is resolved, otherwise i risk losing hardware, as mentioned [here in launchpad bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555") :/

---

