---
title: "Can not mount /dev/loop1 on /cow"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by aimeeda on 2010-03-24
I am trying to install ubuntu netbook remix from a usb stick on an MSI Wind U100. The installer boot menu comes up, but both the Try... and Install... menu options do not work. If I boot without "quiet splash --" it stops with a screen full of the following information.
 
======================================================
(initramfs) stdin: error 0
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) multi-call binary
 
Usage: mount [flags] DEVICE NODE [-o options,more-options]
 
... A list of options here ...
 
There are EVEN MORE flags that are specific to each filesystem
You'll have to see the written documentation for those filesystems
 
Can not mount /dev/loop1 on /cow
======================================================
 
I have done a few searches in the Installation & Upgrades forum and have not found the help I need.

---

### Post by jbchurchill on 2010-05-06
I get the same error. 

I have an EeePC 900A

---

### Post by dino99 on 2010-05-06
install MountManager and tweak as you need the devices and partitions

---

### Post by codex24 on 2010-05-06
> **dino99 said:**
> install MountManager and tweak as you need the  devices and partitions
How would you suggest using the MountManager when the system won't even boot?
Could you be a *little *more specific about the "tweak as you need" part?

I am having this error with ubuntu-10.04-netbook-i386.iso on an Asus EEE PC 1000HA, booting from the SD drive.

---

### Post by ar7499 on 2010-05-10
Did you ever get past this point? I am having the same problem. I am a Ubuntu newb, so any advice will be appreciated.

ar7499

---

### Post by codex24 on 2010-05-11
No, no progress. Not impressed with Ubuntu, not impressed with the kludgy install process, not impressed with this so-called "support". 
C'mon people, the freaking netbook distro will not even BOOT on the industry-leading hardware. Epic Fail.

---

### Post by jelm0 on 2010-05-12
I used usb-creator.exe on Windows to create my USB. To get past the problem, I had to recreate it with the "Discarded on shutdown, unlessyou save them elsewhere" option.

Thanks to Rich Menga post at [http://www.pcmech.com/article/ubuntu-netbook-remix-9-10-usb-install-workaround/](http://www.pcmech.com/article/ubuntu-netbook-remix-9-10-usb-install-workaround/)

---

### Post by codex24 on 2010-05-12
Hey, that worked, thanks for the response, [jelm0]("http://ubuntuforums.org/member.php?u=85457")
So, this problem has been around for a whole release cycle and no one has addressed it? If it is just a matter of a partition on the USB device not being mounted, it seems this should be easy to tweak the boot process to work around or to fix. Is this what [dino99]("http://ubuntuforums.org/member.php?u=129712") was talking about?

---

### Post by ar7499 on 2010-05-12
jelm0,

thank you for the tip. 

IT WORKS.

now I just need to learn how to use this OS :)


ar

---

### Post by aimeeda on 2010-05-31
I remade my usb stick installer and tried again. It successfully installed this time. Subsequently upgraded to 10.04. I now have the same problem as in the "**Wifi not connecting after 10.04 upgrade..." **thread.

---

