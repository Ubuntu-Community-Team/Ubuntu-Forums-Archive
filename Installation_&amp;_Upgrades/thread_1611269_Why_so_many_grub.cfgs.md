---
title: "Why so many grub.cfgs?"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by bkline on 2010-11-01
I upgraded my main workstation from 10.4 to 10.10 yesterday and  was a little concerned that a kept seeing the upgrade software perform the same step of generating grub.cfg over and over.  I went back to the logs and I counted nine (9!) repetitions of this same task.  Can someone tell me what is accomplished by doing this so many times if it's all going to result in a single file?

---

### Post by Quackers on 2010-11-01
I've upgraded to 10.10 twice and I must say that I didn't notice any repetitions like that. Is your system booting alright? Does the grub menu appear to be normal and all items work?

---

### Post by oldfred on 2010-11-01
I have not upgraded for awhile but noticed it running several times on new install. I have multiple installs so it takes a minute or two so I do see it running. I thought one or two versions ago I saw a bug report complaining about it and they were going to improve it. The grub update seems to be triggers on a variety of updates, each kernel, each grub change and maybe one or two other things. It would make sense to postpone those and just once it once at the end.

---

### Post by coffeecat on 2010-11-01
> **bkline said:**
> Can someone tell me what is accomplished by doing this so many times if it's all going to result in a single file?

Quite!

I've seen something similar when uninstalling three old kernels in Lucid. The system ran update-grub after each kernel was uninstalled rather than just doing it once at the end. But I'd be interested to know what triggered nine occasions.

---

### Post by bkline on 2010-11-01
> **Quackers said:**
> I've upgraded to 10.10 twice and I must say that I didn't notice any repetitions like that. Is your system booting alright? Does the grub menu appear to be normal and all items work?

I haven't noticed any ill effects, at least not yet.  It just left me with the impression that the upgrade software wasn't quite sure what it was supposed to be doing.

---

