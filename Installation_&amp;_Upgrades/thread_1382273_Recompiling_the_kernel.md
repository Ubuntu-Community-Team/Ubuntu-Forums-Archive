---
title: "Recompiling the kernel"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by dmcfarland on 2010-01-15
I need to recompile my current kernel, because I need to add uniput support to it. May I get a link or a walkthrough on how to do that so I don't hose my system up. Thanks

---

### Post by Leppie on 2010-01-15
there is a guid here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

please note:
> [SIZE="6"][COLOR="Red"]Reasons for NOT compiling a custom kernel[/COLOR][/SIZE]
You merely need to compile a special driver. For this, you only need to install the linux-headers packages.
You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratch.
You got to this page by mistake, and checked it out because it looked interesting, but you don't really want to learn a lot about kernels.

---

### Post by Techsnap on 2010-01-15
I might be wrong but I think that Ubuntu already has the uinput module, search synaptic if not. Try:

```
sudo modprobe uinput
```

---

### Post by dmcfarland on 2010-01-15
I am trying to get my g11 gaming keyboard to work and yes I have read the guide and that guide is mostly concerned with making a new kernel. I am trying to add uinput support for my kernal so I can get my keyboard fully operational. I would also like to know if there is a way to get around that so I don't have to go through all that trouble.

---

### Post by dmcfarland on 2010-01-15
I tried that and it just shot me back to the command prompt. Is that good?

---

### Post by Leppie on 2010-01-15
yes, it only shows a message if it fails ;)

---

### Post by dmcfarland on 2010-01-15
Ok. Now I need to post a thread about configuring the g-11 "g" keys. Thanks

---

### Post by Leppie on 2010-01-15
i'm not sure, but i'd say it should be similar to the g15 procedure: [https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

---

### Post by dmcfarland on 2010-01-17
I have done all that and no luck. Am I sol because I have a g11 keyboard?

---

