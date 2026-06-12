---
title: "security"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by bigmac_bb63 on 2006-10-18
I am unable to install automatic updates. I followed the page exactly and it says that there is no such directory? What is going on? 
With Redhat Fedora you just "yum update" with this ???? you got me?
I am getting into root as "sudo -i" is this right? I can't find the proper documentation on it? Funny, I've been using Linux for two years and this OS has me completelly stumped. I am frustrated because I want to automatically have the OS download security updates and every time I try it says "no such directory". Whether I use root or my username and password it still says the same thing? Either this OS works properly or it doesn't?

I could sure use some help - thanks.

bigmac_bb63](*,)

---

### Post by taurus on 2006-10-18
From a terminal (as a regular user), run

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by TheWizzard on 2006-10-18
i moved from fedora to here a few months ago. there are some things differently organised in debian/ubuntu, but it's easy to get used to it. there's good community help here. check the wiki's and howto pages.  

here's some information on the root account: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

