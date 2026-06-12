---
title: "Regarding Text Mode Installation"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by derekeverett on 2010-03-30
When I upgrade to 10.04 in a month or so I think I'm going to do a fresh install using the alternate CD. I've been looking into that a little bit and I have a couple questions I would like to have clarified.

1)I am assuming 3 Linux partitions will be enough. (I dual boot with Win7 which obviously already has it's own partition). I am thinking one primary partition for the OS with a logical partition for swap. I would then have a separate primary partition for my home directory. 

If my understanding is correct this will allow me to do a clean install of Ubuntu at will in the future without affecting my home directory? 

If there is anything wrong with this plan or something else I need to consider please tell me

2)As I dual boot with Windows I cannot choose UTC time correct?

3)As I am not part of a LAN I do not have to enter any proxy information, I just leave that blank?

Thanks to anybody that can comment here. I'm a little nervous to try this so I'm just trying to get an idea of what to expect. If there is something I haven't considered please inform me.

---

### Post by Fafler on 2010-03-30
1) Correct, although changes in to configurationfiles in ~/ might make the system behave unfortunate after a reinstall, but it should be trivial to fix.

2) Well, it seems to explain why there's a one hour difference between Linux and Windows on my multiboot machine. Not that it matters for me, though.

3) Correct.

---

### Post by derekeverett on 2010-03-30
> **Fafler said:**
> 
2) Well, it seems to explain why there's a one hour difference between Linux and Windows on my multiboot machine. Not that it matters for me, though.


I just read about how Windows cannot handle UTC time not an hour ago! I would've selected it otherwise I'm sure.

Thanks for your response. Do you know what configuration files I need to be aware of/need to fix?

---

