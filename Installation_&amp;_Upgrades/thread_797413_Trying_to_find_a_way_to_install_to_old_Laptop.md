---
title: "Trying to find a way to install to old Laptop"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2008-05-17
I have an old Gateway laptop model SOLO 5300. I want to put Xubuntu on this system and use it as my central kitchen computer for checking email on the go, looking up recipes, watching online TV or a DVD, and so on.

Its a PIII with 900mhtz CPU, 1-GB memory and I think 20GB hard drive.

The DVD drive is having problems reading any DVDs or CDs I have burned of Xubuntu from my linux computers. It will start reading the disc, like get into the xubuntu menu, but then it locks up and I cannot install the OS. Ive tried the LiveCD and the ALT cd of Xubuntu. Burned them at the slowest speeds both on a cd and also tried a dvd.

The only thing that works is a professionally made Ubuntu disc from Canonical. Id rather not put 7.04 on this system and wanted to try Xubuntu instead. Does Canonical make professional discs I can order of Xubuntu?

Any tips for getting Xubuntu on this old computer some alternative method? Thanks for any ideas! Im scratching my head on this one.

---

### Post by iheartubuntu on 2008-05-17
One of the problems I am finding is this older computer cant read 52x CDs even if I burn them at 1x. Do they still make/sell blank cd's that go up to 8x only?

---

### Post by teaker1s on 2008-05-17
what about a usb enclosure and installing through an external cd rom or dvd drive

---

### Post by kerry_s on 2008-05-17
sounds to me like a burning issue, you want to burn at 4x for the best results, cdr's are generally better.

---

### Post by Pumalite on 2008-05-17
Otherwise go with Unetbootin:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by iheartubuntu on 2008-05-17
> **Pumalite said:**
> Otherwise go with Unetbootin:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Ahh, many thanks!

Would you recommend Ubuntu 8.04 or Xubuntu 8.04 on this particular computer?

---

### Post by teaker1s on 2008-05-17
xubuntu is lighter option but you can have several desktops selectable at login

---

### Post by wolfen69 on 2008-05-17
if the commercial disk is the only one that will work, you could always install the xubuntu desktop after install.
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Pumalite on 2008-05-17
With 1 GB of RAM you can run Ubuntu 8.04

---

### Post by iheartubuntu on 2008-05-17
Does Unetbootin work like wubi or will it eventually wipe out XP for me. Im trying to get rid of XP :)

---

### Post by iheartubuntu on 2008-05-23
> **wolfen69 said:**
> if the commercial disk is the only one that will work, you could always install the xubuntu desktop after install.
```
sudo apt-get install xubuntu-desktop
```

Thanks, I think this is the way to go. I ordered a 8.04 official disc so I'll just have to wait for it. Id rather not install 7.10, then have to upgrade.

---

