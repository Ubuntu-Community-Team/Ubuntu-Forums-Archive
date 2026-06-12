---
title: "installing Moblin Remix on a Netbook Remix karmic beta install"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kayzu on 2009-10-07
Hi, is it possible to install the Moblin Remix into a regular Netbook Remix install of the karmic beta?
I think the Moblin remix has great potential but I'd like to keep the Netbook Remix interface around as well, so is it possible to install UMR via synaptic just like it is possible with UNR on a regular Ubuntu?
Are there any drawbacks to this compared to a straight install of UMR?
And, is there an easy way to switch between the desktop environments? Didn't find any easy way to switch the Moblin interface off on the UMR live-CD I tried.

---

### Post by nanog on 2009-10-07
AFAIK its a dev spin and not supported in the repos.

---

### Post by ceramicm on 2009-10-07
I tested out Ubuntu Moblin Remix and noticed that the following PPA was included in the /etc/apt/sources.list:
```
deb http://ppa.launchpad.net/moblin/ppa/ubuntu karmic main
```

If you look [here]("https://launchpad.net/~moblin/+archive/ppa"), you will notice the PPA contains many Moblin-related packages. I think that adding that repository and then running ```
sudo apt-get update && sudo apt-get install moblin-remix-meta
``` might install UMR.

---

### Post by Sealbhach on 2009-10-07
You can get a Live CD iso here:

[http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/)

.

---

### Post by kayzu on 2009-10-07
> **Sealbhach said:**
> You can get a Live CD iso here:

[http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-moblin-remix/daily-live/current/)
i know, did you even read/understand my post? :p

@ceramicm: thanks, I might try that on a test install

any more suggestions/ideas/comments?

---

### Post by Mizukusai on 2009-10-21
Did it work ?

---

### Post by IanW on 2009-10-21
I tried Moblin Remix, but nuked it when I realised it has NO shutdown button.
My EeePC is now running quite happily on the regular Netbook Remix.

---

### Post by Mizukusai on 2009-10-21
There is still the physical shutdown button which is supposed to show you the menu halt/reboot/sleep/hibernate, isn't it ?

---

