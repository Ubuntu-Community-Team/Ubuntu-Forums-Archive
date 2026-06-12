---
title: "Software installation question"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by lonekingc4 on 2012-02-10
Hi. I am using Ubuntu 11.10

When I install a software from the software center, it downloads the software and then installs. But when I remove the software completely (using synaptic or software center), the software is removed. But when I try to install it again, it doesn't download but installs instantly as if the files weren't deleted. I was wondering how does it happen?

Cheers.

---

### Post by WthIteh on 2012-02-10
> **lonekingc4 said:**
> Hi. I am using Ubuntu 11.10

When I install a software from the software center, it downloads the software and then installs. But when I remove the software completely (using synaptic or software center), the software is removed. But when I try to install it again, it doesn't download but installs instantly as if the files weren't deleted. I was wondering how does it happen?

Cheers.
It caches downloaded .deb files in /var/cache/apt/archives/ folder.
That cache can be cleared using "sudo apt-get clean".

---

### Post by lonekingc4 on 2012-02-10
> **WthIteh said:**
> It caches downloaded .deb files in /var/cache/apt/archives/ folder.
That cache can be cleared using "sudo apt-get clean".

Ah I see. Thanks :D

---

