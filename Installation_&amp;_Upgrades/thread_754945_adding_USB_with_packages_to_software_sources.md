---
title: "adding USB with packages to software sources"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by nlz on 2008-04-14
Hello, I'm trying to install audio software on 10 gutsy PC's. I first wanted to install ubuntu studio, but there is no DVD drive in them. 
So i thought, i can just extract the ubuntu studio image to a USB stick and then install the packages I want (they are in directory /pool ). But if i want to install anything, the installer keeps making problems about dependencies. 

So i'll have to add the directory /media/USB/pool to my repositories (software sources), somehow, this doesn't seem possible. How can i do this?
The easiest would be that i could use synaptic then to select it all. 

I thought sources.lst can only be used for online repos...

PS I gave up on booting up ubuntu studio from USB.

---

### Post by warp99 on 2008-04-14
You can use apt-get locally if you like. Debian has a howto on doing this:

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

---

### Post by nlz on 2008-04-16
i got it working with an external DVD drive.
I changed the sym link cdrom in / and / media by
```

rm /cdrom
rm /media/cdrom
ln -s /media/Ubuntu \studio /cdrom
ln -s /media/Ubuntu \studio /media/cdrom
```

and then you can just use synaptic and use the DVD as a repo.

---

