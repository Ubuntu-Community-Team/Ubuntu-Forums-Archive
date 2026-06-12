---
title: "How do I cleanup update cache?"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2007-02-08
First question: Where are the locations of the "cached" (i.e. downloaded from the Internet) packages used to perform the update installation? (by Synaptic, Aptitude, etc.)

Second question: After they are installed, the system doesn't need those package files anymore, right?

If so, does the system get rids of them automatically? Or do I have to manually delete them in order to free some disk space?

Thanks,
Alex

---

### Post by taurus on 2007-02-08
Synaptic has an option to remove it once it's finished installing an app.  Otherwise, you can clear out your cache from a terminal with

```
sudo aptitude clean
```

---

### Post by xp_newbie on 2007-02-09
> **taurus said:**
> Synaptic has an option to remove it once it's finished installing an app.  Otherwise, you can clear out your cache from a terminal with
```
sudo aptitude clean
```

Thank you!

I have one more question: I heard that aptitude and Synaptic use different cache and subsystem. That is, Synaptic is a GUI frontend to apt, not aptitude. Is this true?

If so, is there way to make both systems (i.e. Synaptic/apt vs. aptitude) agree on what's currently installed? If so, what is the proper way of doing that?

Thanks,
Alex

---

### Post by bobpaul on 2007-02-23
> **xp_newbie said:**
> I have one more question: I heard that aptitude and Synaptic use different cache and subsystem. That is, Synaptic is a GUI frontend to apt, not aptitude. Is this true?

If so, is there way to make both systems (i.e. Synaptic/apt vs. aptitude) agree on what's currently installed? If so, what is the proper way of doing that?


Synaptic, aptitude, and apt-get are all front ends to the APT libraries, and thus dpkg. According to the apt-get man page, apt-get is considered a "back-end" tool where as the other two are considered "front-ends". They all use the same major config and cache folders, namely /etc/apt and /var/cache/apt

The major difference between apt-get and aptitude--from a user perspective--is that aptitude will, by default, install recommended packages as well as required packages, so you might have extra stuff installed if you don't supply the -R option. Also, aptitude will automatically remove dependent packages if they aren't required by anything else, and if there's an error in what you are trying to do, aptitude will suggest possible solutions ranked according to how much trouble it thinks it will cause you. Apt-get will just through an error.

I prefer to use aptitude, but do a lot of mixing. I don't know where people got it in their heads that they are incompatible. Expect to see responses to my post saying you will run into major trouble if you mix them; I'm pretty sure that's due to people poorly choosing from aptitudes possible solutions--I have had trouble with that myself.

---

### Post by xp_newbie on 2007-02-25
> **bobpaul said:**
> Synaptic, aptitude, and apt-get are all front ends to the APT libraries, and thus dpkg...

Wow! Great - and helpful - answer - thanks!

Alex

---

