---
title: "Upgrade to Lucid, black screen, nomodeset not working."
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by jfinner1 on 2010-07-27
I just upgraded to Lucid Lynx, and like most people, I'm getting the black screen during boot. So, I went into the grub edit screen, and I tried every variation of the nomodeset fix I could find. So far, nothing has worked. I don't know what graphics card I have, but it's always given me problems. Can anyone help?

---

### Post by Cason on 2010-07-27
Sometimes this is also caused by a processor problem. If that's the case, you could try either "processor.max_cstate=1" or "nohz=off" instead of "nomodeset". It doesn't sound like you need help making changes to your grub boot options, but if you do, I posted some directions [here]("http://ubuntuforums.org/showthread.php?t=1540340").

---

### Post by jfinner1 on 2010-07-27
Neither of those worked either. One thing I noticed when I was looking through your instructions. In this line

```
linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d2139a9e-b3ee-4684-a7ee-d654bbfcccd7 ro splash vga=789  quiet splash
```

I am missing the part that says "splash vga=789". I tried just typing it in, but nothing happened. Could that be effecting something?

---

### Post by Cason on 2010-07-30
No, I don't think that's the issue. The line is going to look slightly different depending on the individual computer and the kernel version that's running. I don't have any other ideas, but I'm newer to this than many people; hopefully someone else can help. :)

---

### Post by oldfred on 2010-07-30
Use this to see whta VGA controller you have:

lspci | grep VGA

fred@fred-desktop:~$  lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

They have obsoleted any VGA= settings:
vga=799 is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

Some other settings but it is best to know what video card you have:

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

