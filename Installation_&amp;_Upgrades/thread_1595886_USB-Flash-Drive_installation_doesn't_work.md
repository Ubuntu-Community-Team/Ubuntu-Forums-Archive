---
title: "USB-Flash-Drive installation doesn't work"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by UlfZibis on 2010-10-13
I have installed Ubuntu 10.10 on a 16GB USB-Stick using the Startup Disk Creator.
After booting from it, I saw the progress dots running on the start screen running for ever (30 minutes until I switched off my Laptop). The whole time the in-use LED of my Harddrive was on.
What is Ubuntu doing so long on my Harddisk?
How can I manage, that it will work properly? :guitar:

---

### Post by mörgæs on 2010-10-13
Hi, welcome to the forum.

Have you tried booting with a CD and/or creating the USB stick with Unetbootin?

---

### Post by UlfZibis on 2010-10-13
> **mörgæs said:**
> Hi, welcome to the forum.
Thanks, welcome too.
> Have you tried booting with a CD
Yes of coarse, how should I have used Startup Disk Creator otherwise.
> and/or creating the USB stick with Unetbootin?
No, but I additionally used Universal USB Installer from Windows with same result.

---

### Post by kkobashi on 2010-10-13
I had no problem installing Ubuntu 10.10 on a 8GB stick this morning. I used the Universal USB Installer.

---

### Post by Austin25 on 2010-10-13
Like mörgæs said, try [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by UlfZibis on 2010-10-14
> **kkobashi said:**
> I had no problem installing Ubuntu 10.10 on a 8GB stick this morning. I used the Universal USB Installer.
Installing is not the problem, did you run it successfully?

Did you make the partition before, or did you use Universal USB Installer for it?
Did you erase/format the stick?
You used FAT16 or FAT32?
Does the partition cover the whole volume?
Did you install with persistence option (if yes, which size)?

I ask all these details, because 1 week ago I managed to create a working one from the 10.10_RC version, but I don't remember the details. I had one on my 2GB stick and the other on the 16GB, one created from Windows, the other from Linux. The only thing I remember is, that the working one was formatted as FAT16, the other as FAT32.
Maybe some of these parameters are important to have it work.

---

### Post by UlfZibis on 2010-10-14
> **Austin25 said:**
> Like mörgæs said, try [unetbootin]("http://unetbootin.sourceforge.net/").
According [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), UNetbootin is out of date.
Which download you suggest?

---

### Post by mörgæs on 2010-10-14
Unetbootin is not out of date. The default version in 10.04 is.

---

### Post by friTTe81 on 2010-10-14
I have had some trouble using unetbootin, the Startup disc creator works better for me

---

### Post by UlfZibis on 2010-10-14
> **mörgæs said:**
> Unetbootin is not out of date. The default version in 10.04 is.
Did you mean: The default version in UNetbootin is 10.04?
Again, which download you suggest, Windows, Linux or 
***[I]"... current version from this website or the [PPA]("http://launchpad.net/%7Egezakovacs/+archive/ppa") ..."*[/I]**

---

### Post by mörgæs on 2010-10-14
I meant 'Unetbootin is not out of date. The default version of Unetbootin in 10.04 is out of date.'

Just follow the instructions on the web site and you will have a working (and updated) Unetbootin on your machine.

---

### Post by UlfZibis on 2010-10-14
I have tried UNetbootin. Now I can boot Ubuntu from my 2GB USB-stick.
BUT...
- there was not prompt to select the language and the keybord as from the LiveCD, so I still can't use it properly with my german keyboard.
- the install option from the UNetbootin boot menu doesn't work. It ended in a looong bunch of error message, mostly i/o errors.
- there is no option for installing a persistent area to save settings, extensions, data and updates permanently

I've filed a bug: [https://bugs.launchpad.net/bugs/660784](https://bugs.launchpad.net/bugs/660784)

---

