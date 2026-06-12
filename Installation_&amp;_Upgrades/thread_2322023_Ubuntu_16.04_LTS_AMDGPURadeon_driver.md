---
title: "Ubuntu 16.04 LTS AMDGPU/Radeon driver"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by Lightning Dragon on 2016-04-25
Hello,

I decided to upgrade my laptop to the latest LTS to test around with before I make the upgrade on my main PC (which is also AMD GPU powered by a R9 280). I just finished a fresh install of 16.04 and went into Additional Drivers. I know that fglrx is no longer supported and that there is only radeon drivers or amdgpu drivers, but that is what I am confused on. How do I figure out which I was defaulted on or if I was even put on one? I checked Additional Drivers and this is what it shows:

 [http://i.imgur.com/5CxBxs6.png](http://i.imgur.com/5CxBxs6.png)

And here is the output of "lspci -nn | grep VGA" is"

```
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647]
```

I have never seen that before. I'm assuming I have to be on one of the two if I am getting an output, right?



Thanks! :)

---

### Post by QIII on 2016-04-25
With the 280 I'm betting Radeon.

You can use lsmod to find out.

```
lsmod | grep radeon
```

and

```
lsmod | grep amd
```

Should be pretty clear.

---

### Post by Lightning Dragon on 2016-04-25
Hello and thank you for the reply. :)


I do not understand the results of the outputs of those commands. 

```


LD@LDPC:~$ lsmod | grep radeon
radeon               1511424  3
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
drm_kms_helper        139264  1 radeon
drm                   360448  6 ttm,drm_kms_helper,radeon

LD@LDPC:~$ lsmod | grep amd
kvm_amd                65536  0
kvm                   536576  1 kvm_amd
amdkfd                122880  1
amd_iommu_v2           20480  1 amdkfd

```

Thanks!

---

### Post by QIII on 2016-04-25
You are running the Radeon driver.  If you were running amdgpu, you'd probably not have gotten any results from radeon but would have seen amdgpu.

Those commands just asked your system to list the kernel modules with radeon or amd in the name.

---

### Post by Lightning Dragon on 2016-04-25
> **QIII said:**
> You are running the Radeon driver.  If you were running amdgpu, you'd probably not have gotten any results from radeon but would have seen amdgpu.

Those commands just asked your system to list the kernel modules with radeon or amd in the name.

Ah, I see! Thank you!  :)

Does that mean it picked the best for my system though?

---

### Post by QIII on 2016-04-25
Yes.  By default it's Radeon for everything but the Volcanic Islands (Fiji and Tonga) chips, which use AMDGPU.

---

### Post by Lightning Dragon on 2016-04-25
Thank you so much! I appreciate all the help. :)

---

