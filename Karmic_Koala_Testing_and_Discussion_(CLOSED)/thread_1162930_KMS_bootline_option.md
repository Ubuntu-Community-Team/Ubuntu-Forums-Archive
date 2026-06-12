---
title: "KMS bootline option?"
date: 2009-05-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Zorael on 2009-05-18
Not necessarily Karmic-specific (though certainly related), is there a way to enable kernel mode-setting on supported Intel videocards? Meaning, when the kernel has been compiled without having set it to use it as *default*?

I remember reading about the **i915.modeset=1** boot option but recent kernels (-30rc*) don't seem to accept it?

---

### Post by gnomeuser on 2009-05-18
KMS is not yet enabled in the Koala kernels, so you cannot simple pass a parameter to grub and expect it to work.

---

### Post by eldragon on 2009-05-18
> **Zorael said:**
> Not necessarily Karmic-specific (though certainly related), is there a way to enable kernel mode-setting on supported Intel videocards? Meaning, when the kernel has been compiled without having set it to use it as *default*?

I remember reading about the **i915.modeset=1** boot option but recent kernels (-30rc*) don't seem to accept it?

im not sure if what im going to say is distro-independant..

under arch, before passing that kernel boot option, you need to add certain modules to the initramfs

i think the needed ones are "drm" and "i915" which need to be up before the kernel is loaded. (these ones i added and it worked succesfully)

---

### Post by ssam on 2009-05-18
see [http://wiki.ubuntu.com/X/KernelModeSetting](http://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by Zorael on 2009-05-18
> **gnomeuser said:**
> KMS is not yet enabled in the Koala kernels, so you cannot simple pass a parameter to grub and expect it to work.
I'm using my own kernel. I can't get it to compile with it enabled per default for some reason, though, hence my question.

> **ssam said:**
> see [http://wiki.ubuntu.com/X/KernelModeSetting](http://wiki.ubuntu.com/X/KernelModeSetting)
That looks like it, thanks.

---

### Post by marceloshima on 2009-05-18
KMS + plymouth:

To enable plymouth at the init of the boot sequence:
[http://wiki.debian.org/KernelModesetting](http://wiki.debian.org/KernelModesetting)

Install plymouth:
deb [http://ppa.launchpad.net/macslow/ppa/ubuntu](http://ppa.launchpad.net/macslow/ppa/ubuntu) karmic main

To make plymouth work with kms enabled:
$ sudo mv /usr/share/initramfs-tools/scripts/init-top/plymouth /usr/share/initramfs-tools/scripts/local-top/

=)

---

### Post by Starks on 2009-05-19
Grrr. Solar only appears for a second when using vga=792 before going black.

---

### Post by marceloshima on 2009-05-19
KMS doesn´t work with vga=XXXX, if you are enabling kms them remove vga=xxxx, otherwise the system will freeze.

---

### Post by Zorael on 2009-06-02
What about the other way around? When KMS is enabled *per default* and by extension compiled into the kernel (CONFIG_DRM_I915_KMS=**y**, as opposed to as a module with =**m**), can it then be disabled via bootline options?

This is still on a custom kernel from git, so only semi-related to Karmic.

---

### Post by xtoudi on 2009-06-02
I wrote this how-to for Jaunty. Works great with JJ, kernel 2.6.60-rc7 so try with Karmic.


**Info:**
Jaunty 9.04 amd64 - up2date. 
my gfx: 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)

1. Compiling the new version of kernel 2.6.30-rc7 

**Extremly important:** 
 * Don't compile any framebuffer-driver in the kernel, but framebuffer-support itself (section Frame buffer hardware drivers). Everything in this section should looks like this:
```
#
# Frame buffer hardware drivers
#
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
...
...
...
```

 * Turn on (compile into kernel):
```

CONFIG_DRM_I915=y
CONFIG_DRM_I915_KMS=y
```
 * theese should be set too
```
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL=y
```
* and Framebuffer Console support
```
CONFIG_FRAMEBUFFER_CONSOLE=y
```


Obviously don't ask me how to compile kernel - you have to know that or google knows.

2. Take the latest xorg-edgers drivers: 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

3. Like stays in README the only section which should be important in xorg.conf is:
```

Section "Device"
      Identifier "intel"
      Driver     "intel"
EndSection

```


That's all!! 

No need any special commands with your kernel/boot like: i915.modeset=1 - NOTHING like that - it works with default settings!

---

### Post by Zorael on 2009-06-02
Well, that's basically what I did, and it works. But can you *disable* KMS on a single boot when compiled like that? Like, i915.modeset=0 of yore?

---

### Post by xtoudi on 2009-06-02
> **Zorael said:**
> Well, that's basically what I did, and it works. But can you *disable* KMS on a single boot when compiled like that? Like, i915.modeset=0 of yore?

Hmmmmm ... good question :-)
I think there is no way to disable this like any settings in boot/grub.

---

### Post by Eclipse. on 2009-06-02
> **xtoudi said:**
> Hmmmmm ... good question :-)
I think there is no way to disable this like any settings in boot/grub.

nomodset in the kernel config does the trick.

---

### Post by Starks on 2009-06-03
> **marceloshima said:**
> KMS + plymouth:

To enable plymouth at the init of the boot sequence:
[http://wiki.debian.org/KernelModesetting](http://wiki.debian.org/KernelModesetting)

Install plymouth:
** deb [http://ppa.launchpad.net/macslow/ppa/ubuntu](http://ppa.launchpad.net/macslow/ppa/ubuntu) karmic main**

To make plymouth work with kms enabled:
$ sudo mv /usr/share/initramfs-tools/scripts/init-top/plymouth /usr/share/initramfs-tools/scripts/local-top/

=)
 You're wrong. You need the Jaunty repo.

deb [http://ppa.launchpad.net/macslow/ppa/ubuntu](http://ppa.launchpad.net/macslow/ppa/ubuntu) jaunty  main

---

### Post by Starks on 2009-06-03
BTW, Plymouth keeps loading before KMS activates.

Because of this, I'm stuck with the Plymouth Text instead of Plymouth Solar.

---

