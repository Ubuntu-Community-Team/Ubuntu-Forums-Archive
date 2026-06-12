---
title: "Driver Issues"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by pseudosig on 2007-03-15
Okay, I finally got Ubuntu installed on my machine.  Now I'm having an issue of Ubuntu seeing my motherboard components (i.e. ethernet, sound, etc).

My motherboard chipset is nvidia's nforce 650i.  I tried the command **sudo modprobe forcedeth** since that's the opensource driver to run the ethernet.  Didn't help...

I'm new to Ubuntu (and Linux for that matter...) and would like any advive I can get...

thanks...

---

### Post by pradeepadapa on 2007-03-15
which version of UBUNTU did u install nd ethernet card is automatically detected and installed in UBUNTU 6.10 ..... plse tell ur version of ubuntu u installed.

---

### Post by pseudosig on 2007-03-16
> **pradeepadapa said:**
> which version of UBUNTU did u install nd ethernet card is automatically detected and installed in UBUNTU 6.10 ..... plse tell ur version of ubuntu u installed.

Sorry, I should have mentioned it.  I installed Ubuntu version 6.10

---

### Post by pradeepadapa on 2007-03-16
then ubuntu 6.10 detects most of the ethernet cards on various motherboards..... otherwise check the tag for nvidia and see in those posts

---

### Post by pseudosig on 2007-03-16
> **pradeepadapa said:**
> then ubuntu 6.10 detects most of the ethernet cards on various motherboards..... otherwise check the tag for nvidia and see in those posts

So if Ubuntu did support my ethernet card, would it have been plug and play, i.e. if I plugged in my ethernet cable, it wouuld work?  Or would I have to configure a file... like the xorg.conf, etc?

---

### Post by inCursorated on 2007-03-16
> So if Ubuntu did support my ethernet card, would it have been plug and play, i.e. if I plugged in my ethernet cable, it wouuld work? Or would I have to configure a file... like the xorg.conf, etc?

yeah, it would work automatically (assuming dhcp is in use)... fyi, if u had to configure settings manually to be read at boot the file is /etc/network/interfaces

---

### Post by pseudosig on 2007-03-16
Thanks for your input.

---

