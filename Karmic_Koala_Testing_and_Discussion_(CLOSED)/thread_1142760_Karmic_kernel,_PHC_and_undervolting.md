---
title: "Karmic kernel, PHC and undervolting"
date: 2009-04-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-04-29
Is there any news on whether the acpi-cpufreq module will be available as a module or built in (a la jaunty)?

I used to undervolt back in intrepid and hardy, and it made my processor run significantly cooler, as well as drawing slightly less power. In jaunty for some reason the module was compiled into the kernel, and is no longer available to patch without recompiling the whole kernel. The devs apparently realised the short-sightedness of this, and the last thing I heard was that they were planning to have it as a module for karmic.

---

### Post by htrex on 2009-07-17
I hope so, but I've no evidence that KK will have acpi-cpufreq as a module.

for Jaunty there's a phc patched kernel ppa
[https://launchpad.net/~linux-phc/+archive/ppa](https://launchpad.net/~linux-phc/+archive/ppa)

but that's not working for me and it even disables cpu frequency scaling...

---

### Post by htrex on 2009-07-29
submitted an idea on brainstorm
[http://brainstorm.ubuntu.com/idea/20847/](http://brainstorm.ubuntu.com/idea/20847/)

vote for it if you think that's important.

Alessandro

---

### Post by kabaiz on 2009-09-12
hello

I've compiled the kernel and the modul for the (almost) latest karmic koala and i can't recognize changes compared to original kernel.

I can read and write the values for voltages but that doesn't change anything. I'm running 2 burnMMX thread and the CPU stays at the same temperature (74 C) independently from the values...

In 8.10 the temperature was able to go up to 90 C degree by default, so this 74 C is quite low, but with linux-phc i was able to reach 65-70 C.

So maybe there are some optimizations around this by default or i just made something wrong :)

bye,
kabaiz

---

