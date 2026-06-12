---
title: "CPU upgrade: P4-&gt;Core2duo under Feisty"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by jboehm on 2007-05-07
I specifically bought my motherboard so that I could drop in a Core2duo when the prices came down.  I'm currently running a P4 on it under Feisty.  What do I need to do when I go to upgrade the CPU?  Anything?  I'm currently running the stock 2.6.20-15-386 kernel.

Thanks,
Jon

---

### Post by veloce on 2007-05-18
That kernel will run, but you won't get SMP.  I'm not sure how to change over but I think you can do it with apt.

---

### Post by mikewhatever on 2007-05-18
You'll need to install 2.6.20-15-generic kernel. Should be in the repositories.

---

### Post by jboehm on 2007-05-18
Thats it??

sudo apt-get 2.6.20-15-generic

And things just work??  Wow, I hope it turns out to be that easy.

Thanks,
Jon

---

