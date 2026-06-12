---
title: "Low screen resolution after upgrading"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by Dillon3212 on 2013-05-06
I have just downloaded and installed a raft of upgrades for ubuntu. Before the upgrades I was running a screen res of 1280 x 1024. Now, the best resolution I can get (on gnome or KDE) is 1024 x 768. 

Can anyone hlp please?

---

### Post by MAFoElffen on 2013-05-06
Please post the results of:
```

glxinfo | grep -i opengl
lspci -nnk | grep -iA3 VGA
/usr/lib/nux/unity_support_test -p

```
So your prefix says [ubuntu]... but you mentioned KDE and Gnome. Is your Ubuntu based or KDE

---

### Post by Dillon3212 on 2013-05-06
Hi,

I have the std ubuntu desktop and the KDE desktop and I switch between them as required, but screen resolution is the same on both.

---

### Post by MAFoElffen on 2013-05-06
So info back from was I asked will tell me what drivers you have currently installed, the Video GPU installed (as Linux sees it) and the video a capabilities of what is installed. Also what may be help is to attach your /var/log/Xorg.0.log file. That would tell me what drivers are loading and what hardware it is seeing with what capapbilities.

Usually this is just a driver thing. Remove and reinstall. But a little research will tell that, tell what is going on and what needs to be done and how it needs to be done, with what. Better to have a plan of attack than to got blinding changing things, making more of a problem to have to fix.

I'll be in and out all day. I have some loggers to talk with about landings, some custom signs to route for someone... Have a few things to do for my son's wedding... And I have to do some coding on one of my new program's projects, so I will keep an eye on this thread.

---

