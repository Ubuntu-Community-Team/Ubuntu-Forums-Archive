---
title: "Trying to isntal Java JRE, but apt says it's not there, synaptic doesnt find such."
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by StrikeRTM on 2005-06-28
Trying to isntal Java JRE, but apt says it's not there, synaptic package maneger doesnt find it ether. I have updated the package lists, but nothing has changed.

```
sudo apt-get install sun-j2re1.5
```

Now what should I do? Has the name of the package changed since last unofficial ubuntu guide update or something else?

Maybe someone has encountered this error and could help me?  :-?

---

### Post by Caboto on 2005-06-28
Tried it some minutes ago and sun-j2re1.5 is there. Have you added the [backports repository](http://ubuntuguide.org/#extrarepositories) and is the mirror you used really not down?

---

### Post by StrikeRTM on 2005-06-28
Yes, that was the problem I think. Now it works. Thanks.

Though I have a new problem. Azureus that needed the JRE has very low download speeds. The speed doesnt exeed 10kB/s. I wander if that has something to do with Firestarter firewall or iptables(didnt install iptalbe, but i think they come along in the hoary cd).

---

