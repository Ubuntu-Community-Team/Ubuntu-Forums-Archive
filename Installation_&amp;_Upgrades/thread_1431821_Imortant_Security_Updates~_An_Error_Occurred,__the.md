---
title: "Imortant Security Updates~ An Error Occurred,  the following details are provided~E:"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2010-03-17
hey all, 

   I've run into my first update 'glitch', and I really dont know what to do with this..
 Can you please enlighten me on how to handle this little hang-up? please? lol

I just tried to install the "important security updates",  and after it reads package info, 
I get this~

> an error occured~
 the following details are provided

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

 it looks/seems like it should be simple enough, but i truly am lost. 

 all ive come up with is this~ > The "Could not get lock" error indicates that another process is using apt. Note that adding the nVidia driver also counts as adding software. The solution would be: make sure that all package managers, driver installers have stopped. Then install the driver and after it's finished, install extra software   
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-nv/+question/86632](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-driver-nv/+question/86632)

 and its not doing me much good#-o
 who's got my back?  lol

 many thanks,  Rasa  :KS

---

### Post by byStanderone on 2010-03-17
...try a sudo apt-get autoclean.

---

### Post by Rasa1111 on 2010-03-17
> **byStanderone said:**
> ...try a sudo apt-get autoclean.


ahhh, amazing! lol  :KS

 thanks soo much byStanderone. greatly appreciated. 

 can you, or anyone else tell me why how/why that happens? 
and is it 'normal', and just something needed every once in awhile? (apt get autoclean)
it worked well.  Freed almost 200 Mb, and the installs went perfect afterwards. 

 thanks again man, <3

 Solved!!=D>

---

### Post by byStanderone on 2010-03-17
...sometimes update/install fails due to one reason or another, autoclean clears the cache of clutters, (bits of data) if not removed, interferes with other application's functions.

---

