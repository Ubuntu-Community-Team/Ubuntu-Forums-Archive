---
title: "Kernel Update; No Internet"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by ssmithy on 2007-02-20
I just updated the kernel and, in doing so, lost my connection to the net.  I have an onboard network card (wired connection) and it worked fine prior to the update.  If I go into the Administration, Networking, the etho device that used to be there is missing!  Any ideas on what I can do to fix this?!

---

### Post by dcstar on 2007-02-21
> **ssmithy said:**
> I just updated the kernel and, in doing so, lost my connection to the net.  I have an onboard network card (wired connection) and it worked fine prior to the update.  If I go into the Administration, Networking, the etho device that used to be there is missing!  Any ideas on what I can do to fix this?!

Try booting off the previous kernel (one assumes it is still available).

---

### Post by Kateikyoushi on 2007-02-21
You could list your devices with lspci. Then search which module works with that hardware and load it with modprobe modulename. Another option is to stick with the old kernel if it worked for you.

---

### Post by ssmithy on 2007-02-21
I tried logging into the previous kernel, but that didn't work.  Heck, I ever tried using the live cd just to see if my card was working... and it didn't.  So... I'm starting to think this is hardware problem.  I have an ECS mobo (I know... I know... the're crap) and from searching around on various other forums it looks like it might be the culprit.

I might try reseting the CMOS battery jumper later tonight to see if that does anything.  Or perhaps there's some setting in the BIOS I can toy with.  I'll post back if I find anything.

---

### Post by ssmithy on 2007-02-21
Well, I cleared the CMOS and presto... it works!  But that's kinda cruddy news since it confirms that my motherboard is a POS.  Thanks for the help!

---

