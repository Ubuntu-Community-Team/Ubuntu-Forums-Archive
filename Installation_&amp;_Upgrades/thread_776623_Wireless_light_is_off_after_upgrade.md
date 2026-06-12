---
title: "Wireless light is off after upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by karuzo on 2008-04-30
Hello all,
   Just completed an upgrade to 8.04. Strange is that the built-in wireless card indicator remains off while being connected. Just curious.
I run both ubuntu and windows xp on same laptop.
Laptop is an HP pavilion dv8000.
Any thoughts?
Although I can run several commands in terminal I consider myself still new to ubuntu and linux in general.
Thanks,
    Doron

---

### Post by garyedwardjohnston on 2008-04-30
is this just about the light or your internet connection?

---

### Post by LeoSolaris on 2008-04-30
I'm using a Dell 1520, and it's wireless light has never come on in Ubuntu, despite working perfectly otherwise. It is odd that it was used in 7.10 but not in 8.04. I simply count it as 10 seconds more battery time. You could try downloading the backports for hardy, from what the forums are saying that works for a few cards.

Leo

```
sudo apt-get install linux-backports-modules-hardy
```

---

### Post by karuzo on 2008-04-30
> **garyedwardjohnston said:**
> is this just about the light or your internet connection?
I've been having problems lately utilizing my wireless router - nothing to do with ubuntu. But I can see other wireless networks so I figured it is working. Currently I am hard wired.

---

### Post by karuzo on 2008-04-30
> **LeoSolaris said:**
> I'm using a Dell 1520, and it's wireless light has never come on in Ubuntu, despite working perfectly otherwise. It is odd that it was used in 7.10 but not in 8.04. I simply count it as 10 seconds more battery time. You could try downloading the backports for hardy, from what the forums are saying that works for a few cards.

Leo

```
sudo apt-get install linux-backports-modules-hardy
```

Thanks - the light is still off.

Edit on 05-03-08 - After restarting the computer the light is back on, but remains constant. Usually when it seeks for networks it blinks which it does not do that any more. Just remains constantly on. Personally I am ok with that. Thanks,

---

### Post by karuzo on 2008-04-30
> **garyedwardjohnston said:**
> is this just about the light or your internet connection?

Just the light. I am curious as the light was on on gutsy but not now after the upgrade.

---

### Post by jaddle on 2008-05-07
I'm seeing the same thing on my lenove x60s - wireless connection is working fine, but the light hadn't turned on since upgrading to hardy. Looks like the backports module did get the light to turn on, but it doesn't work quite like it used to - previously it flickered while trying to associate with an AP, but now it's just solid as soon as it's doing anything, and I don't see it blink at all to show when data is being transferred. No huge problem, but I preferred it before...

---

