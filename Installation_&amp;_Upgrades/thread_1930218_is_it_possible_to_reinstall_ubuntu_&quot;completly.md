---
title: "is it possible to reinstall ubuntu &quot;completly&quot; fresh from within ubuntu?"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by slippycurb on 2012-02-23
Hi people, ive had ubuntu installed for years without any reinstallation needed, but latley iv just wanted to nuke everything and start clean, (and i plan on installing the kxstudio repositries as soon as possible), mainly due to jackd inconsistencys. this isnt hard i know, but iv no cd/dvd drive as i burnt it out years ago copying films, and ive no usb stick at hand ...so....
Is it possible to Completly" reinstall ubuntu from within ubuntu??I really want a fresh system!!! 
dualbooting with vista by the way on a dell inspiron1545 
any help is greatly appreciated....(yep, i know i could just borrow a usb stick...........)

---

### Post by bogan on 2012-02-23
Hi!, **slippycurb**,

In theory, at least, if you have enough free space and not too many partitions, it should be possible to download the three .deb files and install them with dpkg. Provided that is, if you know your way with that operation.

But if I were you, I would beg borrow or steal an external DVD burner or a USB stick and use that to install the new version alongside the old one. You can then copy over whatever data and configs you need, before deleting it.

BUT I am no expert, so hopefully someone who is will tell you if I am wrong.

Chao!, **bogan.**

---

### Post by snowpine on 2012-02-23
You can try creating a new User to see if that solves your problems. That would be a much less drastic step than reinstalling the OS. Just a suggestion. :)

---

### Post by MAFoElffen on 2012-02-23
> **slippycurb said:**
> Hi people, ive had ubuntu installed for years without any reinstallation needed, but latley iv just wanted to nuke everything and start clean, (and i plan on installing the kxstudio repositries as soon as possible), mainly due to jackd inconsistencys. this isnt hard i know, but iv no cd/dvd drive as i burnt it out years ago copying films, and ive no usb stick at hand ...so....
Is it possible to Completly" reinstall ubuntu from within ubuntu??I really want a fresh system!!! 
dualbooting with vista by the way on a dell inspiron1545 
any help is greatly appreciated....(yep, i know i could just borrow a usb stick...........)
I read everyones posts...
```

sudo dpkg-reconfigure -a

```Which would reconfigure every installed packages that use debconf... Would take about 1-3 hours interactively (asking user questions on what to use, overwrite configuration files with new default or leave changed, etc)...  

It would leave all your data there and unchanged. Everything you installed after the original install, would be there...

You mean like that?

---

### Post by slippycurb on 2012-02-23
Cheers people:-)

sudo dpkg-reconfigure -a eh?

that seems like a good idea to try just for fun anyway......i dont think it can hurt,,,,,,,,,,,
@bogan actually i think i do have no more partitions available....
i was hoping there would be some sort of reset button.............
but if i really have to get a usb to do it, i suppose il have to...I just wanted to be elite:-)

---

