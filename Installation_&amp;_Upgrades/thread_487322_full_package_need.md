---
title: "full package need"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by sandipan on 2007-06-28
HI 
    I am very new in Ubuntu. I installed it in my machine. It's working. But whenever i am trying to install some other thing i think we needsome kind of package. I got the package but that package depends of other one and other one actually depend on some other. I got Surprised. It's really bad.
I am trying to install build-essential pkg.
Can onyone tell me about most basic or most need package where i can start installing.
Or is there some kind of cd/dvd/package wich i can download and it will install everything like all by basic package and mp3 player, dvd player all othe stuff.

thanks
sandipan

---

### Post by croto on 2007-06-29
where do you get those packages from?

---

### Post by sandipan on 2007-06-29
I go the package from ubuntu ftp server. I downloaded from there. It's .deb file so I can installing birrectly.

---

### Post by croto on 2007-06-29
Probably that's not the easiest way of installing packages because, as you already noticed, you have to take care of dependencies. Much easier is to use Synaptic Package Manager (menu system->administration), or the utility apt-get on the CLI. For instance, if you want to install build-essential just type on the terminal:
```

sudo apt-get install build-essential

```

That installs build-essential and *all* required dependencies.

---

