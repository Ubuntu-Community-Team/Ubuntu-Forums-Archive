---
title: "Driver installation. Please help."
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by bigseb on 2010-03-19
How do install this graphics card driver?!?! File name is 'NVIDIA-Linux-x86_64-190.53-pkg2.run'. It is pasted on my desktop.

---

### Post by MelDJ on 2010-03-19
did the way i showed not work?

---

### Post by bigseb on 2010-03-19
> **MelDJ said:**
> did the way i showed not work?
No... help

---

### Post by dino99 on 2010-03-19
> **bigseb said:**
> No... help

You can update your system with unsupported packages from this untrusted PPA by adding ppa:nvidia-vdpau/ppa  to your system's Software Sources

synaptic --> repo --> add

---

### Post by bigseb on 2010-03-19
> **dino99 said:**
> You can update your system with unsupported packages from this untrusted PPA by adding ppa:nvidia-vdpau/ppa  to your system's Software Sources

synaptic --> repo --> add


Thanks... but I don't know what that means. Noob here...

---

### Post by oldos2er on 2010-03-19
Open Synaptic Package Manager (via menus System, Administration, Synaptic), click settings, repositories, other software, add, then copy and paste **ppa:nvidia-vdpau/ppa**. Click close. Your software sources will be reloaded, and you should now be able to install the nvidia drivers from Synaptic.

---

### Post by bigseb on 2010-03-19
Ok, I'm sort of kind of busy with this. Lets hope it works...

---

### Post by bigseb on 2010-06-04
Not to drag up an old thread but it kinda fits:

My wife wants me to load Ubuntu onto her laptop this weekend. Her graphics  card is an ATI Radeon 3200.

> **dino99 said:**
> You can update your system with unsupported packages from this untrusted PPA by adding ppa:nvidia-vdpau/ppa  to your system's Software Sources

synaptic --> repo --> add

Do I follow this same process but type: ppa:ati-vdpau/pp instead?

Thanks

---

### Post by oldos2er on 2010-06-04
No, as far as I know vdpau is an Nvidia-only thing. Ubuntu should recognize the ATI card, and if you're lucky it'll offer to install restricted drivers for it once you get Ubuntu installed.

---

### Post by Joel(Linux) on 2010-06-04
ok, hopefully this works, well it worked for me anyway. First go to system>administration>hardware drivers, it should automatically scan your pc for drivers and install them.

---

