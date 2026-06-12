---
title: "Moving to different hardware"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by Dark Shade on 2008-10-06
Hi all,

This might be a super-n00b question, but I do need the answer to it and this looked like the place to ask.

Right now I have 8.04 running on an AMD 4800+ Dual Core and an ASUS M2N61-AR motherboard quite well, however I am needing to move the installation over to new hardware, specifically a server type.  The new hardware is two quad core AMD Barcelona 8346's and an ASUS KFN4-DRE.  What steps will I need to take to make sure this transition is smooth and clean?  Keep in mind this server will be for hosting games and websites.

1.  Do I need to recompile the kernel?  Or *should* I recompile it?
2.  I am not sure if the quads I am getting are affected by the TLB bug, if so, should that issue be addressed immediately?
3.  Any obvious question I am missing?  :confused:

Thanks for any help :)

---

### Post by asmoore82 on 2008-10-06
I would expect no problems as long as you don't move an amd64 system to a 32-bit CPU :lol:

but, the system does have a "permanent" memory of which physical network devices(MAC addresses) map to which logical names...
to clear this memory, delete the relevant lines from the file
"/etc/udev/rules.d/70-persistent-net.rules"

---

### Post by Dark Shade on 2008-10-06
Thanks :)

Yeah it's moving from one AMD64 to another, so no ARCH problems.  I'm just hoping the drivers will auto-update to its new hardware and all that jazz.  Now I just have to figure out how to configure two NICs :-$

---

