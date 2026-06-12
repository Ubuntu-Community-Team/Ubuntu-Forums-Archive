---
title: "Is there a difference between mirrors?"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-10-21
I sometimes get "Your system is up to date" even after several days passed. Switching to a different mirror then offers me substantial update as expected during development.

Today the mirror in Japan is "Up to date" while Taiwan offers a "Partial upgrade".

If there are differences, could this effect the stability of the system?

Michael

---

### Post by inportb on 2009-10-21
Given sufficient time, there should be no difference. Mirroring does not occur instantaneously, y'know.

---

### Post by 23meg on 2009-10-21
Yes, different mirrors will be in different states at any given time.

You can check how up to date your mirror is at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).

---

### Post by Nerd King on 2009-10-21
They're definitely different. The Thai mirror is frequently pretty hopeless to be honest, often lacking files let alone managing to be up-to-date. The first thing I do on any install is switch to the US mirror.

---

### Post by Paqman on 2009-10-21
> **Yumi said:**
> 
If there are differences, could this effect the stability of the system?


Definitely. That's why you should avoid doing partial updates. If they're caused by your mirror not being in sync, then you'll be left with dependency problems, and all sorts of packages getting uninstalled that really shouldn't be.

---

### Post by ikisham on 2009-10-21
Also (don't ask me exactly why) the Update Manager may not offer any updates, like you said, but go to the command line and ```
sudo apt-get update && sudo apt-get dist-upgrade
```and you'll see the whole bunch of them.

---

### Post by VMC on 2009-10-21
> **23meg said:**
> Yes, different mirrors will be in different states at any given time.

You can check how up to date your mirror is at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).

First time seeing this. Very helpful. There were a couple that are 1 month old!

---

### Post by Yumi on 2009-10-22
Thanks for all the advice. If I am on a mirror which is not updated for a week or more - it will not update. And if I change to a mirror with a older image, it might play havoc with dependencies and versions.

It explains perfectly some of the weired effects I had and which I was blaming (sorry) on the developers of Karmic.

I will avoid switching in future and select a mirror from the list which keeps up to date.

Michael

---

### Post by Paqman on 2009-10-22
> **Yumi said:**
> And if I change to a mirror with a older image, it might play havoc with dependencies and versions.


It shouldn't do. The package manager will only upgrade a packge if all the dependencies are satisfied. If you switched to an even older mirror you'd just get less updates.

Prepare for a mondo update if you do switch to a more current mirror though.

---

