---
title: "xf86config"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by sheine on 2007-07-04
In the past, before installation became so easy, I had to use xf86config with linux installations. Since Ubuntu refuses to give me a decent display on my new computer, I would like to know if this command is still the best to use or is there something newer.

---

### Post by moore.bryan on 2007-07-04
*sudo dpkg-reconfigure xserver-xorg may work and if you have an intel chip, the 915resolution package might be needed.*

---

### Post by sheine on 2007-07-04
> **moore.bryan said:**
> *sudo dpkg-reconfigure xserver-xorg may work and if you have an intel chip, the 915resolution package might be needed.*

I tried the dpkg etc. When I reached the page "configuring xserver-xorg" nothing happened. There is an ok at the bottom which I cannot activate. My chip is not one for which 915resolution is designed.

---

### Post by moore.bryan on 2007-07-04
> **sheine said:**
> My chip is not one for which 915resolution is designed.
*which chipset do you have?*

---

### Post by sheine on 2007-07-04
I just looked at the synaptic package manager. The xserver-xorg packages are installed. How do I activate them or get "resolution preferences" to see them?

---

### Post by sheine on 2007-07-04
> **moore.bryan said:**
> *which chipset do you have?*

Pentium dual core T2080

---

### Post by moore.bryan on 2007-07-04
> **sheine said:**
> I just looked at the synaptic package manager. The xserver-xorg packages are installed. How do I activate them or get "resolution preferences" to see them?
*your config file is /etc/X11/xorg.conf.  perhaps by editing that to include the proper resolution we can solve this puzzle.*
> **sheine said:**
> Pentium dual core T2080
*that chipset is okay with the 915resolution package...*

---

### Post by sheine on 2007-07-04
How do I edit the file? xf86config does not work. Do I just open the file and change the resolution?

---

### Post by moore.bryan on 2007-07-04
*yup.  you can check [this other thread]("http://ubuntuforums.org/showthread.php?t=83973") for some guidance.  back on hoary, i used the [modeline]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") tool to get the exact stuff to put in the xorg.conf file; perhaps you could use it too.*

---

### Post by sheine on 2007-07-04
I solved the problem in an unorthodox way. I copied the xorg.conf file from Simply  Mepis and replaced the xrorg.conf file of Ubuntu.

---

### Post by moore.bryan on 2007-07-04
*it was definitely your xorg.conf.  you might just want to have a look at the old conf file and compare it to your new one to see the difference...*

---

