---
title: "This is now driving me crazy"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by pod25 on 2006-09-09
I'm still trying to install the ubuntu-desktop onto my server version.
My first few attempts failed with the error --fix-missing ?

I've edited my sources.list to include hashed out sites, but still no luck.
I've also tried removing the "gb" from the web address (saw that in a previous post) and now I get "Couldn't find package ubuntu-desktop.

I've and tried several suggestions from previous posts.
The main culprit is :
> Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.7-0ubuntus_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.7-0ubuntus_i386.deb)
I think the reason could be, it's looking for libsexy2_0.1.7 when it should be looking for libsexy2-dbg_0.1.7 ?
Can someone please suggest a fix for this because I'm banging my head against a wall here.

Thanks.

---

### Post by taurus on 2006-09-09
Why don't you post your /etc/apt/sources.list here so others can have a look at it!  Also, did you do something like

```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

---

### Post by pod25 on 2006-09-09
> **taurus said:**
> Why don't you post your /etc/apt/sources.list here so others can have a look at it!  Also, did you do something like

```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

I did do:
sudo apt-get update
sudo apt-get install ubuntu-desktop

And call this a HUGE coincidence, but I also went to the url that was causing the problem using my other comp, I then manually downloaded the missing file(not that I could do anything with it) to see if it would download. I then tried my desktop install again, and BLOW me away with a feather, the damn thing worked  :???:  And believe me, i've been at this all bloody day.

I'm now a happy bunny and can get on with setting up a working web and mail server  :-|  Something tells me I'm gonna need all the luck here.

---

