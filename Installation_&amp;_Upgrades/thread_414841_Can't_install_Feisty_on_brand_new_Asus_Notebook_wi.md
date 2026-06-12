---
title: "Can't install Feisty on brand new Asus Notebook with ATI X2300"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Swiss2K on 2007-04-20
I've tried to install Feisty on my few days old Asus notebook with Ati x2300
After booting the CD X won't start. It says that no displays are found. I've tried to boot with different resolutions but everytime I get the same problem. Is the a workaround?

Ati as far as i can tell ATi is not making linux drivers for this card. Is the a Open source variant?

---

### Post by etherealremnant on 2007-04-20
The X2300 series is out already?

And I thought ATi was dropping the X?

---

### Post by touchwood on 2007-04-20
I am going through the same scenario Asus with x1700. I am running 6.10 using the ati-driver-installer-8.14.13.run. and it works fine after tweaking the wide screen settings in xorg.conf. I am hoping that when the upgrade finishes I can run the driver again and get the screen back as before. See www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run

David

---

### Post by etherealremnant on 2007-04-20
Editing xorg.conf and switching the driver to VESA doesn't help at all?

---

### Post by Jagot on 2007-04-20
Does [this]("http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/") help?

---

### Post by etherealremnant on 2007-04-20
This is ridiculous.

Neither nVidia NOR ATi's high-end cards work with Feisty out of the box?!

They should have pushed back the release and dealt with the backlash... Its better than the backlash that's going to come from people who are new to Feisty and can't get it to work at all, that's for sure.

---

### Post by Swiss2K on 2007-04-20
> **etherealremnant said:**
> The X2300 series is out already?

And I thought ATi was dropping the X?

LoL, well it's in my laptop for sure. I don't know about the X but if you go to ATi's website it's listed as X2300.

Anyways i've found the workaround ussing the alternate CD. I'll download this one first. Should normaly be done in 15 minutes but i don't think that's the case today, it sure wasnt yesterday :)

---

### Post by etherealremnant on 2007-04-20
Maybe the mobility chip is out then. Because the XT desktop card sure isn't!

---

### Post by Swiss2K on 2007-04-20
> **touchwood said:**
> I am going through the same scenario Asus with x1700. I am running 6.10 using the ati-driver-installer-8.14.13.run. and it works fine after tweaking the wide screen settings in xorg.conf. I am hoping that when the upgrade finishes I can run the driver again and get the screen back as before. See www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run

David

Thanks for you reply. I'll first try the 7.04 workaround i just found. If that ain't working I might install 6.10 (wich does boot) and try to do an upgrade

---

### Post by ckh on 2007-07-21
I had excact the same problem when I just changed my laptop to HP 6910p
but I just solved this probelem.

steps below:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart

(This solution was form [http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html](http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html))


-ckh

---

