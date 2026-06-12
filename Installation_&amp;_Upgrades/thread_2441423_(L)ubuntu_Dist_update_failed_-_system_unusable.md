---
title: "(L)ubuntu Dist update failed - system unusable"
date: 2020-04-23
forum: Installation &amp; Upgrades
---

### Post by rachel-g41 on 2020-04-23
In preparation for 20.04 I ran update manager today to update the system.  I'm using Lubuntu

Right at the end of the process, I got a message to say the update had  failed, that it would try to repair the update. Then a message saying  the update had failed and the system may be unusable. 

The system started, it looks updated and at first all appeared well, I opened a couple of programs. 

When I tried to set my keyboard settings (Language support) I got a  message to say the system was damaged and that nothing could be  installed or uninstalled. There was a message to use sudo apt-get  install -f (I think) but when I opened the terminal, I couldn't type  correctly because my keyboard layout is wrong. Typing sudo gives me an S  followed by a 4 and some other characters I can't remember.

Fortunately I had made a boot disk (18.04) in case of accidents and have  also backed up all important files to an external disk, so one option  of last resort would be a clean install if 18.04. 
However, when I tried to boot from the usb, it didn't recognise it and  went straight into booting the system. I checked boot options (f7 from  the splash screen) and the usb is there and selected, so I will keep  trying, but at the moment having no luck.

Any advice greatly appreciated.

---

### Post by mörgæs on 2020-04-23
> **rachel-g41 said:**
> one option  of last resort would be a clean install if 18.04.

I would say that your first resort should be a clean install of 20.04, especially since you alredy have a back-up.

---

### Post by rachel-g41 on 2020-04-23
Many thanks - the laptop did eventually boot from usb and I've done a clean install. It was for 18.04 but will update to 20.04 asap, before adding anything and/or replacing personal files.

I've marked this as SOLVED even though I'm not sure what caused the problem.

---

### Post by mörgæs on 2020-04-23
A Buntu system should be updated every day but never upgraded. Better to install the release you want and do another clean install when you want another.

---

### Post by Rex Bouwense on 2020-04-24
Since Lubuntu changed from lxde to lxqt after the 18.04 version, an update to 20.04 is generally not recommended.  A clean install is your best bet (as recommended by mörgæs.)  You should not run into problems that way.  Just back up your data.

---

