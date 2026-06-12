---
title: "after 10.4 update DVI has no display unless VGA monitor is connected"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by DrKlingmann on 2011-07-20
I've updated ubuntu to 10.4 and I wanted to view everything on my panasonic TV as I did on previous version.
But unfortunately my TV doesn't display anything unless I connect other monitor to VGA connector while booting my system.
My card is radeon 9100.
I recall having such a problem (or similar one) on previous version.. but I don't remember solution..

---

### Post by MAFoElffen on 2011-07-20
> **DrKlingmann said:**
> I've updated ubuntu to 10.4 and I wanted to view everything on my panasonic TV as I did on previous version.
But unfortunately my TV doesn't display anything unless I connect other monitor to VGA connector while booting my system.
My card is radeon 9100.
I recall having such a problem (or similar one) on previous version.. but I don't remember solution..
Welcome to Ubuntu Forums.

There are 2 ways to do this...  Both ways would need you to connect something to your ports of your card... Then do these commands and post the results:
```

sudo lspci -v | grep VGA
xrandr -q
sudo hwinfo --frambuffer
cat /etc/X11/xorg.conf

```
The first of the ways is to get the data returned from xrandr and use it and the names returned to manually turn off and on the ports.  If you want to do this persistent, then you create an .xprofile file to do it.

The second way is to add the definitions using data from above, to the xorg.conf file...

---

