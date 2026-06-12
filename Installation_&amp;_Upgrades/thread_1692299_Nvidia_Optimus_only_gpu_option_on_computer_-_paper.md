---
title: "Nvidia Optimus only gpu option on computer - paperweight for Ubuntu?"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-02-21
when buying a new computer, some of the computers that interest me only come with Nvidia optimus as graphics. That is, there's no integrated Intel gpu option or regular Nvidia card option.

Does this mean this computer will not work with Ubuntu? To run ubuntu MUST I get a non-optimus or integrated gpu option?

---

### Post by cascade9 on 2011-02-21
Optimus MUST have intel video (I refuse to give any intel video chip the 'GPU' name). So you should be able to use an optimus laptop with linux. 

That said, avoid optimus at all costs. In almost all cases, unless you have a BIOS switch for forcing the nvidia GPU, you cant use the nvidia graphics. If there is not BIOS switch to force or disable the nvidia GPU, it takes a fair bit of work (if its possible at all) to even disable the nvidia GPU. So it just sits there, sucking power, creating heat.

---

### Post by nrundy on 2011-02-21
The problem I'm finding is that more and more laptops come with Optimus or Integrated. You can't get a discrete GPU anymore without Optimus.

Linux is a real bummer for this situation.

---

### Post by cascade9 on 2011-02-21
Its getting much, much harder to find nvidia GPUs without optimus, but AMD doesnt have that problem. No intel video, no optimus. 

The intel models with ATI/AMD GPUs dont have optimus either (but they can have switchable graphics, which isnt exactly great) 

The laptops with a BIOS switch to force the nvidia GP should be fine as well. 

Last of all, some of the i7 models dont have intel GMA, so they are optimus free as well.

---

### Post by nrundy on 2011-02-21
how do i identify if the comp has the BIOS switch? is this something i have to email Support before buying, "do you offer a BIOS switch for turning off nvidia?" or am i looking for something specific in the tech specs published at the manufacturer websites?

---

### Post by nrundy on 2011-02-21
Does the Lenovo T410 have this BIOS switch for turning off Optimus?

---

### Post by cascade9 on 2011-02-22
Its a right #^&#&^# to figure out if a laptop has a BIOS switch. Even if you can figure it out, sometimes the manufacturer will remove the BIOS switch in later BIOSes (dell has done it, probably others). 

I'd doubt that support would even know if a laptop has a BIOS switch. well, the higher level techies might, but you tend to get kicked up to them for 'serious' problems. Initial email support will get you get a trained monkey. 

Looking at spec sheets doesnt help either. Most of the optimus models dont even list optimus on in spec sheet, let alone if there is a way around the blasted thing.  

I had a quick look at the T410, but since is the same model number for the earlier non-optimus versions as it is with the newer optimus versions, its difficult to tell if its ot a way to 'force' the nvidia GPU in BIOS. But I dont think it does.

---

### Post by nrundy on 2011-02-23
> **cascade9 said:**
> Initial email support will get you get a trained monkey. 


LOL. I've come to the same conclusion :)

I think it's best to stay away from Optimus. Thanks for the help.

---

### Post by cascade9 on 2011-02-23
No problem. 

Its a pity about optimus.....how the mightly have fallen. :(

---

