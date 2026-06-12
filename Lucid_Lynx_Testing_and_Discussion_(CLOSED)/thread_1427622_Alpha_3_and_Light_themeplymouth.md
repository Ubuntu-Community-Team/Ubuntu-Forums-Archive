---
title: "Alpha 3 and Light theme/plymouth"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2010-03-11
I read today that Alpha 3 had a new theme and a plymouth boot screen - but when i boot it up off the Live CD i'm not seeing anything new.  just the same old brown - am i missing something?

---

### Post by shafin on 2010-03-11
Yeah. You're missing
```
sudo  apt-get update && sudo apt-get  upgrade


```

---

### Post by kansasnoob on 2010-03-11
> **zoomy942 said:**
> I read today that Alpha 3 had a new theme and a plymouth boot screen - but when i boot it up off the Live CD i'm not seeing anything new.  just the same old brown - am i missing something?

You had a silent boot????????????

I'm jealous.

---

### Post by zoomy942 on 2010-03-11
> **shafin said:**
> Yeah. You're missing
```
sudo  apt-get update && sudo apt-get  upgrade


```

but i DL'd the image today - do i still need this?

---

### Post by shafin on 2010-03-11
> **zoomy942 said:**
> but i DL'd the image today - do i still need this?
Yeah, Alpha 3 image is basically a snapshot of what was in the repos when alpha 3 was released. for the latest packages you need to download the daily-live CD's.

---

### Post by zoomy942 on 2010-03-12
so i installed alpha 3, ran the update and I have the plymouth startup now but no light theme.  What am i missing now?

---

### Post by howefield on 2010-03-12
Have you looked in System > Preferences > Appearance to choose the new theme ?

---

### Post by zoomy942 on 2010-03-12
> **howefield said:**
> Have you looked in System > Preferences > Appearance to choose the new theme ?

lol.  yes sir.  i dont see Light listed.

---

### Post by howefield on 2010-03-12
> **zoomy942 said:**
> lol.  yes sir.  i dont see Light listed.

The new themes are called "Radiance" and "Ambiance". Do you see them ?

---

### Post by zoomy942 on 2010-03-12
> **howefield said:**
> The new themes are called "Radiance" and "Ambiance". Do you see them ?

negative ghost rider

---

### Post by WildWillie on 2010-03-17
For some reason, I had to apt-get install them. I googled around until I found the .debs and then gdebi informed me that a later version was available. Incidentally do you have MeMenu, because I don't.

update and all things with upgrade in their argument did nothing. I upgraded from 9.10 through apt though, so it could be that that is messing with my sources somehow, though I did in fact change sources.list.

---

### Post by zoomy942 on 2010-03-18
> **WildWillie said:**
> For some reason, I had to apt-get install them. I googled around until I found the .debs and then gdebi informed me that a later version was available. Incidentally do you have MeMenu, because I don't.

update and all things with upgrade in their argument did nothing. I upgraded from 9.10 through apt though, so it could be that that is messing with my sources somehow, though I did in fact change sources.list.

i had to do the exact same thing.  weird

---

### Post by shafin on 2010-03-18
Have you removed ubuntu-desktop earlier with some other removal? It is used to pull new packages into the install, and its always a good idea to reinstall it before dist-upgrade.

---

