---
title: "How can I remove the i686 kernel after failed upgrade?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by DarkN00b on 2006-09-20
One of the reasons I wanted to try Linux (which I really like btw) is that I am a compulsive tinkerer.

Well, I tinkered myself into a kernel panic.  I'm running the 2.5.15-27-386 kernel.  I had no problems after upgrading from 2.6.15-26-386. Then I decided to give the i686 kernel a try which resulted in a kernel panic upon reboot.

My question now is: how do I remove the i686 kernel?  I can boot into the 386 kernel just fine using grub so I just want to dump the 686. I tried 
```
sudo apt-get remove linux-686
```

That didn't work. :/

My machine still tries to boot the 686 kernel resulting in a kernel panic.  So how do I remove it?

---

### Post by missmoondog on 2006-09-20
boot into the 386 kernel then remove the 686 in synaptic.

---

### Post by DarkN00b on 2006-09-20
That did it. I don't know why I didn't think of that myself. just the other day recommended someone here use Synaptic to install Nvu. 

Thank you; you get a :KS .

---

