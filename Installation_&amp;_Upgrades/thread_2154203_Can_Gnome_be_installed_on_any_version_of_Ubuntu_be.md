---
title: "Can Gnome be installed on any version of Ubuntu besides 13.04?"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by FMFCorpsman on 2013-06-13
Hello,

I just got my Ubuntu back a little while ago. I was fortunate enough to be able to purchase a cheap laptop, but unfortunate that Dell gave me Windows 8. Some people on here put a lot of time in to help me load Ubuntu alongside. This morning though after upgrading to 12.10 through the update manager, I got a black screen at restart. OldFred tried bail me out again, but in the end my impatience won and I wiped the whole drive and now just run 12.04.

I would like to try Gnome, so can I install Ubuntu-Gnome 13.04 over an Ubuntu 12.04 raw install, no updates downloaded or added?

Thanks.

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by FMFCorpsman on 2013-06-14
I honestly didn't know it was that bass ackwards. Why would it be logical for them to stop supporting something they just came out with, and in the same instance support something far longer that came out almost a year ago. now I know that, it does make sense to stay, it doesn't make sense as to their thinking.

---

### Post by Cheesemill on 2013-06-14
LTS versions of Ubuntu (like 12.04) are released every 2 years and supported for 5 years. These are aimed at businesses and people who don't want to upgrade every time a new release comes out

All of the interim releases have a much shorter support cycle. This used to be 18 months but has recently been reduced to 9 months so that the Ubuntu devs only have a few releases to support at any one time. If all of the Ubuntu releases were supported for 5 years then there would be 10 different versions of Ubuntu that had to be kept patched and updated, this would be far too much work for the available developers.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

To install Gnome on your current installation you can just do...
```
sudo apt-get install gnome-shell
```

---

### Post by markbl on 2013-06-14
> **Cheesemill said:**
> 
To install Gnome on your current installation you can just do...
```
sudo apt-get install gnome-shell
```
And btw, this one-liner installs the GNOME desktop in all Ubuntu releases starting 11.10 onwards.

---

### Post by Rebelli0us on 2013-06-14
I [wiped off Windows 8 on my laptop]("http://ubuntuforums.org/showthread.php?t=2120763") too. Honestly, if you prefer Gnome you could install Mint 13 MATE, it's based on Ubuntu Precise,  has LTS and it's the most popular distro these days.

---

### Post by ahallubuntu on 2013-06-14
~

---

### Post by cincinnatus13 on 2013-06-14
> **FMFCorpsman said:**
> Hello,

I just got my Ubuntu back a little while ago. I was fortunate enough to be able to purchase a cheap laptop, but unfortunate that Dell gave me Windows 8. Some people on here put a lot of time in to help me load Ubuntu alongside. This morning though after upgrading to 12.10 through the update manager, I got a black screen at restart. OldFred tried bail me out again, but in the end my impatience won and I wiped the whole drive and now just run 12.04.

I would like to try Gnome, so can I install Ubuntu-Gnome 13.04 over an Ubuntu 12.04 raw install, no updates downloaded or added?

Thanks.

You can of course install Ubuntu Gnome 13.04 over it though it will of course erase all your settings, etc. You could keep /home if you have it as a separate partition though.
I'm on 13.04 on two laptops (one with 3.8) and it is the best Ubuntu experience I've had. Much better than Unity, or Cinnamon, etc. (JMHO of course.) 3.8 is buttery smooth and hassle free as well.

Or you can choose to go the other route and just sudo apt-get install gnome-shell.
But honestly, 13.04 with the Gnome3 PPA is very, very nice.

---

