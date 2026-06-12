---
title: "Gasp! Has ubuntu-restricted-extras finally cast off msttcorefonts?"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-24
I decided to do a /root reinstall today and I as I was reinstalling my packages, I noticed that ubuntu-restricted-extras no longer marks msttcorefonts for installation.

Has the Liberation font set finally taken its rightful crown as a replacement?

---

### Post by cb951303 on 2009-02-24
> **Starks said:**
> I decided to do a /root reinstall today and I as I was reinstalling my packages, I noticed that ubuntu-restricted-extras no longer marks msttcorefonts for installation.

Has the Liberation font set finally taken its rightful crown as a replacement?

I hope not
liberation looks weird

---

### Post by Starks on 2009-02-24
I agree. CNN.com still fails to look even passable.

---

### Post by Starks on 2009-02-24
Okay. I'm confused.

ttf-liberation isn't installed either now.

msttcorefonts is now transitional.

"This package exists to facilitate upgrades to ttf-mscorefonts-installer.
It can safely be removed from your system."

---

### Post by cb951303 on 2009-02-24
> **Starks said:**
> Okay. I'm confused.

ttf-liberation isn't installed either now.

msttcorefonts is now transitional.

"This package exists to facilitate upgrades to ttf-mscorefonts-installer.
It can safely be removed from your system."

Hmm apparently they changed the name of the package from msttcorefonts to mscorefonts-ttf-installer. Actually it makes more sense now since msttcorefonts package never contained the actual ttf files. It was just used to get them from internet and extract to appropriate place.

---

### Post by Starks on 2009-02-24
Holy crap. Why does ttf-liberation look so horrid with subpixel enabled?

---

### Post by Technoviking on 2009-02-26
I just install ubuntu-restricted-extras in Jaunty and got msttcorefonts install?

---

### Post by Vorian Grey on 2009-02-26
Yeah, me too. I guess they just renamed the package.

---

### Post by ubuntu27 on 2009-03-01
I have Microsoft fonts installed in my comp but I never use them to create documents.

I always use [Linux Libertine]("http://linuxlibertine.sourceforge.net/") Font even in Windows box.

[http://linuxlibertine.sourceforge.net/](http://linuxlibertine.sourceforge.net/)


Everyone should install that font :) Tell all your friends about this font. It seems that Linux Libertine Font is obscure and unknown for many people. Please, raise awareness of the existence of this alternative to MS fonts.

**It is in the repositories**

One of the previous poster mentioned Linux Liberation Font. I suppose it is the same as Linux Libertine, or it is a different project? Either way both has different websites:


[Linux Libertine Homepage]("http://linuxlibertine.sourceforge.net/")
[URL="https://fedorahosted.org/liberation-fonts/"]
Linux Liberation Homepage[/URL]

---

### Post by mc4100 on 2009-03-01
> **ubuntu27 said:**
> I have Microsoft fonts installed in my comp but I never use them to create documents.

I always use [Linux Libertine]("http://linuxlibertine.sourceforge.net/") Font even in Windows box.

[http://linuxlibertine.sourceforge.net/](http://linuxlibertine.sourceforge.net/)


Everyone should install that font :) Tell all your friends about this font. It seems that Linux Libertine Font is obscure and unknown for many people. Please, raise awareness of the existence of this alternative to MS fonts.

**It is in the repositories**

+1, it make a nice replacement for Times.
```
sudo apt-get install linux-libertine
```

---

