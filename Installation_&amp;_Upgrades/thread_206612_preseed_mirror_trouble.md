---
title: "preseed: mirror trouble"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by aSa on 2006-06-30
Hi everybody,

How do I restrict preseeded, local network installation system getting any "install information" from internet and use only the local install image from my server?

I already have these (see below) standard local mirror settings, and this system did work for a while.  Now if I have internet access connected to my local lan, installation fails trying to find (changed version?) binutils-static-udeb from my local server.  I would like to install machines with plain 6.06 base and afterwards use different mirror settings for proper updating (if needed).  I do not want to start building a full size Ubuntu mirror server nor switching my ADSL box off everytime I need to install Ubuntu.

```
### Mirror settings
d-i mirror/country string enter information manually
d-i mirror/http/hostname string 10.10.10.254:80
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
```

I hope you could give me a clear and simple solution I have missed somewhere.

Thanks in advance,
     aSa

---

