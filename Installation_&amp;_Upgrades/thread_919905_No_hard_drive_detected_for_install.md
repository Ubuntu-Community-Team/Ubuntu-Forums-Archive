---
title: "No hard drive detected for install"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by Exodus7707 on 2008-09-14
Ok so I ordered a free CD from linux -- ubuntu 8.0.4.1 Desktop Edition TLS. I am currently posting from the liveCD, but when I try to do a full install when I get to step 5 of 7(partition a drive) it does'nt list any hard drives. I looked in gparted and it also said no devices detected. The other OS I was using was vista, and my hard drive is a SATA. Did some searching on google on the topic, but found no solution.

---

### Post by Pumalite on 2008-09-14
When you get ready to boot your Live CD; edit your boot line and add 'all_generic_ide' at the end. See if that helps.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi Exodus7707, you *might* want to try intrepid if your hardware is brand new. Sometime support for new hardware can only be found in new software. Good luck :)

---

### Post by Pumalite on 2008-09-14
Intrepid Ibex Alpha5 is pretty good, but things do crash at times. I think it will be ready in October.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **Pumalite said:**
> Intrepid Ibex Alpha5 is pretty good, but things do crash at times. I think it will be ready in October.

Yeah, but for example, when I received the laptop I'm currently using in late november 2006, edgy, released in october 2006 was too old for it. Support for something on the motherboard was only present in newer kernel, so I just used feisty in very early alpha stages.

---

### Post by Exodus7707 on 2008-09-14
ok i added all_generic_idle and it still doesnt detect any hard drives

---

### Post by Pumalite on 2008-09-14
Boot your Live CD and post:
sudo lshw

---

### Post by Exodus7707 on 2008-09-14
sudo lshw didnt work for me either.. your talkng about putting it after everything in that boot line right?

---

### Post by Pumalite on 2008-09-14
No. Boot your Live CD. Once you get to the Desktop, go to Applications>Accessories>Terminal. Run the command there.

---

### Post by susssus on 2008-09-16
> **Exodus7707 said:**
> ok i added all_generic_idle and it still doesnt detect any hard drives

Note that it's ```
all_generic_ide
``` not *idle*. Got my installation working using that line :-).

---

