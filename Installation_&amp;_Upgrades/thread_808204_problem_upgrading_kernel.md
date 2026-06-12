---
title: "problem upgrading kernel"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Th3Professor on 2008-05-26
Has anybody any experience with kernel upgrades in ubuntu and with resolving upgrade issues that arise?

I received errors during an auto-update:
[http://ubuntuforums.org/showthread.php?t=808009](http://ubuntuforums.org/showthread.php?t=808009)

---

### Post by zvacet on 2008-05-26
If that will make you feel better this is so called dependencies hell.I will go with 

```
sudo dpkg --configure linux-image-2.6.24-17-rt
```

but I can be wrong.You have 6 packages depends on each other so if you install one of them rest will just follow.If linux-image-2.6.24-17-rt is not good start try other package.Good luck!

---

### Post by Th3Professor on 2008-05-26
I suppose I could do this also? :

sudo dpkg --configure linux-image-2.6.24-17-generic

What is so-called dependencies hell? (Not sure what you're referring to.)

You said you can be wrong - I think I'll hold off on the above commands for now. :) :) My grub is currently set to offer the -17 generic and rt kernels in its menu list, though I have a back-up of the previous menu in any case.

This all started with an auto-update, lol... I didn't even do a manual kernel upgrade, which is odd (I thought the specific ubuntu version only upgrades the kernel in the bi-annual full system upgrade). So, I went with the auto-update step, which is when is proceeded to crap on itself. :confused: I'm perfectly happy with the kernel version I'm running now, though if I can get the auto-update thing to properly complete itself, that'll be fine too.

---

### Post by zvacet on 2008-05-27
> What is so-called dependencies hell?

It is situation when one dependecy need other and other need third one and so on...

I don´t think you will be able to do updates until you resolve your currrent situation.

```
sudo dpkg --configure linux-image-2.6.24-17-generic
```

no need for that,because that one is installed properly.You need to configure packages which spitting errors.

---

### Post by Th3Professor on 2008-05-27
Alrighty... I did:
sudo dpkg --configure linux-image-2.6.24-17-rt

It looks like it worked just fine. :)

Next time I reboot hopefully it won't have any probs.

---

### Post by stanley82 on 2008-05-27
I have a problem after upgrade (AMD64) gutsy to hardy giving the initramfs thing.  I went back to the gutsy kernel and all seems to be good.  If I try your "sudo dpkg --configure linux-image-2.6.24-17-rt" and give it the Hardy version numbers will that mess up my Gutsy kernel or simply install one more kernel (prefered)?  Regards Ian.

---

### Post by zvacet on 2008-05-27
It will install one more kernel and when you start you will see them in grub so you can select one to work with.

---

