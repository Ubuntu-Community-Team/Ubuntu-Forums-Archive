---
title: "CPU Upgrade on Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by jonom on 2007-04-23
I've got a new CPU I want to drop into my system, going from an AMD64 3000+ to an AMD 64X2 3800+. Everything else stays the same, it's a simple cpu swap on the motherboard.

Is there anything I'm going to need to do/should know about before attempting this? Can I do it without reinstalling Feisty?

---

### Post by obijywk on 2007-04-23
i think you should be fine. i can't see what in Feisty would need to change for moving between different AMD64 CPUs. if you were changing the motherboard this would be different, but for just switching CPUs I think there will be no problem.

---

### Post by bulldog on 2007-04-23
> **jonom said:**
> I've got a new CPU I want to drop into my system, going from an AMD64 3000+ to an AMD 64X2 3800+. Everything else stays the same, it's a simple cpu swap on the motherboard.

Is there anything I'm going to need to do/should know about before attempting this? Can I do it without reinstalling Feisty?

You'll go from a single CPU to a Dual Core.
It should be wise to install the generic kernel with smp support,so it can use both CPU's.
This means new restricted modules to let your graphics work.

---

### Post by jonom on 2007-04-23
> **bulldog said:**
> You'll go from a single CPU to a Dual Core.
It should be wise to install the generic kernel with smp support,so it can use both CPU's.

Should I do that before or after putting the new cpu in, and can I find it synaptic?

> This means new restricted modules to let your graphics work.

What needs to be done there? Will reinstalling the graphics drivers take care of that? I'm running nvidia.

Thanks for the help!

---

### Post by jonom on 2007-04-24
Wow, I'm impressed!

I checked through synaptic and from what I could tell, it said that the smp support was defaulted to the generic linux kernel.

So I figured I'd give it a try.

Success! I didn't have to do a thing. Ubuntu started up recognizing both cpus, graphics are running fine. Everything seems to be running fine.

---

