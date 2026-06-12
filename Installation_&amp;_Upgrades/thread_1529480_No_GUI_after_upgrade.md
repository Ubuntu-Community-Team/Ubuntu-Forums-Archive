---
title: "No GUI after upgrade"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by grathinam on 2010-07-12
Hi

I did automatica upgrade, it did go okay but after reboot I don't get the GUI any more just the command line, any ideas what is causing this and how to resolve this

Upgrading from 8.04 

Thanks in advance

---

### Post by ajgreeny on 2010-07-12
What hardware have you got, in particular the graphics card?

---

### Post by grathinam on 2010-07-12
Hi

I have the following graphic card and also everything was working fine (on 8.04) before i tried the upgrade. 

01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)

IBm T41P

Thanks in advance

---

### Post by ajgreeny on 2010-07-12
From the cli can you login and run ```
cat /etc/X11/xorg.conf
``` just to see if there is one, and if there is, what driver it is giving you.

ATI are a pain in the neck as far as these older cards are concerned, but if you have anything other than **"ati**" or "**radeon**" showing in a **Driver** line in the xorg.conf file, you may need to edit the file with ```
sudo nano /etc/X11/xorg.conf
``` and change the driver to "radeon".

If that gives you a GUI you can then look at the **System ->Administration** ->Hardware Drivers utility to see if there is a better driver available.

---

### Post by grathinam on 2010-07-12
Hi

Tried your suggestion but it did not work.
Edited the xorg.conf file, by default it had "ati" in there
changed it to "radeon" but it did not give me the GUI either and it kind of stuck at "running local boot scripts (/etc/rc.local)

any other ideas how to resolve this

I cannot blow away and start over as I have lots of data in there

Thanks

---

### Post by ajgreeny on 2010-07-13
Have you tried renaming your xorg.conf and rebooting without any such file to see if that helps.  ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conbak && shutdown -r now
```

---

