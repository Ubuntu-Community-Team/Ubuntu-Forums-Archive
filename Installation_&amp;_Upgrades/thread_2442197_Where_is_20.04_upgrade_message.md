---
title: "Where is 20.04 upgrade message"
date: 2020-04-30
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2020-04-30
A question. I am at 19.10 and I have been doing "**updates**" every day the past two weeks with the software updater and have "**for any new version**" selected for "notify me of a new Ubuntu version". I have not gotten any notification from the software updater that a 20.04 **upgrade** is available. Is there some kind of problem(s) holding up things? I can install it via the terminal but want to make sure their isn't some major issue in background holding up 20.04. Can anyone tell me if it is safe to g to 20.04? ....just being cautious. And if it is ok to install, can I do it via the updater rather than the terminal. If so, how do I get the updater to do the upgrade? Many thanks for the answers to my questions!

---

### Post by Bashing-om on 2020-04-30
jgwphd; Hello -

The normal upgrade channel will open with the 20.04.1 release. Until that time 20.04 remains in the development state.

[INDENT]hope that helps
[/INDENT]

---

### Post by jgwphd on 2020-04-30
Ok, when do we expect 20.04.1 to be "released" and are things being held up due to problems. I am looking to install a stablel version. Thanks

---

### Post by wildmanne39 on 2020-04-30
It is due to be released on July 23rd 20/20 according to:

[https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule](https://wiki.ubuntu.com/FocalFossa/ReleaseSchedule)

---

### Post by jgwphd on 2020-04-30
Ok, I'll wait till July 23rd. Many Thanks!

---

### Post by Virus692 on 2020-04-30
> **jgwphd said:**
> Ok, I'll wait till July 23rd. Many Thanks!

[https://linuxconfig.org/how-to-upgrade-ubuntu-to-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-upgrade-ubuntu-to-20-04-lts-focal-fossa)

you can also run the following in terminal now...
```
$ sudo apt update 
$ sudo apt upgrade
$ sudo apt dist-upgrade
```

---

### Post by Impavidus on 2020-05-01
The upgrade from 18.04 to 20.04 will be available shortly after 23 July, when 20.04.1 is supposed to be released. The upgrade from 19.10 to 20.04 will be available well before that, considering that 19.10 will reach end of life on 17 July. It could be made available at any time, but I'm not aware of any announced date. It's normal that this takes up to about two weeks after release, although usually just a few days.

If there's a delay, it's because of a problem with the upgrade process, not a problem with 20.04 itself.

---

