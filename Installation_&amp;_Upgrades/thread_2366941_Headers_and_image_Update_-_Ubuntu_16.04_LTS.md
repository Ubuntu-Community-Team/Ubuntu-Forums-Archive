---
title: "Headers and image Update - Ubuntu 16.04 LTS"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by blauensl on 2017-07-24
Hey guys,


after the following updates my ubuntu login screen disapeared:

linux-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-headers-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-image-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-signed-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-signed-image-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]

Any known bugs with this versions?

Side notes: My Ubuntu Gnome machine is joined in an UCS domain.

Thanks in advance.

---

### Post by vocx on 2017-07-24
> **blauensl said:**
> Hey guys,


after the following updates my ubuntu login screen disapeared:

**linux-generic-hwe-16.04**/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-headers-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-image-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-signed-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]
linux-signed-image-generic-hwe-16.04/xenial-security 4.10.0.27.30 amd64 [upgradable from: 4.8.0.58.29]

Any known bugs with this versions?

Side notes: My Ubuntu Gnome machine is joined in an UCS domain.

Thanks in advance.
Well, you just updated the kernel, which probably means you also updated your video card drivers. The first step to investigate would be to check that your video card model is supported in the new kernel, and add specific options if needed. Otherwise boot the old kernel and use that until you know the newest kernel works with your video card.

---

### Post by #&amp;thj^% on 2017-07-24
> **blauensl said:**
> 

Any known bugs with this versions?

Side notes: My Ubuntu Gnome machine is joined in an UCS domain.

Thanks in advance.
Yep starting to see more than a handful of login problems with the 4.10 kernel here in the forums as of late.
vocx has a good thought with  "video drivers" also, are you using the non free drivers?
EDIT: And I'm going to assume you are also fully updated on your system. (Not just the kernel upgrades but a full system upgrade)

---

### Post by blauensl on 2017-07-25
> **vocx said:**
> Well, you just updated the kernel, which probably means you also updated your video card drivers. The first step to investigate would be to check that your video card model is supported in the new kernel, and add specific options if needed. Otherwise boot the old kernel and use that until you know the newest kernel works with your video card.

How do I check if my video card is compatible to the new kernel version?

> **1fallen said:**
> Yep starting to see more than a handful of login problems with the 4.10 kernel here in the forums as of late.
vocx has a good thought with  "video drivers" also, are you using the non free drivers?
EDIT: And I'm going to assume you are also fully updated on your system. (Not just the kernel upgrades but a full system upgrade)

I do not know which driver package I use - This is the output of "lshw -c video":

```
 *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:4000(size=64) memory:c0000-dffff
```

Correct I did a full upgrade of my system.

---

### Post by blauensl on 2017-07-31
Any solutions here?

Thanks in advance.

---

