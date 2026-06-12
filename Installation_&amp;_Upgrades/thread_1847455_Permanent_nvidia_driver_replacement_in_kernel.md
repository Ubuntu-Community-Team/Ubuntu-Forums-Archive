---
title: "Permanent nvidia driver replacement in kernel"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by HankF on 2011-09-20
How can I remove and replace an nvidia driver at boot?

Because of an nvidia driver mismatch with the kernel, my linux boots into terminal  mode.
If I log in and remove and replace the nvidia driver using modprobe -r nvidia and modprobe nvidia and starting gdm, it finishes up booting in graphics mode just fine.

HOWEVER, I have to do this _every time_ boot up linux.

**How can I remove and replace this driver during boot?**

I have tried putting the nvidia  in /etc/modules but on boot it doesn't replace the old version in the kernel. Should I blacklist it in modprobe.conf?  There's a question of timing, which happens first?

Of course it would be best to r/r nvidia in the kernel itself. I've tried for many days to replace the old model in the existing kernel but, so far, unsuccessfully. I tried dkms but can't even get to the build part. the dkms.conf isn't right AND I'm too stupid to figure it out.

This is NOT a driver or xorg.conf problem: it is a kernel problem.

---

### Post by MAFoElffen on 2011-09-20
> **HankF said:**
> How can I remove and replace an nvidia driver at boot?

Because of an nvidia driver mismatch with the kernel, my linux boots into terminal  mode.
If I log in and remove and replace the nvidia driver using modprobe -r nvidia and modprobe nvidia and starting gdm, it finishes up booting in graphics mode just fine.

HOWEVER, I have to do this _every time_ boot up linux.

**How can I remove and replace this driver during boot?**

I have tried putting the nvidia  in /etc/modules but on boot it doesn't replace the old version in the kernel. Should I blacklist it in modprobe.conf?  There's a question of timing, which happens first?

Of course it would be best to r/r nvidia in the kernel itself. I've tried for many days to replace the old model in the existing kernel but, so far, unsuccessfully. I tried dkms but can't even get to the build part. the dkms.conf isn't right AND I'm too stupid to figure it out.

This is NOT a driver or xorg.conf problem: it is a kernel problem.
Welcome to Ubuntu Forums.

Technically, it is not a Linux kernel problem, but rather an NVidia kernel problem... and a problem in the order which it is loaded in the boot process.

If you look at my instructions here in this post:
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

Look where the title is "**_Solution Step II_**". The first part of that describes how you are getting things to work presently... and where to make it persistent.  The last instructions there are for updating the initramfs boot image, which is what you're trying to do to load it when the Linux kernel boots in the intitial RAM disk-- To load the new nvidia kernel (nvidia.ko) as soon as possible = before any other graphics modules have a chance to load.

---

### Post by HankF on 2011-09-21
Thank you. 

I tried the UDEV route using a rules.d file. It has two entries: running modprobe -r nvidia and running modprobe nvidia to remove and replace the driver.

The first time I rebooted it worked just fine! 

On succeeding reboots it tried several times before succeeding, flashing terminal mode boot screen. Now it won't go into GUI automatically at all. lsmod shows the new driver module is loaded. If I do a simple sudo start gdm, it works.

At the bottom of the last kern.log it sez repeatedly:

Sep 21 10:30:48 hank-desktop kernel: [  757.754014] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.28  Wed Aug 31 18:26:00 PDT 2011
Sep 21 10:30:48 hank-desktop kernel: [  757.768075] nvidia 0000:00:0d.0: PCI INT A disabled
Sep 21 10:30:48 hank-desktop kernel: [  757.795826] Linux agpgart interface v0.103
Sep 21 10:30:50 hank-desktop kernel: [  758.989179] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
Sep 21 10:30:50 hank-desktop kernel: [  758.989194] nvidia 0000:00:0d.0: setting latency timer to 64
Sep 21 10:30:50 hank-desktop kernel: [  758.989203] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=none,decodes=none:owns=io+mem

Sep 21 10:30:50 hank-desktop kernel: [  758.989983] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.28  Wed Aug 31 18:26:00 PDT 2011
Sep 21 10:30:50 hank-desktop kernel: [  759.004074] nvidia 0000:00:0d.0: PCI INT A disabled
Sep 21 10:30:50 hank-desktop kernel: [  759.031811] Linux agpgart interface v0.103
Sep 21 10:30:51 hank-desktop kernel: [  760.225188] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
Sep 21 10:30:51 hank-desktop kernel: [  760.225203] nvidia 0000:00:0d.0: setting latency timer to 64
Sep 21 10:30:51 hank-desktop kernel: [  760.225213] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=none,decodes=none:owns=io+mem

Could I have some dependency problems?

---

### Post by MAFoElffen on 2011-09-21
> **HankF said:**
> Thank you. 

I tried the UDEV route using a rules.d file. It has two entries: running modprobe -r nvidia and running modprobe nvidia to remove and replace the driver.

The first time I rebooted it worked just fine! 

On succeeding reboots it tried several times before succeeding, flashing terminal mode boot screen. Now it won't go into GUI automatically at all. lsmod shows the new driver module is loaded. If I do a simple sudo start gdm, it works.

At the bottom of the last kern.log it sez repeatedly:

Sep 21 10:30:48 hank-desktop kernel: [  757.754014] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.28  Wed Aug 31 18:26:00 PDT 2011
Sep 21 10:30:48 hank-desktop kernel: [  757.768075] nvidia 0000:00:0d.0: PCI INT A disabled
Sep 21 10:30:48 hank-desktop kernel: [  757.795826] Linux agpgart interface v0.103
Sep 21 10:30:50 hank-desktop kernel: [  758.989179] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
Sep 21 10:30:50 hank-desktop kernel: [  758.989194] nvidia 0000:00:0d.0: setting latency timer to 64
Sep 21 10:30:50 hank-desktop kernel: [  758.989203] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=none,decodes=none:owns=io+mem

Sep 21 10:30:50 hank-desktop kernel: [  758.989983] NVRM: loading NVIDIA UNIX x86 Kernel Module  275.28  Wed Aug 31 18:26:00 PDT 2011
Sep 21 10:30:50 hank-desktop kernel: [  759.004074] nvidia 0000:00:0d.0: PCI INT A disabled
Sep 21 10:30:50 hank-desktop kernel: [  759.031811] Linux agpgart interface v0.103
Sep 21 10:30:51 hank-desktop kernel: [  760.225188] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 23 (level, low) -> IRQ 23
Sep 21 10:30:51 hank-desktop kernel: [  760.225203] nvidia 0000:00:0d.0: setting latency timer to 64
Sep 21 10:30:51 hank-desktop kernel: [  760.225213] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=none,decodes=none:owns=io+mem

Could I have some dependency problems?
Well-  You do know that "nvidia" module are normally not loaded until after this file loads right?  So why are you unloading the nvidia.ko before it would be loaded? And you have the syntax as 
```
[FONT=monospace]
[/FONT]RUN+="/sbin/modprobe nvidia"

```Right?

Did you try to update the initramfs?

---

### Post by HankF on 2011-09-21
Thanks again,

I'm embarassed, but before I saw your last response, I removed the modprobe -r nvidia rule leaving the modprobe nvida rule and BEHOLD, it works like a charm. So far I've rebooted three times in succession with the machine coming up in graphics mode each time like it should. I sure hope this solves my problem. and......

Yes I did run the update-initramfs command.

Thanks again!

---

### Post by MAFoElffen on 2011-09-21
> **HankF said:**
> Thanks again,

I'm embarassed, but before I saw your last response, I removed the modprobe -r nvidia rule leaving the modprobe nvida rule and BEHOLD, it works like a charm. So far I've rebooted three times in succession with the machine coming up in graphics mode each time like it should. I sure hope this solves my problem. and......

Yes I did run the update-initramfs command.

Thanks again!
Good Job! Hooray! 

Please mark this thread "solved" via the thread tools toolbar.

---

