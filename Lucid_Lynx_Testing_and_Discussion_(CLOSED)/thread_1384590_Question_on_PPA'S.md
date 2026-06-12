---
title: "Question on PPA'S"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2010-01-18
Has anyone tried to use any of the ppa's from [http://ubuntuforums.org/showthread.php?p=5469046?](http://ubuntuforums.org/showthread.php?p=5469046?)  Which ones work at present, if any?

---

### Post by cariboo on 2010-01-18
All of the ppa's Ived used worked the way the should, there is a new to Karmic way of adding ppa's, in Software Sources the command will look something like this:

```
ppa:yorba/ppa
```

---

### Post by mc4man on 2010-01-18
I would certainly advise that the ubuntu-tweak ppa be used with care (if at all), and that when adding any ppa(s), first go to the ppa and see what packages are in it.

While many ppa's are app specific, others contain a wide range of packages and may cause you some issues, regressions, if left enabled and you do an update thru the update manager or apt-get.
(apt-get is worse because it will remove packages to make way for updated and or new ones.

I think ppa's should be used for a specific reason and not just to add a bunch of them

---

### Post by VMC on 2010-01-18
> **mc4man said:**
> I would certainly advise that the ubuntu-tweak ppa be used with care (if at all), and that when adding any ppa(s), first go to the ppa and see what packages are in it.

While many ppa's are app specific, others contain a wide range of packages and may cause you some issues, regressions, if left enabled and you do an update thru the update manager or apt-get.
(apt-get is worse because it will remove packages to make way for updated and or new ones.

I think ppa's should be used for a specific reason and not just to add a bunch of them

I haven't added any ppa's for the various things mentioned.

---

### Post by mc4man on 2010-01-18
> I haven't added any ppa's for the various things mentioned.

The other reason here is it can 'skew' what is working or broken in lucid, though there is always two sides to a coin.

Use of ppa's in a testing release can point to what may be improved with updated and or re-configured sources and could lead to some realistic or valid feature requests/wishlists.

And in a limited sense can help those that intend to modify/update their install past the ubuntu release version ( though that would represent the vast minority of eventual users

---

### Post by zika on 2010-01-18
> **mc4man said:**
> i think ppa's should be used for a specific reason and not just to add a bunch of them+1

---

### Post by Starks on 2010-01-18
> **cariboo907 said:**
> All of the ppa's Ived used worked the way the should, there is a new to Karmic way of adding ppa's, in Software Sources the command will look something like this:

```
ppa:yorba/ppa
```
That method doesn't work with lucid unless the ppa specifically offers a lucid repo. Otherwise that command will add a non-existent lucid repo to your sources.

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/502454)

---

### Post by sports fan Matt on 2010-01-18
What are all these "disabled on upgrade to lucid" in source list..they worked well in karmic, could it be they don't have repos for lucid yet?

---

