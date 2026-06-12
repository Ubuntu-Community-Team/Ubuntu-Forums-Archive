---
title: "Really spotty wireless in Karmic?"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phrizek on 2009-10-22
Is anyone else experiencing a similar issue? I have installed the 9.10 beta on two machines, both of which had wireless working with previous versions of ubuntu. I can connect to my wireless network, but some sites are incredibly slow, and often fail to load. Mind you, these sites include google and amazon, so I'm sure it's not my connection. Other sites work fine and load up fast. If I plug in an ethernet cable, the sites no longer load slowly, and all works as it should. If I reboot into windows, wireless works perfectly, so it isn't my hardware. Anyone experience a problem like this and are there any known fixes?

Thanks.

---

### Post by jomtois on 2009-10-22
I have a Broadcom Wireless 4312 card and I have experienced similar issues.

I got a lot of this in my syslog:

```
Oct 22 20:20:17 jon-laptop kernel: [ 6100.719183] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:18 jon-laptop kernel: [ 6101.743167] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:19 jon-laptop kernel: [ 6102.767167] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:20 jon-laptop kernel: [ 6103.791205] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:21 jon-laptop kernel: [ 6104.712936] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:22 jon-laptop kernel: [ 6105.736966] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b40
Oct 22 20:20:37 jon-laptop kernel: [ 6120.994939] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=eda66b
```

I filed this bug:
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/453647](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/453647)

One thing I have tried tonight that seems to be working so far as a "workaround" is to go into my wireless router and disable TKIP.  Now it only uses AES encryption and I haven't been getting the issues, but it would usually happen after awhile of being logged on so I am still crossing my fingers.

Maybe this will help.

---

