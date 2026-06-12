---
title: "Libc6-2.4-6 Downgrade??"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by phibit on 2007-07-30
This is sort of funny, but sort of not. In order to compile Cube 2 (sauerbraten), I had to do some things that in retrospect I didn't understand. One of which was to install a new version of Libc6, version 2.4-6 ... So anyways I played my game and had my fun, so I wanted to move on to compiling something else (AWN from SVN). 

I go to run an ./autogen.sh  and I get

```

You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.
```

Magnificent... gnome-common sounds kinda important. I go to try and install gnome-common with synaptic, and it tells me.

gnome-common:
 Depends: libtool but it is not going to be installed

No problem: I'll just go and install libtool, and everything should be good, right?  Nope!! I go to install libtool and it leads me to libc6-2.406, and basically tells me I need to downgrade... 

Alright: Packages > Force Version > Old Version. I'm about to click okay when It tells me it's going to uninstall a buuuuuunch of packages, one of which is APT. That's not good, I NEED APT, right!? :P

Needless to say I was to scared to click apply, so I backed off... Is there anything I can do? Is this safe or am I going to screw myself over completely?

I'd like to be able to compile stuff, AND have this new version of libc6. What other choices do I have besides Ubuntuicide?

---

### Post by phibit on 2007-07-31
There has to be a better way than just reinstalling Feisty!!

---

