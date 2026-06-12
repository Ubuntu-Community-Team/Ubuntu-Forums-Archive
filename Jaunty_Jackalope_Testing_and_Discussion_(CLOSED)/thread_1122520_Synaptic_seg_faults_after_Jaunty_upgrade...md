---
title: "Synaptic seg faults after Jaunty upgrade.."
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Pablo Pablovski on 2009-04-11
Hey, all.
Upgraded from Intrepid to Kubuntu Jaunty during the week, and I've come across a problem - sudo apt-get update, Synaptic and Adept all produce "segmentation fault" when I run them.

I was able to apply updates immediately after the Jaunty upgrade, this new behaviour only started yesterday.

Oh yeah, and while Jaunty is working fine otherwise - hada  few issues with Compiz and (weirdly) Konsole, it takes much longer to boot than did Intrepid. I've attached a bootchart showing today's boot timing - I guess these things may be related. Looks like it's hard disk activity that's taking the time, but I'm not sure how to approach fixing that.

Any ideas? Any diagnostics I can run?

Spec:
AMD 3500+, 
2GB RAM
20GB / with 11GB free

---

### Post by Pablo Pablovski on 2009-04-12
Looks like a faulty apt cache. I cleaned the bin files from it:

```
sudo rm /var/cache/apt/*.bin

```

And it's working properly again.

---

