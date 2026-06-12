---
title: "How to install Ubuntu on an old computer?"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Opeth on 2008-11-29
Right, so, I've got an old computer that I want to install Xubuntu on. It's got a CD drive, but for some reason, the computer won't post with it plugged in. When I unplug it, it's fine. I can't seem to get into the BIOS either. So...

No CD drive
Probably unable to boot from USB

What else is there? The OS on the HDD now is corrupt, so I can't get on it to install it via Wubi either. What can I do to bring this computer back to life?

---

### Post by sosaudio1 on 2008-11-29
> **Opeth said:**
> Right, so, I've got an old computer that I want to install Xubuntu on. It's got a CD drive, but for some reason, the computer won't post with it plugged in. When I unplug it, it's fine. I can't seem to get into the BIOS either. So...

No CD drive
Probably unable to boot from USB

What else is there? The OS on the HDD now is corrupt, so I can't get on it to install it via Wubi either. What can I do to bring this computer back to life?

This isnt a compaq computer is it?

---

### Post by Opeth on 2008-11-29
Nope, it's a Gateway Performance 800. 

384mb RAM
15.4GB 5400RPM IDE HDD
800MHz Pentium 3

---

### Post by sosaudio1 on 2008-11-29
> **Opeth said:**
> Nope, it's a Gateway Performance 800. 

384mb RAM
15.4GB 5400RPM IDE HDD
800MHz Pentium 3

ok because back in the day, used to be that compaq would put their BiOS on the HDD which caused problems when booted and Nuked...LOL...The next question is, is the CD drive slave or master to the bus on the motherboard?

---

### Post by Opeth on 2008-11-29
> **sosaudio1 said:**
> ok because back in the day, used to be that compaq would put their BiOS on the HDD which caused problems when booted and Nuked...LOL...The next question is, is the CD drive slave or master to the bus on the motherboard?

Since the cables are way too short to reach each other, the hard drive is using one cable by itself as a master, then the cd drive was using another separate cable as a master. 

I appreciate the help.

---

### Post by sosaudio1 on 2008-11-29
> **Opeth said:**
> Since the cables are way too short to reach each other, the hard drive is using one cable by itself as a master, then the cd drive was using another separate cable as a master. 

I appreciate the help.

Try setting the CD Drive as slave and see if that gets you started..I ha....I dislike intensely running a CD drive and a hard drive on the same bus but...maybe this will get you started...if you can avoid it, I would...but let's see if we can at least get to post...

---

### Post by logos34 on 2008-11-29
> **Opeth said:**
> It's got a CD drive, but for some reason, the computer won't post with it plugged in. When I unplug it, it's fine. I can't seem to get into the BIOS either. 


So you tried pressing **F1** key to enter the Bios at startup?

Verify the jumper on the back of the cd is set for 'master' or 'cable select'.  

If you switch the cd drive as suggested, make sure the jumper on the back is set for 'slave', or 'cable select' (in the latter case the hard drive also has to be set the same).

---

