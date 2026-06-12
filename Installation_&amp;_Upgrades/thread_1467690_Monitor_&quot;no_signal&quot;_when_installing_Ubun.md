---
title: "Monitor &quot;no signal&quot; when installing Ubuntu 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by tarjxvf on 2010-05-01
I tried to install Ubuntu 10.04 amd64 version on desktop. I created the usb boot disk using usb-creator, and booted using that usb drive. About 5 seconds after booting from the usb drive, my LCD monitor shows "No Signal", and stayed blank afterwards. I had to push the "reset" button to reboot.

It's definitely not the problem of my usb drive, because I had successfully used it in my laptop. I believe this is a bug of the Ubuntu 10.04 installer, which somehow doesn't get along with my desktop hardware.

---

### Post by Shigoki-linux on 2010-05-01
did the screen with language select come up at all?

[http://ubuntuforums.org/showthread.php?p=9207300#post9207300](http://ubuntuforums.org/showthread.php?p=9207300#post9207300)

---

### Post by oldfred on 2010-05-01
I had to add nomodeset to get my liveCD and the first boot to work. Then after I installed the nvidia drivers it has worked just fine.
The release notes for Lucid mention that some may have to add nomodeset as a boot parameter.

I just replaced splash & quiet with nomodeset on the kernel boot line but this has another way with more information.

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by Shigoki-linux on 2010-05-01
where was the file you used? it is what i thought is the solution, but i forgot where the file was. thanks!!

nvrmnd! i got it working. thans very much for the advice!! hours of work paid off!

---

### Post by tarjxvf on 2010-05-01
I tried the "nomodeset" option in both "Try without installation" and "Install Ubuntu" with no luck. Still the same problem. The screen went blank and ctrl+alt+del etc. doesn't work, and I had to use the reset button to reboot.

I'm very frustrated. Haven't Ubuntu been thoroughly tested before released?

> **oldfred said:**
> I had to add nomodeset to get my liveCD and the first boot to work. Then after I installed the nvidia drivers it has worked just fine.
The release notes for Lucid mention that some may have to add nomodeset as a boot parameter.

I just replaced splash & quiet with nomodeset on the kernel boot line but this has another way with more information.

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by ieee488 on 2010-05-01
nomodeset is one option

i915.modeset=1 is another; this is for those for Intel 8xx video chipset

both are discussed at [http://ubuntuforums.org/showthread.php?t=1463294](http://ubuntuforums.org/showthread.php?t=1463294)

---

### Post by tarjxvf on 2010-05-01
> **ieee488 said:**
> nomodeset is one option

i915.modeset=1 is another; this is for those for Intel 8xx video chipset

both are discussed at [http://ubuntuforums.org/showthread.php?t=1463294](http://ubuntuforums.org/showthread.php?t=1463294)

Thank you. Is there an option for NVIDIA video card?

---

### Post by Daemoniq on 2010-05-10
I had a similar problem when upgrading my Thinkpad R51 from 9.1 to Lucid  10.04

The solution was to enter the GRUB2 menu by holding down the shift key  just after the BIOS had finished during boot.

I then selected a previous kernel, and got a Recovery Menu, at which  time I chose "Run in failsafe graphic mode".

I then followed workaround F here -
[http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by skaranko on 2010-11-15
Old thread, but as I ended up reading this too, thought I should add this here to help some future poor soul avoid the 3 hours of blog searching I endured, nomodeset was no help for me.

My Radeon HD5570 resulted in no signal at installation, finally resolved as follows:

1. During installation add "radeon.modeset=0 xforcevesa" instead of the default splash & quiet.

2. On first login after installation (with 1600x1200 res on my HD screen) go to System -- Administration -- Hardware Drivers and enable the ATI/AMD prprietary FGLRX driver: ahh... finally two HD screens!

Cross-linking other sites that proved helpful: [http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

Cheers,

 Samu

---

