---
title: "How to update to 10.04"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by charreedawn on 2010-03-03
I would like to update Ubuntu from 9.10 to 10.4, How would I do that,

---

### Post by Silvertones on 2010-03-03
I do believe that the Update Manager will tell you when it's avaiable.

---

### Post by spiky001 on 2010-03-03
you can download it from here [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
you might be better waitng fro proper release in april tho

---

### Post by QLee on 2010-03-03
> **charreedawn said:**
> I would like to update Ubuntu from 9.10 to 10.4, How would I do that,

If you want update manager to handle it for you (and I've done it successfully).
From the Ubuntu Lucid alpha3 page:
> 
To upgrade from Ubuntu 9.10 on a  desktop system, press Alt+F2 and type in "update-manager -d" (without  the quotes) into the command box. Update Manager should open up and tell  you: New distribution release '10.04' is available. Click Upgrade and  follow the on-screen instructions.  

Note it is "alpha", not released yet, there may still be some bugs.

---

### Post by OliW on 2010-03-03
If you need to ask, you're not ready for it.

It's very early on. It will break and you'll need to be able to work out how to fix it. Some of the time, this will involve finding things out for yourself.

Given that you couldn't Google this question, please consider being patient. Good things come to those that wait. Massive breakage comes to those that don't.

---

### Post by bodhi.zazen on 2010-03-03
> **charreedawn said:**
> I would like to update Ubuntu from 9.10 to 10.4, How would I do that,

First update your system, back up your data.

The open a terminal and run:```
gksu update-manager -d
```

=)

---

### Post by uRock on 2010-03-03
> **bodhi.zazen said:**
> First update your system, **[COLOR=Red]back up[/COLOR]** your data.

The open a terminal and run:```
gksu update-manager -d
```=)

+1 I upgraded my VBox install from Karmic to Lucid 2 weeks after Karmic was released. It has only broke and had to be reinstalled twice. That only happened because I went a couple of weeks between booting to run updates. Do them daily and everything should be fine, but do not be broken hearted if you go to restart after an update and it doesn't make it past grub.

---

### Post by 23meg on 2010-03-03
> **bodhi.zazen said:**
> First update your system, back up your data.

The open a terminal and run:```
gksu update-manager -d
```

=)

There's no need to run Update Manager as root. ```
update-manager -d
``` will suffice.

---

### Post by Robledo on 2010-03-19
> **OliW said:**
> If you need to ask, you're not ready for it.

It's very early on. It will break and you'll need to be able to work out how to fix it. Some of the time, this will involve finding things out for yourself.

Given that you couldn't Google this question, please consider being patient. Good things come to those that wait. Massive breakage comes to those that don't.


Is it goint to be very bad. I mean for beginners? I also couldn`t wait.  You are very right. But even we are beginers why we are here is, because we want to explore, new things every day. That what makes it exiting.
I can always start from scratch, no data loss. So I understand rookies who update too early. WE NEED THE CHALLANGE OTHERWISE WE USE APPLE.

---

### Post by cariboo on 2010-03-19
> **Robledo said:**
> Is it goint to be very bad. I mean for beginners? I also couldn`t wait.  You are very right. But even we are beginers why we are here is, because we want to explore, new things every day. That what makes it exiting.
I can always start from scratch, no data loss. So I understand rookies who update too early. WE NEED THE CHALLANGE OTHERWISE WE USE APPLE.

Please don't make empty threats about going to another operating system. Checking out the [Release notes]("http://www.ubuntu.com/testing/lucid/alpha3"), it is always a good idea before trying an unreleased version. The one linked to is for  alpha 3, as the beta has just been released, the upgrade works the same way.

---

