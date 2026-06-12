---
title: "Installer does nothing when I press Forward"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by rbx68a on 2011-03-26
Hi I'm trying to install Ubuntu Netbook remix on an Acer Aspire One previously running Linpus. I've created a bootable USB which works ok and the initial Ubuntu screen comes up, I can connect to my network.

But when I select Install, a screen comes up with three ticks - drive space, power source and internet. When I then press forward, all that happens is the cursor changes to a spinning disc. Nothing else happens. I can still click Quit so it's not frozen, it just won't do anything.

---

### Post by Dutch70 on 2011-03-26
Hi and welcome to UF

 First, what version of Ubuntu are you trying to install & how are you trying to install it? side by side, manual?

Have you tried selecting "Try Ubuntu" before attempting to install it?

Is it a dual boot or are you just moving from Linpus to Ubuntu?

Sounds like it may be a problem with your partitioning. If you can boot to the live cd. Please open gparted and take a screenshot of it. 
Attach it to your next post using the paper clip in the toolbar.

---

### Post by rbx68a on 2011-03-26
Hi - I'm trying to install the Netbook Remix 10.10 version. Installing instead of Linpus. Not sure what side by side or manual is....

Tried running directly off the USB and that does work sort of-if I remove the SD card I've got in the storage expansion slot it's ok.

Tried running gparted - it starts scanning, but then closes down.

---

### Post by Dutch70 on 2011-03-26
Try checking the md5sum of the downloaded .iso
[[COLOR="Blue"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

You may also want to check the cd/sd card if possible.
[[COLOR="blue"]https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by Rubi1200 on 2011-03-26
On the LiveCD/USB, choose Try not install.

Then, go to Applications > Accessories > Terminal and run this command:

```
sudo fdisk -lu
```

(lowercase L not 1)

Copy/paste the output back here please.

---

