---
title: "Intel i915 kernel module loading for no apparent reason"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-24
anyone else get this problem?
asus m3a motherboard and an nvidia card but i'm getting the i915 module loading across all kernels from 2.6.28 up to 2.6.31-4. blacklisting it doesnt seem to stop it. its a recent problem within the last few weeks.

---

### Post by zika on 2009-07-24
> **dinxter said:**
> anyone else get this problem?
asus m3a motherboard and an nvidia card but i'm getting the i915 module loading across all kernels from 2.6.28 up to 2.6.31-4. blacklisting it doesnt seem to stop it. its a recent problem within the last few weeks.I have ATI HD3650 (2.6.31-999) and i915 is loaded also ...

---

### Post by dinxter on 2009-07-25
i now get i915,nouveau and nvidia autoloaded!
nvidia              10265800  26 
nouveau               591520  0 
i915                  236520  0 
drm                   192288  3 nouveau,ttm,i915
i2c_algo_bit            7076  3 bttv,nouveau,i915
video                  23388  1 i915

have added a bug if anyones finding a range of drivers autoloaded
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496)

---

### Post by taavikko on 2009-07-25
This is happening on my laptop running Radeon and desktop running Nvidia

```
devil@core7:~$ lsmod |grep i915
i915                  236520  0
drm                   193152  1 i915
i2c_algo_bit            7076  1 i915
video                  23388  1 i915
```

EDIT: confirmed the report

---

### Post by dinxter on 2009-07-25
i thought it might have to do with i915 being added to initramfs these days but it doesnt really explain how i get both nouveau and nvidia as well, i filed it against the kernel, not sure it is but i'm sure theyll know better than me

---

### Post by Hairy_Palms on 2009-07-25
happens here too, only way to stop it is totally purge the xserver-xorg-video-intel package i assume

---

### Post by psyke83 on 2009-07-25
> **Hairy_Palms said:**
> happens here too, only way to stop it is totally purge the xserver-xorg-video-intel package i assume

Don't do that. The kernel modules and the intel driver are separate.

Folks, what happens if you boot with "nomodeset" added to your grub boot string?

---

### Post by taavikko on 2009-07-25
> **psyke83 said:**
> 
Folks, what happens if you boot with "nomodeset" added to your grub boot string?

didn't make any difference on my laptop running ATI
```
:~$ lsmod | tail -5
i915                  236520  0 
drm                   193152  4 radeon,ttm,i915
i2c_algo_bit            7076  2 radeon,i915
video                  23388  1 i915
output                  3680  1 video
intel_agp              31664  0 

```

---

### Post by wayne_cat on 2009-07-25
confirmed ... ATI x1600

---

### Post by dinxter on 2009-07-25
i was thinking it might have something to do with kms, i915 now being included in the initramfs but nomodeset didnt make any diference, seems to affect more than just the i915 module. all i can think of is that both the nvidia and nouveau kernels are dkms, i was wondering if people with this problem are using dkms modules such as fglrx (i think) or are also having the same thing happen with modules in the kernel tree?

---

