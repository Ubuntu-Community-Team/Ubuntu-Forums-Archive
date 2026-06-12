---
title: "no sound on 10.10 and missing /dev/dsp on lenovo ideapad y 530"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by peterpan7191 on 2010-10-20
No sound on my lenovo ideapad y530 since upgrade to 10.10 and the /dev/dsp is missing after every reboot.

The audio device ouput for "lspci -v" is 

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo Device 3a0d
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d3d00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel modules: snd-hda-intel
```I initially had sound coming through my 4.1 speaker system including the sub-woofer in 9.04,9.10 and also in 10.04 through out the sequential upgrades.

Expecting help.

---

### Post by autark on 2010-10-20
/dev/dsp missing is exactly according to policy. See [https://bugs.launchpad.net/bugs/579300](https://bugs.launchpad.net/bugs/579300).

---

### Post by peterpan7191 on 2010-10-20
Ok. [autark]("http://ubuntuforums.org/member.php?u=910393") Thnx for the info.

But doesn't that mean there will be a lot of applications that will stop working ??


Primarily there is not sound at all and this is a lot troublesome 

and secondary things - 
Im a noob to the things relating the sound in ubuntu and things like ALSA and OSS (i just know they correspond to the working of sound devices). So can u like give more information on how to get some applications like "gtkguitune" (a guitar tuner) work. It gives the /dev/dsp missing error.

---

### Post by autark on 2010-10-21
I'm sorry but I don't see an easy solution to this problem (no /dev/dsp). There is supposed to be a thingy called OSSp that should provide some basic OSS compatibility, but I haven't found out how that is supposed to work. 

If OSSp doesn't work for you, you could compile a custom kernel or try finding a PPA that provides the missing modules. Other than that, you might consider downgrading to 10.04 or finding another distribution.

---

### Post by peterpan7191 on 2011-04-30
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662009](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662009)

Seems like a bug fix has been made for higher kernels of 10.10 
and sound directly working in 11.04 .....

---

