---
title: "Upgrading a dual boot machine"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by RFXCasey on 2009-12-03
Just updated my dual boot machine from 8.06 to 8.10 and I hope to continue without issue until I reach the latest version. When installing the updates the manager kept asking my if I wanted to keep the currently installed version of menu.lst or use a new one. Since my menu.lst is set up to reflect my dual boot setup I didn't install the new version because I didn't want to end up in a situation where I couldn't boot to my Windows XP install. I want to edit my menu.lst manually but is there a way to find out all the kernel versions I have installed do I can make the new entries? Thanks.;)

---

### Post by dhavalbbhatt on 2009-12-03
Can't you look it up in Synaptic?

---

### Post by RFXCasey on 2009-12-03
After the upgrade it won't start for me, maybe because I'm using the old kernel version? Is there any way to check it through the terminal?

---

### Post by RFXCasey on 2009-12-03
Ok well I've found how to list the installed kernels by typing

```
$ dpkg --list | grep linux-image 
```

---

