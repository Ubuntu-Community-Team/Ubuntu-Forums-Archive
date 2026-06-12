---
title: "Sun Java JRE in Karmic: how-to for security updates"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Pjotr123 on 2009-10-20
Sun Java JRE in Karmic has been abandoned in favour of OpenJDK. This means, that the current JRE packages in the repositories of Karmic, won't be updated and will probably even be removed.

If they won't be removed, you'll need to take care of security updates for JRE yourself. By installing a new version manually.

The current JRE packages in the repositories for Karmic are still secure (update 15), but no longer the most recent (that's update 16).

I've written a how-to for installing JRE manually. Both for 32 bit and for 64 bit Ubuntu 9.10. You can find it here:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Hope this helps. :)

---

### Post by aim on 2009-10-20
I guess somebody (maybe even sun) will create a ppa with sun-jre. it's a very important package to be abandoned.

---

### Post by alexcckll on 2009-10-23
Why on earth was that done?  Why not negotiate with Oracle and get Sun Java into the Partner repo?  Same as is done with Adobe and Acrobat?

I'm now scared that when I update to the next LTS whenever it comes out - that I'll be cut off from the chat sites I use?

---

### Post by edin9 on 2009-10-23
Does OpenJDK work fully now?

---

### Post by steeleyuk on 2009-10-23
> **edin9 said:**
> Does OpenJDK work fully now?

I've heard it does work in 99% of cases. I'm going to give it a go now anyway...

---

### Post by philinux on 2009-10-23
> **alexcckll said:**
> Why on earth was that done?  Why not negotiate with Oracle and get Sun Java into the Partner repo?  Same as is done with Adobe and Acrobat?

I'm now scared that when I update to the next LTS whenever it comes out - that I'll be cut off from the chat sites I use?

Adobe acrobat is still missing from the 64 bit repos.

[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/437566](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/437566)

---

### Post by Keyper7 on 2009-10-23
> **edin9 said:**
> Does OpenJDK work fully now?

It passed the Java SE 6 Test Compatibility Kit. As far as I know, this means Sun says it does.

---

