---
title: "Samba Issue - Karmic Only."
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Roasted on 2009-08-03
I noticed something on Karmic that I figured was worth pointing out.

I am running Ubuntu Jaunty 64 bit with Samba. I have 5 shares. 4 of them are single names, example - Bob. The last one is Spare_Storage.

I have both Ubuntu Hardy Heron 32 bit and Ubuntu Karmic 32 bit installed on Ubuntu Jaunty in a VM with VirtualBox.

If I connect to my Jaunty Samba server with Karmic, all shares show up except Spare_Storage. If I connect to the Jaunty Samba server with Hardy, all shares show up.

I changed the "display" to SpareStorage and it showed up, despite the true path still being Spare_Storage.

Turns out, Samba shares containing an underscore don't show up in Karmic. But show up fine in Hardy and other OS's accordingly.

---

