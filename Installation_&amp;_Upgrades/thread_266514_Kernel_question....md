---
title: "Kernel question..."
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by bobosity on 2006-09-27
I just installed the K7 kernel. It works fine but I'm wondering.... what do I have now that I didn't with the 386 kernel?

I understand that it's optimized for my AMD chip but what does that mean? Is my machine faster? More stable? Should I be able to see the difference?

Thanks....

---

### Post by pseudonym on 2006-09-27
I'm no expert on this, but I think that at least one important optimisation has to do with multimedia instructions in AMD CPUs. I f the kernel is specifically configured for K7, then it knows better how to deal with them, thus leading to better performance. It should be noticeable in things like CPU load in video applications, for example.

---

### Post by Shay Stephens on 2006-09-27
I never noticed a change switching from the 386 to 686 kernal.  But I am sure there must be something going on back there to make it worthwhile to have a separate one created in the first place ;-)

---

### Post by bobosity on 2006-09-27
Since I can hit either kernel from the grub menu, I'm interested in trying to benchmark them. 

Searching synaptic for 'benchmark' didn't give anything that looked useful. 

Is there a tool that would work?

---

### Post by Shay Stephens on 2006-09-27
I tried benchmarking and couldn't see a difference in boot times or a few other things.  I think I tried Photoshop filters as my test.

---

