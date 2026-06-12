---
title: "Slow/No Internet"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by meo on 2005-06-08
I just installed Ubuntu on my computer a few weeks ago.  When I first reinstalled it, the internet was working just fine, but more often than not, when I log in, it doesn't work.  I do have my computer partitioned so it runs Windows on half (where the internet works perfectly), and Ubuntu on the other half.  I also share the internet connection with my family, so we have a router.  When I am connected to the router, it either works just fine or I don't get anything at all.  When I am connected directly to the DSL modem, I can get internet access to get my email, but the web browsers and other internet-based programs don't work, and anything that does work is extremely slow.

If anyone has any idea what I could do, please let me know.  Thanks.

---

### Post by PhilippWollermann on 2005-06-08
How are you connected to the router? I guess using standard ethernet cable and not using WLAN?
Please boot the PC and when you're in a state that the internet works perfectly in Ubuntu, do an ifconfig -a and save it somewhere.. then boot again until internet connection doesn't work and do an ifconfig -a again. There should be some differences like failing to get an IP address (experienced some very strange things like DHCP not working sometimes with my router, too). If you can't spot anything, you could post both outputs here.

You could also try using a static IP address / static gateway / static DNS, if you know, how to configure Ubuntu this way. :)

It would also help to know, which router you've got.

Philipp

---

