---
title: "apt-get udpate does not work"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by remush on 2009-12-01
I've just done an install of ubuntu server 9.10 and the first thing I did after rebooting for the first time is

>sudo apt-get update

To be told that au.archive.ubuntu.com is not available (sorry I dont have the exact error)

I've found that when installing recent versions of Debian and Ubuntu and setting my location as Australia, apt-get does not work once install is done.

Can someone please post a working sources.list file for australia ? 

I'm not sure how to post the error messages I'm getting as ubuntu server has NO gui.

---

### Post by Megafag on 2009-12-01
> **remush said:**
> I've just done an install of ubuntu server 9.10 and the first thing I did after rebooting for the first time is

>sudo apt-get update

To be told that au.archive.ubuntu.com is not available (sorry I dont have the exact error)

I've found that when installing recent versions of Debian and Ubuntu and setting my location as Australia, apt-get does not work once install is done.

Can someone please post a working sources.list file for australia ? 

I'm not sure how to post the error messages I'm getting as ubuntu server has NO gui.

change all the "au.archive.ubuntu" to "au2.archive.ubuntu".

```
sudo gedit '/etc/apt/sources.list'
```

---

### Post by remush on 2009-12-01
I've already changed all relevent paths from 'http://au' to 'http://nz' however I will also try changing these entries to au2 and see what happens.

thanks for your input.

---

