---
title: "Recommend the best kernel for Sempron64 2600+"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by bravemosquito on 2007-02-27
My current kernel version is 2.6.17-11-386 on Xubuntu 6.10. As you see this isn't best choice - 32bit kernel vs AMD64 ... I'm not experienced very well in this distribution specific area and here I'm asking some advices which stable kernel to choose (386, generic, 686...). Perhaps and how to install it without messing with my current configuration - freshly (and stable, I hope so) installed FF 2.0.0.1, video drivers, sound system and apps for normal use.

Thanks

---

### Post by mikewhatever on 2007-02-27
Can you explain in greater details why your kernel is not the best choice? Are there any problems? If you wanted a 64 bits kernel, I think you should have installed a 64 bits version of Xubuntu.

---

### Post by bravemosquito on 2007-02-27
Yes, there are some minor and some major problems. But I'm not sure exactly this is the right solution for fixin' them...

Some apps are slow compared to my BSD box, other aren't but closing themselves unexpected (GUI problems?). I'm just searching the kernel with best performance/problem-free ratio. It's normal that changing the kernel from 386 to AMD64 is hell-work, I know. Maybe it's not necessary to install new 64bit version of Xubuntu,  maybe just upgrading the current with newer is easier.

I'll appreciate some links with usefull information ;)

ps. hmmm, "the optimal kernel for..." sounds more accurate than "best" :)

---

### Post by actuary286 on 2007-02-27
For Edgy (6.10), the developers stopped producing separate kernels for different processor generations and SMP. Now, only the following kernels are in the repositories:

[LIST]
[*]linux-generic for most desktops
[*]linux-386 for older (pre-686) processors
[*]linux-server for server hardware
[*]linux-lowlatency which is in the non-free multiverse
[/LIST]

All of the above are meta-packages that will always point to the most recent version of the kernel. You can check which one you have installed with Synaptic.

You probably won't get much better performance from changing the kernel unless you compile your own.

---

### Post by bravemosquito on 2007-02-27
> **actuary286 said:**
> 
[*]linux-386 for older (pre-686) processors


Is there a differences between x.x.xx-xx-386 and x.x.xx-xx-686 when we're talkin' for 64bit cpu? :)

---

### Post by actuary286 on 2007-02-27
Yes, because the 64 bit CPU can also run in 32 bit mode and 686 supports more processor instructions. The linux-generic kernel provides support for all the different processor extension sets (i.e. SSE, 3DNow).

---

### Post by bravemosquito on 2007-02-28
Thanks...

But I'm totaly giving up myself from installing 2.6.17-11-generic. The new kernel trashes Xorg configuration after 2 hours of trying different ways (including use of envy script) to install it - with and w/o linux-restricted-modules through synaptic

Is there a little chance that somewhere in the forum has a nice thread with simple instructions 'how to' ?

---

### Post by mikewhatever on 2007-02-28
Supposedly, installing the restricted modules for the newer kernel and reconfiguring xserver/reinstalling the driver, are the instructions.

---

