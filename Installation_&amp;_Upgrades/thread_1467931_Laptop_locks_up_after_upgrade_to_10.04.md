---
title: "Laptop locks up after upgrade to 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by IBadget on 2010-05-01
Yesterday, I upgraded to 10.04 from 9.10 via Update Manager. Upon reboot after the upgrade, I only got as far as the log-on sound and the laptop locked up. Even the power button was unresponsive, so I had to unplug the laptop and let the battery run out to get the thing turned off. I then tried doing a clean install from the CD, but got the same lock-up problem afterwards. I finally had to do a clean reinstallation of 9.10. I am using a Sony PCG-GRT240G Notebook. Are there any steps I can take to get 10.04 to work flawlessly? To get 9.10 to work flawlessly, all I had to do was boot with the noapic parameter. Any help would be greatly appreciated.

---

### Post by IBadget on 2010-05-02
I am still waiting for an answer on how to get 10.04 Lucid to work on my Sony PCG-GRT240G Notebook. I can't upgrade until I find out what to do, e.g., what boot parameters to use. Using the nomodeset boot parameter gives me a tty1 (text-based) log-in prompt and no way to access the graphical GNOME desktop. Again, any help would be greatly appreciated.

---

### Post by IBadget on 2010-05-03
Bump. Still waiting for an answer. I fear that I'll be stuck on 9.10 forever. I don't want to lose the support for security updates.

---

### Post by bjarkih on 2010-05-03
I have the same problem only with an old HP compaq nx9030 I've decided to go back to karmic but I need some info on how to get the contents of my /home folder out the 10.04 partition before I remove it.

---

### Post by lechien73 on 2010-05-03
Have you tried updating the BIOS, and then booting with the noapic and nolapic options?

---

### Post by bjarkih on 2010-05-03
I did an upgrade using the manager. have no idea how to set some boot options only get the splash screen and then black screen of death.

---

### Post by IBadget on 2010-05-03
> **lechien73 said:**
> Have you tried updating the BIOS, and then booting with the noapic and nolapic options?

No, I have never updated the BIOS, and I'm only using the noapic options. When I burned the ISO of 10.04, the Live CD worked great except when trying to restart the computer after installation, the computer freezes, but the power button is still responsive and could be used to turn off the machine. When I turn it on again, I hold down the shift key for the GRUB menu and press e to specify the noapic option. After that, the system goes as far as the log-on sound and as the log-in GUI is displaying, the computer completely locks up, forcing me to unplug it and let the battery run out. I suspect it has something to do with KMS. The computer has a Nvidia graphics card. I may have to wait a month or two for the devs to iron out the bugs causing the fiasco before trying the upgrade again.

---

### Post by lechien73 on 2010-05-04
I would still suggest attempting to upgrade the BIOS. A bizarre problem with my CD-ROM eject button arose after I installed 10.04. At first I blamed the upgrade to 10.04, since it always worked fine under 9.10, but a BIOS update cured it.

---

### Post by DeeWhy2099 on 2010-05-10
> **bjarkih said:**
> I did an upgrade using the manager. have no idea how to set some boot options only get the splash screen and then black screen of death.

Exactly the same thing happened to me when upgrading using Update Manager on my Toshiba Satellite A50. Even worse, the computer now goes to BSOD about 5 min after I boot to XP as well. No probs with this computer at all prior to doing this upgrade. The upgrade has clearly stuffed something at a very deep level in the BIOS or similar. Can't seem to find any solutions on the forums anywhere. Grrrrrrrrrrr.

---

### Post by boozt77 on 2010-05-13
I experienced the same problem...

I've been running 9.04 and 9.10 without problems, but after upgrading to 10.04 (via update manager)  my laptop went blank. 

My conf:
Compaq HP Nx9030
running bios F16 (not upgraded). 

I've tried noapic options but it doesnot make a difference...

Any suggestions?


grtz
Bzt

---

### Post by kepardue on 2010-05-13
Same here.  Also running a Compaq NX9030.

---

### Post by krispiebrown on 2010-05-22
I am using Ubuntu 10.04 on a Compaq nc6400 and my mouse locks up / freezes every time I start Ubuntu.

However I have found a work around....

I press the volume up and the volume down laptop buttons and it frees the mouse.

I have to do it each and everytime I boot up...

Krispie

---

### Post by schucki.be on 2010-06-30
Still no news about getting our laptops alive with 10.04?

Thnx,

JSK

---

### Post by bjarkih on 2010-06-30
It works fine with a clean install.  There seems to be a problem with the upgrader.  My friend had a similar problem when using the upgrader on his desktop.  It didn't freeze but bootup was very slow.

---

### Post by schucki.be on 2010-08-17
I did several clean installs, but nothing works...:-&

---

