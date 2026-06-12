---
title: "I cant install Fluxbuntu!!!"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by Adam.W on 2008-08-05
Hello
I am running xubuntu on my fujitsu siemens lifebook B-2131 but I still find it a bit slow :( so i have been looking at installing fluxbuntu. The problem I have is that my laptop has not got a cd rom drive and the bios is to old to boot from USB :( dose anybody know of a way I can install fluxbuntu onto my laptop or is there a way of updating my bios in linux?

Thanks 

Adam

---

### Post by kerry_s on 2008-08-05
just install fluxbox on top of xubuntu.

sudo apt-get install fluxbox menu
update-menus

now log out, select fluxbox from the session menu.

---

### Post by billgoldberg on 2008-08-05
The fluxbox link in my signature will be able to help you install fluxbox and will help you to set it up properly.

No cd-rom required.

---

### Post by Adam.W on 2008-08-05
I have been playing with fluxbuntu on virtualbox and like the standerd setup so if there is a way I would like to run a fresh install of that. I'v played around with fluxbox on xubuntu but just can seem to get it how I want it where fluxbuntu is just the way I want it.

---

### Post by snowpine on 2008-08-05
> **Adam.W said:**
> I have been playing with fluxbuntu on virtualbox and like the standerd setup so if there is a way I would like to run a fresh install of that. I'v played around with fluxbox on xubuntu but just can seem to get it how I want it where fluxbuntu is just the way I want it.

Having experimented both with Fluxbuntu and with roll-my-own Fluxbox, I definitely understand where you're coming from. :-)

I wonder, if you used another computer with a CD drive to read the fluxbuntu-desktop, fluxbuntu-artwork, fluxbuntu-settings, etc. packages, then sent them to the new computer with xubuntu+fluxbox and installed them, would that basically give you Fluxbuntu for all intents and purposes? I have installed fluxbuntu-artwork on a fluxbox build and it worked perfectly, not sure if the same principle will hold true for things like rox-filer configuration.

---

### Post by Adam.W on 2008-08-05
Is there a way of net booting fluxbuntu?
Thats how I got xubuntu on my laptop.

---

### Post by snowpine on 2008-08-05
> **Adam.W said:**
> Is there a way of net booting fluxbuntu?
Thats how I got xubuntu on my laptop.

Maybe, but I kind of doubt it because it doesn't even have a live cd. :)

Try doing a search over at community.fluxbuntu.org. Things are pretty quiet over there now, but there are some good threads in the archives.

---

### Post by Adam.W on 2008-08-05
Thanks I'll have a look. If I am sucsessfull in installing fluxbuntu I will let you all know.

Thank

Adam

---

### Post by snowpine on 2008-08-05
Worst case scenario, you can download the Fluxbuntu .iso onto the new computer and scavenge some packages such as fluxbuntu-artwork from it (they are all in a folder called 'pool'). 

There is also a lesser-known distro/remix called Crunchbang that is similar to Fluxbuntu in many ways. It has an excellent net installer described here: [http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation](http://crunchbang.org/forums/topic/crunchbang-linux-80402-alternative-installation)

Good luck!

---

### Post by snowpine on 2008-08-05
ps How much ram do you have? I had a problem installing Fluxbuntu with 64mb--the terminal didn't work--and I am waiting for someone to help me over on the fluxbuntu boards. If you have 96mb or more, you'll be golden (if you can figure out how to install). I wonder if there is a floppy that you can boot from that then allows you to boot from an iso image on a USB drive?

---

### Post by Adam.W on 2008-08-05
I'v got 128mb's so should be ok. Thanks for the info I will have a crack at this tonight see what happens.

Thanks

Adam

---

### Post by snowpine on 2008-08-05
I saw this mentioned on another thread, no personal experience however: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

