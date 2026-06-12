---
title: "question about Ubuntu updates"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by soso64 on 2010-01-17
Hello everyone!

I'm new to Ubuntu ... and I installed it along with Vista in one laptop and it works fine with me

But when I install new updates for Ubuntu and restart my computer to apply those updates.... a new Ubuntu with different number appears on the list of the operating systems that I need to choose from 

For example ..
At first I have those OS: 
 Ubuntu (and some number I think it's 15)
 Vista

after the first update I have:
  Ubuntu (16)
  Ubuntu (and some number I think it's 15)
  Vista

after the second update:
  Ubuntu (17)
  Ubuntu (16)
  Ubuntu (and some number I think it's 15)
   Vista

My question is .. does this mean every time I updated Ubuntu I'll have additional OS on my device?

Any help is really appreciated :)

---

### Post by wojox on 2010-01-17
No those are just kernel upgrades. If your current kernel (17) is working out you can remove the others (15, 16).

---

### Post by kansasnoob on 2010-01-17
I always like to keep two kernels just in case.

Oh, and to remove a kernel safely I first run:

```
cat /boot/grub/grub.cfg
```

Which pulls up a copy of grub.cfg and I scroll down through it and look for the kernel I want to remove, in this example 2.6.31-16:

[ATTACH]143906[/ATTACH]

You can see that I've used my mouse pointer to highlight that kernel # so I can just right click and choose "copy".

Then I can just go to Synaptic and click on Search, then paste that number into the search window, then press Enter and let Synaptic find it for me. Then just mark for removal.

---

### Post by audiomick on 2010-01-17
> **kansasnoob said:**
> 
Then I can just go to Synaptic and click on Search, then paste that number into the search window, then press Enter and let Synaptic find it for me. Then just mark for removal.

that's a good trick ;)

---

