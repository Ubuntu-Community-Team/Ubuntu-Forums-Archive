---
title: "Root, swap, home help"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by ChuckNH on 2006-08-26
Just the basics, here......

Two hard drives, 30G, one with XP already on it with plenty of extra space.  When I'm loading Ubuntu, am I not right that I'm best to reserve my blank drive's space for my root file, or home file?  When I'm loading new programs for ubuntu, where do they locate automatically?  I'm just trying to determine how I set up partition sizes, knowing that I can resize, but I just want to optimize set-up before I load Ubuntu. My last install was limited for space, so I obviously did something major wrong.

---

### Post by ChuckNH on 2006-08-26
Maybe this should have gone into the "beginner's forum"....but could use some help.

---

### Post by John.Michael.Kane on 2006-08-26
You can use the [gparted-livecd]("http://gparted.sourceforge.net/livecd.php") to make any adjustment you need.

As to howto set up the file system. you can do it many ways.

```
/
home
swap

boot
/
home
swap

swap
/
home

boot
/
swap
home
```

As for the space 
2-5GB for root
1-2x your mem for swap eg: if you have 512meg of ram your swap would be 1gb to 2gb
the rest of the hdd space for home

---

### Post by ChuckNH on 2006-08-26
Got it....thanks.

Just wondering..........when loading new packages, they write to...where? Home or root?

---

### Post by cjm5229 on 2006-08-26
Apps will install in root. Updates also, I usually reserve about 7-10 Gigs for root. 1 gig for swap, the rest for home. 1.5 times the amount of ram on your computer is what is usually recomended for swap. Hope that helps clarify things for you.

---

### Post by ChuckNH on 2006-08-26
Yup........very good clarification!  I had been partitioning and setting up a reinstall before your post.........and it worked out great! Have one drive as root (30 Gig) and swap as 2 Gig on other drive, with home and space where my soon to be rare windoz files reside.  Thanks to both of you for great assistance.  Learning by mistakes so far. So wondering about recommendations for learning keyboard shortcuts and also favorite apps in Ubuntu.

Thanks again.  I'd say my favorite aspect of Ubuntu is definitely the forums.  With all the recent flap about the recent xserver upgrade (I was a victim) solutions seem readily available.

---

### Post by John.Michael.Kane on 2006-08-26
This may help 
[**Linux keyboard shortcuts**]("http://www.tuxfiles.org/linuxhelp/shortcuts.html")

Here's another:
[**Gnome / KDE Keyboard Shortcuts**]("http://www.novell.com/coolsolutions/tip/2289.html")

---

