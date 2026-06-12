---
title: "Installed Kubuntu, Not Working"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by Lambert on 2005-06-24
I was able to get kubuntu installed but when I boot from drive I can't get kubuntu to work.

When I boot up it loads everything and starts kde. The screen goes to a graphic showing the kubuntu logo, a cursor at center screen and then stops. There are no bars or icons in view and I can not move cursor. 

I can load up in recovery mode.

Can anybody help?

---

### Post by ltmon on 2005-06-24
Can you get hold of and attach the following file to your post:

/var/log/Xorg.0.log

It may hold the answer if we're lucky :)

Cheers,

L.

Edit: Also, when you are locked up, does the key combination CTRL-ALT-F1 allow you to go to console mode.  Also, when you start in safe mode, can you succesfully run 

> /etc/init.d/kdm start

Cheers,

L.

---

### Post by Lambert on 2005-06-25
I'm on dial up and my current provider doesn't allow a generic dialer, have to use theirs which doesn't work on a linux os. So I can't get that log.

I tried ctrl alt f1 and nothing happens, system just freezes.

I went ahead and cleaned the drive and tried ubuntu. I can get to the log in screen but after I type my log in exact same thing happens.


I did write /etc/init.d/gnm start and it brought up the login screen.  Same thing though, it just freezes.  Are there any graphic config I need to do maybe? I'm running an rs480ml mobo from msi with integrated ati radeon x200 graphics. I've read that ati has been known for poor linux support?

---

