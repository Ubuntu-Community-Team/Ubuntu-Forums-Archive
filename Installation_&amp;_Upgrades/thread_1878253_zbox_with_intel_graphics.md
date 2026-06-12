---
title: "zbox with intel graphics"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by Unicate on 2011-11-09
hi everyone!

I bought myself a zotac zbox barebone with intel graphics an want to run an ubuntu with xbmc on that.

The story:
First I wanted to use a debian for that just because I felt like it (no special reason)
After I successfully installed the xbmc, it worked like a charm except the graphics. The menu already was more a diashow than anything else.
My first suggestion: graphic drivers
So I searched a while till I found that: intellinuxgraphics.org 
I didnt want to build the drivers by myself, I guess you know how long that stuff can take.

So I've seen that there're some ubuntu packages with this drivers already. (yes later I figured out that they're in the kernel already...)

So what I did, I installed a ubuntu (oreiric net_install) on that zbox with normal gnome on it, then I installed the xbmc(there is a script for oreiric) and xorg packages.

Worked perfect so far, except that all the time I wanted to watch something gnome booted up and THEN finally xbmc. Well I thought, that if I would install an ubuntu without the gnome (and dmlight and all that stuff) it would work as same as good.
FAIL. It didn't.

I checked on which driver the kernel loaded it is "i915"

Please help I dont know what else todo now. (btw: why does ubuntu does not have an xorg.conf)

onboard graphics with Intel GMA 3xxx (thats everything I could figure out about the graphics hardware)

---

### Post by mikewhatever on 2011-11-09
OK, so you've installed 'an ubuntu without the gnome (and dmlight and all that stuff)', and it worked. What's the problem now?

Xorg.conf was dropped a long time ago. Why? Why not? Create it if you need it.

---

### Post by Unicate on 2011-11-09
Sorry I forgot to write that it does not work...

Problem is that the graphics on the ubuntu without gnome doesnt work.
And I have no clue why.

Well it does work but not as fluid as with gnome installed. what could that be (sorry my questionmark does not work on that keyboard :| )

PS: Where do I setup my display settings then

---

### Post by mikewhatever on 2011-11-09
Thanks for clarifying the issue. Not really sure why it doesn't work.

As said above, you can either manually create xorg.conf or generate it with the 'Xorg -configure' command. That should be run as root, so the sequence of the steps should look like this:

```

sudo -i

Xorg -configure

mv /root/xorg.conf /etc/X11/xorg.conf

exit

```

---

### Post by Unicate on 2011-11-09
Tried that already, and the X-Server is running with that configuration.
But as long as I dont know what I have to change, it does not help me :(

Anyway, where does ubuntu stores the i.e. display resolution if there is no xorg.conf

---

