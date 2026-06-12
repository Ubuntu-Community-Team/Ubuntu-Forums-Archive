---
title: "Kernel Panic on old PC"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by KenBW2 on 2008-05-11
I have a really, really old PC (designed for Win95, used to run Win98 ), with a pre-Pentium Intel processor and I'm hoping to breathe new life into it with Linux of some description. I thought I'd choose Ubuntu + variants (most likely Xubuntu for obvious reasons) as I'm an Ubuntu man at heart and would like to stick with it.
But alas, every time I try to boot the install CD (with Ubuntu, Xubuntu (where the hell did I put my Kubuntu CD?) + alternates as well) it tells me "Kernel panic. Attemped to kill the idle task!" and then sits there for as long as it takes me to give up on it. I've tried Puppy Linux and DSL, which both work but I never get to the install stage as it dies beforehand. Plus I like *ubuntu :D

Any ideas? Thanks

---

### Post by Pumalite on 2008-05-11
Post your specs. The first suspect is your burner if you do md5sum and burn at 4x or less, on good quality CD-R. Try your CD's in a different computer. Clean the lens in your burner or change it. I hope you have enough RAM.

---

### Post by KenBW2 on 2008-05-11
The CDs are fine - I've installed on other PCs with them.
I don't know the specs - i suspect it has 128MB RAM, processor is <1GHz and the HD was a 1.4GB one, but I've put an old 20GB one in since. Problem occurs with both HDs.

---

### Post by Pumalite on 2008-05-11
Use xubuntu Alternate CD and use some common boot parameters like noapic, nolapic, acpi=off or similar.

---

### Post by sTpny on 2008-08-06
I believe you need 256 of memory to install ubuntu from live cd.

---

### Post by Pumalite on 2008-08-06
> **KenBW2 said:**
> The CDs are fine - I've installed on other PCs with them.
I don't know the specs - i suspect it has 128MB RAM, processor is <1GHz and the HD was a 1.4GB one, but I've put an old 20GB one in since. Problem occurs with both HDs.

If Xubuntu does not work; you might have to stick to a smaller distro like Puppy or DSL

---

### Post by KenBW2 on 2008-08-07
> **sTpny said:**
> I believe you need 256 of memory to install ubuntu from live cd.

I've tried the Alternate CD as well, still no joy.

@Pumalite

You think there's no chance?

---

### Post by Pumalite on 2008-08-07
Try a Minimal Install:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by snowpine on 2008-08-07
Staying within the *Buntu family, your 128mb of ram options are: Xubuntu from alternate CD, Fluxbuntu, Crunchbang, Minimal install (see Pumalite's link).

---

