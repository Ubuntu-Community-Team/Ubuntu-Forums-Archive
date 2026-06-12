---
title: "linux-restricted-modules-2.6.26-1-rt  not installable"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc510 on 2008-09-22
trying to install linux-rt on ubuntu 8.10 alpha 6 desktop i386 (wubi) ... synaptic says linux-rt depends on linux-restricted-modules-rt but that it is not going to be installed.  okay, i'll select linux-restricted-modules-rt for installation in synaptic ... now synaptic says "Depends: linux-restricted-modules-2.6.26-1-rt but it is not installable."   :confused:  user error?  packaging bug?

---

### Post by Quikee on 2008-09-22
Looks like rt is not an priority for packaging (2.6.26-1 was the first kernel release for intrepid - in the mean time they decided to switch to 2.6.27). Probably they are waiting for 2.6.27 to be released before they can apply rt patches and will release a working package. For time being just use the generic package.

---

### Post by prismatic7 on 2008-09-24
> **Quikee said:**
> Looks like rt is not an priority for packaging (2.6.26-1 was the first kernel release for intrepid - in the mean time they decided to switch to 2.6.27). Probably they are waiting for 2.6.27 to be released before they can apply rt patches and will release a working package. For time being just use the generic package.

There's been discussion on the UbuntuStudio users list about this. There's significant errors with midi timing and latency in the .26 kernels, and not enough time and devs available to patch the .27 kernel for the October 30 release (I think there's issues with the -rt branch for .27 anyway) So we may be looking at a wait for any sort of realtime kernel in intrepid. Which sucks, but UbuntuStudio isn't blessed by Canonical staff working on it, so it's all volunteer...

---

### Post by mc510 on 2008-09-25
bummer.  so the realtime kernel is not an official canonical project?

---

### Post by Sandsound on 2008-10-01
> **prismatic7 said:**
> we may be looking at a wait for any sort of realtime kernel in intrepid.

:( Bad news... Was so hoping to test-drive the new Beta :(

---

