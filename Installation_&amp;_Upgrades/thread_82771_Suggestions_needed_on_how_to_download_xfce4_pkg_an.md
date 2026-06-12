---
title: "Suggestions needed on how to download xfce4 pkg and depencies? (Solved)"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by Blackie_Chan on 2005-10-27
Hi all, 

I'm in the process of install xfce4 on a old computer. So far, I've done a 'server' installation. Now I'll like to use xfce4. The problem is xfce4 has a lot of dependencies and it'll take a lot time to go to packages.ubuntu.com/hoary and download every single dependency one by one.

So, what's the best approach to download and install xfce4 on the computer? By the way, I don't have internet access on the computer, so I'll have to download everything, put it on a usb drive and transfer it over.

Thanks in advance.

---

### Post by Blackie_Chan on 2005-10-27
I found the solution to my problem, I just needed to run the following command on one of my other ubuntu machines (what has an internet connection).

```
apt-get -d install xfce4  
```

That would download all the packages into /var/apt/cache/archives

---

