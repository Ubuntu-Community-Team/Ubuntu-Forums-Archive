---
title: "reuse your existing installation on a new computer"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by eentonig on 2008-04-04
If you're buying or getting a new computer and you don't want to reinstall your whole setup, you could just install the old Hard drive in the new computer.

This is especially usefull if you are running Ubuntu from an USB HD like me.

I already tried this on three different computers (1 desktop and 2 laptops)

If your GPU is from the same manufacturer, chances are you'll be in business without any hassle. If your GPU manufacturer is from different brands, you'll have to reconfigure X. Just boot up in safe mode and issue
> dpkg-reconfigure xorg-server


I did it again last night when the HD from my companies HP nc6220 broke down and I got a Lenovo T60. I came home, plugged in my USB HD and was working on my 'own' computer in 15 minutes. (Beat this MS)

---

