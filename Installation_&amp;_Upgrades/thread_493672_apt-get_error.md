---
title: "apt-get error"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by zoobave on 2007-07-06
Hi,
     When i try to install the Mozilla NSS development package, i got the following error. How can i resolve this?


```
root@dvm-desktop:/home/dvm/mono/moon# apt-get install  mozilla-nss-devel
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mozilla-nss-devel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-nss-devel has no installation candidate
root@dvm-desktop:/home/dvm/mono/moon#                       
```




regards
Zoobave
[http://zoobave.blogspot.com/]("http://zoobave.blogspot.com/")

---

### Post by kevinlyfellow on 2007-07-06
Try 
```

sudo apt-get install libnss-dev

```

Its for firefox and not mozilla (old seamonkey) but it may work

---

### Post by zoobave on 2007-07-06
Thanks. It works. Then how to install
 the **"Mozilla XPCOM development package"**



regards
Zoobave
[http://zoobave.blogspot.com/]("http://zoobave.blogspot.com/")

---

### Post by kevinlyfellow on 2007-07-06
I think you need to install the development version of firefox (or mozilla, same thing, just replace firefox with mozilla, sorry)
```
sudo apt-get install firefox-dev
```

I may be wrong though...

If you know spanish, here is a howto: [http://magarto.com/blog/archivo/2007/06/23/howto-instalar-moonlight-en-ubuntu/](http://magarto.com/blog/archivo/2007/06/23/howto-instalar-moonlight-en-ubuntu/)
But from what I understand from that, it doesn't seem to provide you with much information.

When you get [moonlight installed, let me know how it is.]("http://www.mono-project.com/Moonlight#Getting_Started")

---

