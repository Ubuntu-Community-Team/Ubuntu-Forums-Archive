---
title: "Problems installing Ubuntu on PC"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2008-10-28
I started up from the CD I created for my PC. I am running XP Pro with no external devices attached. When I restart, the live CD starts to boot, I get the Ubuntu logo and then I am stuck at a prompt that says:

(initramfs) with the Flashing cursor

What should I do?

---

### Post by Pumalite on 2008-10-28
Post your specs.

---

### Post by rmcellig on 2008-10-28
What specs are you looking for?

---

### Post by Pumalite on 2008-10-28
Memory? Graphics?

---

### Post by rmcellig on 2008-10-28
512MB of RAM

NVIDIA Geoforce2 MX/MX 400

Windows XP Pro with service pack 2

---

### Post by Therion on 2008-10-28
I would suggest you download the Ubuntu "Alternate CD" and try to install from that.

---

### Post by rmcellig on 2008-10-28
OK thanks!!

---

### Post by x C0MMAND0 x on 2008-10-28
Try the windows installer.  It is awesome.  It also allows you to still access all of your windows files.  I simply target my music app to my itunes folder and voila, all my music was there.

[http://wubi-installer.org/](http://wubi-installer.org/)

Check it out if you are interested in maintaining a dual-boot system.  It simply makes it so when your computer loads you choose what you want to boot into (Ubuntu or Windows).

Good luck!

---

### Post by Pumalite on 2008-10-28
> **Therion said:**
> I would suggest you download the Ubuntu "Alternate CD" and try to install from that.
Beat me to it!

---

### Post by Therion on 2008-10-28
> **rmcellig said:**
> OK thanks!!
And burn that CD slooooooow... 8x or slower.  I *suggest* 4x actually...

---

### Post by gmjs on 2008-10-28
Hello,

What HDD interface does your PC have?  Are you using IDE or SATA?

If you're using SATA, check which specification it's using in the BIOS.  I think you'll need to use SATA with AHCI rather than SATA with an IDE interface.

If your HDD is IDE, then I'm stuck!

Please note that you will break any Windows installation you are running on the same machine if you change this setting.  Windows XP also needs extra drivers during the initial setup ("F6 for Third Party Drivers" step) if you did reinstall XP.

You SHOULD (with definite emphasis on SHOULD!) be able to change SATA spec. from IDE to AHCI and back again and then still be able to boot your XP installation, just to test that this solves the Ubuntu issue.  I'd be much happier if you had a backup first though!

Hope this helps.

Graham

---

### Post by Pumalite on 2008-10-28
Download ImgBurn and install it:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Once installed; go to Mode>ISO>Burn
Select 1x as speed of burn

---

### Post by rmcellig on 2008-10-29
The wubi installer worked great. My only problem was that I wanted to create a 100GB partition and it seems that this installer only allows a maximum of 30GB. Is there any way of changing the partition size or am I limited to only 30GB?

---

### Post by tugh on 2008-11-02
And use a good quality blank CD

---

