---
title: "Intel Graphics Drivers not installing?"
date: 2021-06-05
forum: Installation &amp; Upgrades
---

### Post by Parrallax on 2021-06-05
Hello Everyone,

I have just installed Ubuntu Desktop 20.04 on a brand new build, the CPU is an i5 11400. The machine seems to run fine except for the graphics drivers. I cam currently stuck at a resolution of 1024x768. Going to the screen resolution settings only shows one option. I've tried upgrading the kernel, or livebooting Ubuntu 21.04, no go. I've tried installing Oibaf graphics drivers, no good either.

```

root@muru1:/home/bob# inxi -G
Graphics:
  Device-1: Intel driver: N/A 
  Display: server: X.Org 1.20.9 
  driver: fbdev,intel 
  unloaded: modesetting,vesa 
  resolution: 1024x768~76Hz 
  OpenGL: 
  renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 
  Mesa 21.2.0-devel (git-db83dc6 2021-06-05 
  focal-oibaf-ppa) 

```

I've also tried adding resolutions using xrandr in a way similar to this: [https://askubuntu.com/questions/1075157/unable-to-set-my-screen-resolution-higher](https://askubuntu.com/questions/1075157/unable-to-set-my-screen-resolution-higher) 
However whenever I do that it says it can't find the connection type e.g. VGA-1, HDMI1. I've tried many iterations but it doesn't detect it.

I'm completely out of ideas, I'd really appreciate some help.

Thanks.

---

### Post by tea for one on 2021-06-06
Was your processor released in 2021?

[s]You may need a newer kernel, therefore, why not try Ubuntu 21.04.[/s]

Whoops - I just noticed that you had tried 21.04

---

### Post by GhX6GZMB on 2021-06-06
Running lshw will give you better information on the graphics hardware.

---

### Post by ubfan1 on 2021-06-06
What does lsmod show for video?  The i915 would be what i'd expect.  Maybe try adding i915 to /etc/modules to force its load.

---

### Post by Parrallax on 2021-06-07
Thanks for the reply. Here is some of my output from lshw. I'm guessing these are the only sections that are needed?

```

*-cpu
          description: CPU
          product: 11th Gen Intel(R) Core(TM) i5-11400 @ 2.60GHz
          vendor: Intel Corp.
          physical id: 50
          bus info: cpu@0
          version: 11th Gen Intel(R) Core(TM) i5-11400 @ 2.60GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 4363MHz
          capacity: 4400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx avx512f avx512dq rdseed adx smap avx512ifma clflushopt intel_pt avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp hwp_pkg_req avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq rdpid fsrm md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=6 enabledcores=6 threads=12


*-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:50000000-50ffffff memory:40000000-4fffffff ioport:3000(size=64) memory:c0000-dffff


```

---

### Post by Parrallax on 2021-06-07
> **ubfan1 said:**
> What does lsmod show for video?  The i915 would be what i'd expect.  Maybe try adding i915 to /etc/modules to force its load.

lsmod does show i915. So I'm guessing there's no point in adding it to modules?

```
video                  49152  1 i915
```

---

### Post by deadflowr on 2021-06-07
You seem to be running into the same problem as this user over at linuxmint's forums:
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372]("https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372")
Solution there was installing the linux-oem kernel.
See if that works.

---

### Post by ubfan1 on 2021-06-07
You're right, no need to add i915 to modules if it's already loaded.  My video does have in addition, a thinkpad_acpi, so maybe something along the lines of acpi=0 on the kernel boot line (edit grub to try it out).  If that helps, you should try and refine what's minimally needed, since acpi=0 tends to clobber many desirable  things, like using more than one core. There are many acpi options to try.

---

### Post by ubfan1 on 2021-06-07
Also, do check for any firmware updates from your motherboard mfg.  Even a new machine may be several firmware versions behind, and those updates may fix these sorts of problems.

---

### Post by MAFoElffen on 2021-06-07
Just for my own comfort... You said you tried to use xrandr. I'm not trying to assume anything, so what was the output from:
```

xrandr -q

```
I see it's a Intel 11th Gen i5... So I know it is a recent motherboard... What is the motherboard?

Because in your output from 
```
lshw -c video
```
I see physical id #2... It's curious that  that shows up as unclaimed(?) To find out more about that please do:
```
[FONT=var(--ff-mono)]lspci | grep -i vga -A3[/FONT]
```

Are you using the onboard graphics(?) or other, and with what Display? In 20.04, and you running on Xorg right?

Did you go through the Trouble Shooting Flowchart in my ["Graphics Resolution"]("https://ubuntuforums.org/showthread.php?t=1743535") sticky in this Section?

Edit: The OpenSource Intel Graphics drivers are installed under Xorg XServer as a default. But in your first post, they were unloaded. Was that from your Xorg log file?

---

### Post by oldfred on 2021-06-08
There seems to be several versions of Xe graphic or other Intel graphics depending on generation of chip and whether desktop or mobile.

Xe is gen 12 or 11th-Gen Mobile Processors
Gen 11 desktop,   Intel(R) UHD Graphics 730 or Intel UHD 730

Kernel needs a setting when compiled and only some now have it.

See also:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1909457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1909457)

Gen12 Xe Graphics might not be working out-of-the-box depending upon your kernel. 
Re-booting the system while having "i915.force_probe=4c8a" Some distribution kernels including the likes of Ubuntu are already carrying the patch 
[https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1](https://www.phoronix.com/scan.php?page=article&item=intel-rkl-linux&num=1)

But they say not to use the force_probe as that is just for developers to test a new driver.
Please don't mention i915.force_probe in end-user documentation #980 
[https://github.com/intel/media-driver/issues/980](https://github.com/intel/media-driver/issues/980) & 
[https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html](https://cateee.net/lkddb/web-lkddb/DRM_I915_FORCE_PROBE.html)
[https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html](https://www.mail-archive.com/intel-gfx@lists.freedesktop.org/msg191190.html)

---

### Post by Parrallax on 2021-06-08
> **deadflowr said:**
> You seem to be running into the same problem as this user over at linuxmint's forums:
[https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372](https://forums.linuxmint.com/viewtopic.php?p=2002372&sid=7eab49285b06a0cda51c4ed7ace61615#p2002372)
Solution there was installing the linux-oem kernel.
See if that works.

This was my problem! Thank you very much for the assistance!

---

