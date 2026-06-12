---
title: "Problems with laptop Lifebook s7210"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fsando on 2008-09-18
I don't know if this is the right place to ask these questions
I have recently bought a

Fuji Siemens Lifebook S7210
Cpu 2.4 Ghz
Graphics Intel x3100
Mobile Internet option (can't seem to find the make)
Various card readers (including chip card reader)

I initially installed 8.041 but it was extremely slow and from the cpu-speed applet it always ran at 800 Mhz.

I upgraded to Intrepid 8.10 which solved that problem.

There seem to be a range of problems left still though. Most important problem is that the x3100 is apparently not working as it should:

When I try to enable 'Visual Effects' it start with: "Looking for suitable driver"
then it fails with: "Desktop effects could not be enabled"
Highlighting in menus lags seriously after mouse movement

Various other hardware seem to not be recognized like turning screen light up or down, chip card reader (have not done extensive testing as I really don't know how to). My question is if x3100 is in fact supported (I'll be happy for a pointer) or if the support of this is under way, and if some testing is perhaps needed.

Because of the problems I have at the moment designated this laptop purely as spare machine for emergency windows sessions (dual boot). And as I have 'partimaged' everything I'm not too afraid to do quite extensive testing if someone would need that. (I'm not unfamiliar with compiling etc. though certainly no expert)

If this is not the right place to ask please point me gently in the right direction ;)

---

### Post by Nullack on 2008-09-18
Going to an Alpha piece of software is a brave move :) I like your style.

If you want to have production like robustness, it might be better to stick with Hardy and work out what it needs for your specific hardware.

With Alpha software, it is early in the lifecycle and it will cost you more of your time in bugs, debugging and so on.

For compiz youll need a compatible video driver.

---

### Post by fsando on 2008-09-18
> **Nullack said:**
> Going to an Alpha piece of software is a brave move :) I like your style.

If you want to have production like robustness, it might be better to stick with Hardy and work out what it needs for your specific hardware.

With Alpha software, it is early in the lifecycle and it will cost you more of your time in bugs, debugging and so on.

For compiz youll need a compatible video driver.

Ok I can see what you are aiming at. But it is not what it seems.

I know this is alpha and early lifecircle but I don't feel I have much choice. The problem is that this laptop doesn't work with 8.041. I bought it because of a deal between suse and fuji-siemens regarding Lifebooks lead me to believe it would be supported under linux. Turns out it concerned the E-series.

Now because it is alpha-stage my hope is that I can help myself  and perhaps others by testing before we reach RC (I may have completely misunderstood how these things work). 

I have done quite extensive searching for solutions in recent weeks and the closest I have got is 
1) thinkpads with x3100 seem to experience problems 
2) there is a German Lifebook-linux page regarding ubuntu 7.10 but that is for an earlier version for the lifebook.

I also feel a bit embarrassed that it didn't occur to me that I should have gone straight to this forum earlier but as I said I started out with 8.04 and then moved on to 8.10. I actually spent two whole days last weekend installing all possible distros to see if any of them would work reasonably. In my view ubuntu is by far the best (all things considered) even when using the 8.10 alpha because of the repositories and synaptics are so well integrated into the system and so easily accessible.

---

