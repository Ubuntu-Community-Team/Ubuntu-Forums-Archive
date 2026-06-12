---
title: "Medibuntu update issues"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by ray field on 2012-07-01
I've tried everything I can think of -- instructions for installing GPG keys, changing the source download location, ticking off source code -- but I can't seem to get Update Manager to update these. Every time I try, I get the "Requires installation of untrusted packages" popup - under details, it gives

```
libavcodec-extra-53 libavformat-extra-53 libavutil-extra-51 libpostproc-extra-52 libswscale-extra-2
```

---

### Post by ray field on 2012-07-03
ba dump

---

### Post by raja.genupula on 2012-07-03
> **ray field said:**
> I've tried everything I can think of -- instructions for installing GPG keys, changing the source download location, ticking off source code -- but I can't seem to get Update Manager to update these. Every time I try, I get the "Requires installation of untrusted packages" popup - under details, it gives

```
libavcodec-extra-53 libavformat-extra-53 libavutil-extra-51 libpostproc-extra-52 libswscale-extra-2
```

open your terminal and try to install . In terminal its going to give you the same thing , but here you can allow it by giving yes(Y).

---

### Post by Frogs Hair on 2012-07-03
The packages that are listed show up in synaptic , but the upgrade option is not applicable.Either I have the latest versions or the packages can not be upgraded yet.

---

### Post by ray field on 2012-07-03
> **raja.genupula said:**
> open your terminal and try to install . In terminal its going to give you the same thing , but here you can allow it by giving yes(Y).

thanks, that worked. however, I feel like I should be concerned about trusting an application to update itself if the GPG key verification isn't up-to-date -- or should I?

---

### Post by raja.genupula on 2012-07-04
> **ray field said:**
> thanks, that worked. however, I feel like I should be concerned about trusting an application to update itself if the GPG key verification isn't up-to-date -- or should I?

update your cache twice . one time with un-selecting all the check boxes in the Other software TAB at update manager settings . Then update the cache again by selecting all the check boxes from the Other Software TAB . 


hope this gonna solve your issue .

---

### Post by ray field on 2012-07-04
> **raja.genupula said:**
> update your cache twice . one time with un-selecting all the check boxes in the Other software TAB at update manager settings . Then update the cache again by selecting all the check boxes from the Other Software TAB . 


hope this gonna solve your issue .


thanks -- that sounds logical.

I am going to wait until it happens again, however. for one thing, my list of PPA has 30 or 40 entries and a number are unchecked, so I'll need to keep track & right now it doesn't seem like a fruitful use of my time. will repost when the situation arises again.

---

### Post by raja.genupula on 2012-07-05
Ok for now mark the thread as solved and in future if issue raises again , then you can bump this thread and unmark as solved .



                                         Thank you :)

---

### Post by dino99 on 2012-07-05
> **ray field said:**
> thanks -- that sounds logical.

I am going to wait until it happens again, however. for one thing, my list of PPA has 30 or 40 entries and a number are unchecked, so I'll need to keep track & right now it doesn't seem like a fruitful use of my time. will repost when the situation arises again.

sudo  apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

):P

---

### Post by ray field on 2012-07-05
> **dino99 said:**
> sudo  apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

):P

WOW looking forward to trying this one, kind thanks!

---

