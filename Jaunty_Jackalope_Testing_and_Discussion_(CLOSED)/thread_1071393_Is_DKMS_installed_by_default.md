---
title: "Is DKMS installed by default?"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-16
It seems to be either not installed by default or is spontaneously uninstalled on a whim.

---

### Post by desm on 2009-02-16
Check synaptic. It marks packages that are already installed. 
I think the package you're looking for is:

dkms (2.0.20.4-0ubuntu2)
    Dynamic Kernel Module Support Framework

or at least, that's what happened when I looked for 'dkms' at [http://packages.ubuntu.com/intrepid/allpackages](http://packages.ubuntu.com/intrepid/allpackages).

---

### Post by Starks on 2009-02-16
> **desm said:**
> Check synaptic. It marks packages that are already installed. 
I think the package you're looking for is:

dkms (2.0.20.4-0ubuntu2)
    Dynamic Kernel Module Support Framework

or at least, that's what happened when I looked for 'dkms' at [http://packages.ubuntu.com/intrepid/allpackages](http://packages.ubuntu.com/intrepid/allpackages).

You missed the point of my post.

I was lamenting at the fact that DKMS is either not installed by default or finds itself easily uninstalled if it is installed by default.

---

### Post by desm on 2009-02-16
I'm not on Ubuntu right now - but I'm pretty sure it also finds itself easily installable... ?

---

### Post by taavikko on 2009-02-16
> **Starks said:**
> It seems to be either not installed by default or is spontaneously uninstalled on a whim.

It's supposed to be automatically installed.
At least it should be installed when installing proprietary drivers for graphics cards...

---

### Post by kde4-core-user on 2009-02-16
> **Starks said:**
> Is DKMS installed by default?

No, it is not installed by default! But it's a dependency (for example) from nvidia-180-kernel-source. So it will be automatically installed, when you need DKMS!

---

### Post by bruce89 on 2009-02-16
```
bruce@Scooby-Dum:~$ apt-cache rdepends dkms
dkms
Reverse Depends:
  sl-modem-source
  virtualbox-ose-source
  virtualbox-ose-guest-source
  nouveau-kernel-source
  lirc-modules-source
  kvm-source
  kqemu-source
  nvidia-96-kernel-source
  nvidia-71-kernel-source
  nvidia-180-kernel-source
  nvidia-173-kernel-source
  fglrx-kernel-source
```

---

