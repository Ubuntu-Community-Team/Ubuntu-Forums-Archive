---
title: "How to re-install 12.04 from Terminal?"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by aivanchev on 2012-09-21
Hello everybody, 

I would greatly appreciate if someone could help: Yesterday I upgraded from 10.04 to 12.04, by just pressing the "upgrade" button on the "update manager". 

All seemed to go well, but when I logged in again, there was no menu bar. As in, nothing but my icons. Luckily, I had a programme "gnome up", with which to enter applications. Otherwise, there is no menu bar, i cannot open anything. 

It appears the installation was not full, somewhere it must have gone wrong. I now want to re-install 12.04 or just go back to 10.04 through terminal. 

Could someone please help?

---

### Post by Mad-One on 2012-09-21
Sorry I can't help but I can sympathise; the same thing happened to me. My solution was to reformat and install from CD. Obviously I lost all the data on the drive so I'm having to restore from backup plus re-set-up LAMP, SAMBA etc. etc. It's a complete pain.
 
Cheers - MO

---

### Post by Deepak A on 2012-09-21
i hope you did upgrading in this way, 

[http://www.omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go](http://www.omgubuntu.co.uk/2012/04/ubuntu-10-04-12-04-upgrade-how-well-does-it-go)

And i think there is no way to undo the upgrade operation. 

Try this, 

[http://www.ubuntugeek.com/apt-undo-a-simple-way-of-undoing-apt-actions.html](http://www.ubuntugeek.com/apt-undo-a-simple-way-of-undoing-apt-actions.html)

Don't know whether its gonna work or not. You should have made a backup.

---

### Post by Deepak A on 2012-09-21
ok.. try to boot using a LIVECD and take the back up if possible. Then re-install it.

---

### Post by aivanchev on 2012-09-21
Thanks all for your quick reply! 

I am currently on the 12.04 system, withOUT the dashboard/menu bar. simply a background and hte icons that I had left on the desktop, I only operate through terminal (luckily, there is ctrl+alt+T). 

To get a copy of the Ubuntu, though, I see that all downloadable files are made for windows (which I am not using atm) or as a .iso files.. However,  I would imagine it is best to download ubuntu 10.04 on a .deb file so? i can't find it anywhere.. Or just 12.04 on .deb file, so i can install it directly from here? 

or from Terminal?

---

### Post by black veils on 2012-09-21
if you are wanting to download ubuntu, to make a live disc/usb flash drive, you download the .iso. then burn as **image** to disc, at slowest speed, or use [**unetbootin**]("http://unetbootin.sourceforge.net/") (in Windows or Linux) to put it on the usb flash drive.

---

### Post by kansasnoob on 2012-09-21
> **aivanchev said:**
> Hello everybody, 

I would greatly appreciate if someone could help: Yesterday I upgraded from 10.04 to 12.04, by just pressing the "upgrade" button on the "update manager". 

All seemed to go well, but when I logged in again, there was no menu bar. As in, nothing but my icons. Luckily, I had a programme "gnome up", with which to enter applications. Otherwise, there is no menu bar, i cannot open anything. 

It appears the installation was not full, somewhere it must have gone wrong. I now want to re-install 12.04 or just go back to 10.04 through terminal. 

Could someone please help?

If you want to use Unity and restore it's defaults look here:

[http://ubuntuforums.org/showpost.php?p=11968600&postcount=40](http://ubuntuforums.org/showpost.php?p=11968600&postcount=40)

If you'd prefer a classic DE with no effects look here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

If things just seem somehow hosed from the upgrade try running:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

The output from any one of those commands may be helpful in determining how to recover ;)

---

