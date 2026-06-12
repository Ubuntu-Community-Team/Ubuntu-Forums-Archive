---
title: "Ubuntu doesn't recognize DVD"
date: 2019-12-21
forum: Installation &amp; Upgrades
---

### Post by Norm24 on 2019-12-21
Downloaded Lubuntu 18.04 iso for installation on an older laptop.When trying to burn the image Mate 18.04 does not recognize the inserted DVD-R,it does recognize older CD-R but these are to small to fit the image.I'm dumbfounded as to why Ubuntu Mate 18.04 can't recognize a DVD.

---

### Post by Autodave on 2019-12-21
No idea and I don't know what program Mate uses for burning.  If it is Brasero, I have had problems with that and I use xfburn which works fine.

---

### Post by CelticWarrior on 2019-12-24
> **Norm24 said:**
> (...) Mate 18.04 does not recognize the inserted DVD-R,it does recognize older CD-R (...)

Which drive do you have? Are you sure it can burn DVDs?

A CDRW drive won't read or write DVDs, a Combo DVD+CDRW drive reads DVDs but only writes to CDs; A DVDRW drive will do both. If you have the latter and it doesn't recognize blank DVDs then chances are it's broken (partially), as this drives uses two different and independent lasers for different media, one could be shot and the other still working.

It almost never is a matter of OS/software.

And if the laptop where you intend to install Lubuntu can boot from USB then don't think twice, forget about optical media, get yourself a small 4GB USB stick and use that instead.

---

### Post by yetimon_64 on 2019-12-24
> **Norm24 said:**
> Downloaded **Lubuntu 18.04** iso for installation on an **older laptop**.When trying to **burn the image Mate 18.04** does not recognize the inserted DVD-R,it does recognize older CD-R but these are to small to fit the image.I'm dumbfounded as to why Ubuntu Mate 18.04 can't recognize a DVD.

Don't assume it is **Lubuntu/Ubuntu Mate 18.04**; maybe you don't have hardware that is up to date enough to support DVD at all if very old. 

In Mate or Lubuntu install "inxi" with the command...
```
sudo apt install inxi
```
... then run inxi to check your optical drive with ...
```
inxi -d
```

On Ubuntu Mate 18.04 here; this is my result from "inxi -d" as an example...
```
yetiman:~ $  inxi -d
Drives:    HDD Total Size: 2000.4GB (58.0% used)
           ID-1: /dev/sda model: ST2000LM003_HN size: 2000.4GB
           [B]Optical-1: /dev/sr0 model: hp DVDRW  DU8A6SH dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram[/B]
```

You can see from the above example what media types this laptop supports from the output. I have highlighted the optical drive with bold text above; the other data is for my main hard disk.

If you wish to post your results we can check what your older laptop hardware supports media wise.

Regards, yeti.

---

### Post by Norm24 on 2019-12-25
Thanks for the replies folks.

Just ended up using a USB stick instead.The last DVD I burnt was Mate 18.04 on the very laptop running it now.

---

