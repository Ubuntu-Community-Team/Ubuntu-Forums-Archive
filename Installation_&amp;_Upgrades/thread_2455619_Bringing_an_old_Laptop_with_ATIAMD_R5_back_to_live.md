---
title: "Bringing an old Laptop with ATI/AMD R5 back to live?"
date: 2020-12-23
forum: Installation &amp; Upgrades
---

### Post by docdoc2 on 2020-12-23
Hey ho,

i am trying to relive an old HP Pavillon 17-f042ng from the year 2014. I noticed the machine is running very hot quickly(cpu fan is new though), and also the CPU goes up to 100% when only playing a youtube video. When stopping lightdm, it goes down though. So i assume the integrated graphics are not addressed properly and there is no hardware acceleration. 

Inside is an AMD/ATI R5 M230 Chip.

I found out there are the following options:

-Open source radeon driver: this is installed in the kernel and is used on a fresh installation, but doesn't really work
-AMDGPU: This can either be done by some kind of update or via oibaf drivers, but it doesn't really make anything better
-AMDGPU-PRO: I dont think this will work, as it is only for newer models.
-fglrx: It seems not to be up to date, but i would like to try it, anyone knows how i could do that? I think i would need to install Ubuntu 14.04 then.

---

### Post by QIII on 2020-12-23
Assuming that this is NOT a hybrid Intel/AMD graphics solution:

The radeon module, which is selected for load at install time, is your only choice.  Stay away from PPAs that claim to offer better drivers.  Those are unlikely to work any better and are likely to cause problems with updating from the repos.  The OIBAF amdgpu module will not work any better than the open source amdgpu module already included in your kernel  -- amdgpu is for newer hardware and won't work if your hardware is unsupported. 

fglrx is less than unmaintained.  It is dead and will not work with modern distros.  amdgpu and AMDGPU-PRO are applicable only to new physical hardware and simply will not work with anything very old.

Is this a hybrid graphics machine?

Would you please post the results of 

```
lsmod | grep radeon
```

and 

```
lsmod | grep amdgpu
```

Those will check for whether the radeon or amdgpu kernel modules are loaded.

---

### Post by GhX6GZMB on 2020-12-23
@QIII

What's the problem with hybrid Intel/Radeon graphics?

I run two HP 6910p with Lubuntu 20.04 (actually from 18.10 up until today).
One has only the Intel graphics, the other has Intel/Radeon graphics and both work directly from installation. The first with 1280x800, the other with 1440x900.

Admittedly, they are 6 years older than the Pavillion, but still...

---

### Post by QIII on 2020-12-23
The "problem" is that there is no way to switch on the fly from Intel to AMD with radeon or amdgpu from the GUI.

One or the other must be blacklisted in the BIOS/EFI.  Just asking if the user has the simplest solution to deal with.

---

### Post by GhX6GZMB on 2020-12-23
> **QIII said:**
> The "problem" is that there is no way to switch on the fly from Intel to AMD with radeon or amdgpu from the GUI.


I understand. But why would anyone want to do that?

The experience I have with my machines (and this is no way representative, I know), is that the installer selects the "best" graphics and install those. So on my Intel/Radeon machine the Intel graphics are ignored and not installed. As opposed to Intel-only machine where the Intel drivers are installed.

---

### Post by CelticWarrior on 2020-12-24
> [COLOR=#000000]But why would anyone want to do that?[/COLOR]
Because people do it in Windows?
The idea behind hybrid graphics is the possibility of using the more energy efficient iGPU (Intel in your case) for most tasks and only switch to the dGPU (AMD, idem) for software that demands more (games, etc.). Of course you can use only the dGPU (high performance) and in many cases it's a must for external monitors but at the expense of battery life, an important detail for a laptop.

---

### Post by GhX6GZMB on 2020-12-24
@CelticWarrior:
OK, understood. Never ran into that scenario myself (I'm not a gamer).
You learn every day.

---

### Post by docdoc2 on 2020-12-27
Thanks for the quick reply. As i now changed the fan and could see the hardware, i belief the system does not have two graphic controller, at least i couldn't see a dedicated chip. My main goal is to keep the heat and cpu/gpu consumption low.


The Output of lsmod | grep radeon

```
radeon               1474560  8
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   106496  2 amdgpu,radeon
drm_kms_helper        184320  2 amdgpu,radeon
drm                   491520  11 gpu_sched,drm_kms_helper,amdgpu,radeon,ttm

```

And that of lsmod | grep amdgpu

```
amdgpu               4579328  0
amd_iommu_v2           20480  1 amdgpu
gpu_sched              32768  1 amdgpu
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   106496  2 amdgpu,radeon
drm_kms_helper        184320  2 amdgpu,radeon
drm                   491520  11 gpu_sched,drm_kms_helper,amdgpu,radeon,ttm


```

I purged the oibaf drivers with ppa-purge again. According to lshw -c video nothing changed (the output was the same with the oibaf ppa):

```
       description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:fea00000-fea3ffff memory:c0000-dffff


```

I guess i will be fine with the radeon module. I am just wondering why the temp is at 60°C when there is just no program running. Also, it goes up to 99°C very quickly, while the cpu usage is rather low. That is why i assumed it was a problem with the gpu. 

Right now Lubuntu with the lxqt desktop environment keeps the cpu consumption down very well.

---

### Post by CelticWarrior on 2020-12-27
> **ml9104 said:**
> @CelticWarrior:
OK, understood. Never ran into that scenario myself (I'm not a gamer).
You learn every day.

So, if you aren't a gamer or doing intense computational tasks (machine learning, video conversions, etc.) then very likely you don't need the extra AMD graphics dGPU. The iGPU Intel is likely adequate for everything else including UHD video.

You could have saved a lot of money by going for an entry level laptop with only an iGPU. Some entry level AMD APU based laptops are an excellent value for the money, often better than the Intel solutions in the same market segment. And keep saving on electricity costs although negligible for only one computer in an household in most parts of the world. 

Here's an example that many people can relate much better than computer hardware:

If you're commuting in urban areas you don't need a 233HP 4WD 2.0LT GDI Luxury SUV like the famous [Changan CS75 Plus]("https://www.changan.com.cn/car/cs75plus/"), you only need the entry level 1.5L [Changan CS15]("https://www.changan.com.cn/car/cs15-2019/"), for about half of the price.

---

### Post by GhX6GZMB on 2020-12-27
> **CelticWarrior said:**
> So, if you aren't a gamer or doing intense computational tasks (machine learning, video conversions, etc.) then very likely you don't need the extra AMD graphics dGPU. The iGPU Intel is likely adequate for everything else including UHD video.

You could have saved a lot of money by going for an entry level laptop with only an iGPU.

Most likely not. My laptops are HP 6910p as stated, ~12 years old. Bought off eBay for aroung 50 Euro each. Whether you get one with or without GPU is uncertain.
As you see, my needs are not bleeding edge.

But apart from that, you're probably right.

---

