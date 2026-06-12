---
title: "Can't install linux-restricted-modules"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2010-10-18
Hi

I am running Ubuntu 10.04 kernel 2.6.32-25

I have had trouble with getting Nvidia card to work after kernel upgrade.  Nvidia kernel module fails to load and I have to boot in low graphics mode.  After reinstalling drivers etc etc, I discovered that I need linux-restricted-modules installed.  However, there is no such meta-package installed in Synaptic  When I tried:

sudo apt-get install linux-restricted-modules-$(uname -r)

I get this error message:

E: Couldn't find package linux-restricted-modules-2.6.32-25-generic

Restricted packages is selected in sources, so why is it not installing the restricted modules meta-package?

How do install it??

Thanks

---

### Post by Lazaruss on 2010-10-18
try 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by realzippy on 2010-10-18
Open synaptic/settings/repositories
and check if "restricted" is enabled.

Edit:

sorry,overread that you enabled them.So have you updated the sources?

---

### Post by realzippy on 2010-10-18
> **Lazaruss said:**
> try 
```
sudo apt-get install ubuntu-restricted-extras
```

this is a package with
GStreamer plugins, Microsoft fonts,java runtime environment, Flash plugin, LAME,aso.
It does not contain the "restricted modules" (AFAIK).

---

### Post by Lazaruss on 2010-10-18
> **realzippy said:**
> this is a package with
GStreamer plugins, Microsoft fonts,java runtime environment, Flash plugin, LAME,aso.
It does not contain the "restricted modules" (AFAIK).

oops, my bad, thought they were one and the same... i have no linux-restricted-modules in synaptic, just ubuntu-restricted-extras

---

### Post by mrnelson1986 on 2010-10-18
What is your video card? For me just booting into recovery and reinstalling the nvidia drivers manually works.

---

### Post by Wtwine on 2010-10-19
Problem solved.  It wasn't a problem with restricted modules after all.    It turns out that my GeForce4 T4200 graphics card requires the Nvidia-glx-96.43.xx legacy driver, and is not supported by the current driver (260.19.xx).  When I upgraded, the legacy driver must somehow have been replaced by the current one.

So, I purged all installed nvidia drivers again (sudo apt-get --purge remove nvidia*), installed Nvidia-glx-96 and associated recommended packages in Synaptic, and rebooted.  Now my graphics card works again!  At last!

---

