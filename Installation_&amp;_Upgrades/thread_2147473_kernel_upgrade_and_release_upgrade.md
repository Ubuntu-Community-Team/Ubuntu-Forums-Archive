---
title: "kernel upgrade and release upgrade"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by E411 on 2013-05-22
Hello,

Here are two (related) questions. Since the very beginning my laptop had problems (see [here]("http://ubuntuforums.org/showthread.php?t=2107354")). Long story short : only kernel 3.5.0-17 is working (with others, flickering black screen at boot).

I configured grub so that the system will boot on 3.5.0-17 but I'm regularly annoyed with the software updater. Also I'd like to run do-release-upgrade because I'm still on 12.10 but I really don't fancy to go through another 5 days of text mode, log files, boot parameters and whining wife.

So this is my first question : can I run do-release-upgrade without altering my grub config and installing new kernels which will most likely not work?

And then a second question : because I am not sure of how and when a new kernel comes into play through the software updater, I tend to untick all the boxes with the word "kernel" but it is most likely suboptimal.
I am almost sure that
```
linux-signed-image-3.5.0-30-generic (New install)
```
will install that kernel and configure grub to boot it
but what about the following "important security updates"
```
linux-generic
linux-headers
linux-headers-generic
linux-image-extra
linux-image-generic
linux-signed-generic
linux-signed-image-generic
linux-libc-dev
linux-firmware
```

The list is obviously growing day after day. Should I update all/none/some?

Any suggestion on how to durably fix my problem without having to stick to 3.5.0-17 for ever is obviously welcome!

---

### Post by dino99 on 2013-05-22
what should be nice to know is : wich graphic card/chip and driver are used ?

do-release-upgrade will, of course, download & install the newest kernel, and indeed upgrade grub too.
but 3.5 is way worst than 3.8/3.9 kernel

---

### Post by E411 on 2013-05-22
> **dino99 said:**
> what should be nice to know is : wich graphic card/chip and driver are used ?




```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler LE [AMD Radeon HD 6625M Graphics]
```

```
configuration: driver=radeon latency=0
```

---

### Post by grahammechanical on 2013-05-22
Why do you want to upgrade? Is 12.10 working fine for you? Will upgrading to 13.04 fix any problems that you have with 12.10? If you are concerned about upgrading then do not upgrade. As dino99 has said upgrading to the next release of Ubuntu will of course bring in the latest Linux kernels (the latest everything, in fact) and in the process the Grub configuration files will be updated and the first reboot will be with the kernels that come with 13.04. In fact it is is most likely that the 3.5.0 kernels will be removed in the process. You may find that there remains at least one 3.5.0 kernel in Advance options. I am not sure about that.

The first update after upgrading will most likely bring in yet another new kernel. There are lots of kernel revisions in an attempt to fix the kind of issues that you seemed concerned about.

How well does your system run using the Nouveau video driver? If Nouveau is usable then I would suggest using Nouveau during the upgrade process and activating the proprietary video driver after the upgrade has finished. That way you may get to a working desktop on the first post upgrade reboot.

Regards.

---

### Post by E411 on 2013-05-23
> **grahammechanical said:**
> Why do you want to upgrade? Is 12.10 working fine for you? Will upgrading to 13.04 fix any problems that you have with 12.10? If you are concerned about upgrading then do not upgrade. 




Hi grahammechanical, everything is working fine and there is no problem to fix. The only annoying thing is the recurring messages asking me to upgrade. I was also wondering whether it is secure to stick to an older version. Would you advise me to keep 12.10 and the kernel 3.5.0-17 as long as possible?

---

