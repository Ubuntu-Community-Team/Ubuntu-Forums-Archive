---
title: "Printer no longer works"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by mdraicch on 2010-08-01
Hi to all

Have recently updated 10.04 with latest updates which included a new kernel and the printer no longer works.  In-fact I can't even define the printer and I don't have a printer installed, the install script can't locate the printer on the USB.  I have a cannon MP640.

I don't know if this helps but I can print OK through windowsXP on virtualbox, printer is found OK.  

Everything was fine until latest update.

Also my USB TV card doesn't work anymore, it also was OK before the update.

Is this just me or is someone else got the same problems?

any suggestions??

Regards
Muzza

---

### Post by davidmohammed on 2010-08-01
[google search]("http://en.eduard-dopler.de/36/install-canon-mp640-on-ubuntu/") revealed this for your printer - does it work for you?

---

### Post by mdraicch on 2010-08-02
Hi davidmohammed,

Thanks for the try but no it doesn't work, I think the upgrade screwed up something in the system files.

Muzza

---

### Post by ahbart on 2010-08-02
The Canon mp640 is working very well here on a 10.04 system. Even the scanner is working with sane now. So maybe it is something in your settings.
But: I'm using kernel [2.6.34]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/"), that could make the difference.

---

### Post by mdraicch on 2010-08-03
Hi ahbart

I am using 2.6.32.23 generic-pae everything was OK until trhe last lot of updates.

Does anyone know if I can reverse the last updates? I have tried rebooting the previous kernel but I still have the problem.  I think the problem has something to do with the USB ports.

---

### Post by ahbart on 2010-08-03
I would not reverse the last updates if I were you. 
Have you tried to remove the canon and reinstall it? 
Do you have the cups-bjnp installed? 
Don't you have this printer network connected?
You could try to install kernel 2.6.34 (it is stable): [This is a link]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/")
You need three packages: Linux-headers-x-generic, linux-headers-x-all and linux-image.
Download them en in a terminal in this specific folder type:
```
sudo dpkg -i linux*.deb
```
But you will miss the pae setting then. Are you using more then 3Gb of ram?
This page ([link]("http://www.ubuntuupdates.org/ppas/37")) suggest that there is a pae version too.

---

### Post by mdraicch on 2010-08-03
Hi ahbart

Yes I have tried all the things you said but nothing works.  I can understand about not reversing updates, I would be concerned about this too.  I thought that a good workaround might be to purchase a small hub and put the printer on the network.  That way I could have the Internet and the printer connected this might solve all my problems.

What do you think?

Muzza

---

### Post by mdraicch on 2010-08-04
I put the printer on the network all works OK, don't know what the original problem is but hopefully will clear itself with the next version.

muzza

---

### Post by ibates on 2010-12-26
I have what sounds like the same problem.  I am using 10.04 LTS 2.6.32-26-generic-pae and as far as I can tell, the problem doesn't seem to be related to an upgrade.

But, I have changed the network on the computer to which the printer is connected by USB.  I always thought it was working by USB and not WiFi.  (It is working by WiFi for other computers on the network).

lsusb deetects the printer on USB.

What is really puzzling, is that the scanner function on the MP640 ***is*** working by USB.

Any suggestions?

---

