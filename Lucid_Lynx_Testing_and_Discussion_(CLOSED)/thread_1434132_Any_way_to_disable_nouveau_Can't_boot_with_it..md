---
title: "Any way to disable nouveau? Can't boot with it."
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by e-rebus on 2010-03-19
Hi folks, I just tried to install the beta of Lucid on Macbook Pro 5,3 with Nvidia 9400 gfx card and the thing can't boot even in recovery mode. The last thing that I see on the screen (in recovery mode) is:

[drm] nouveau 0000:02:00.0: PRAMIN flush timeout

and the it just hangs, hence my guess about the nouveau being the problem. Anybody knows how to get replace it with something else (even vesa) so that I can install nvidia drivers?

Thanks!

---

### Post by keybuk on 2010-03-19
Add "nomodeset" to the kernel command-line.

If you're coming from the installer, press a key at the initial logo, F6 for options, and it's the first one.

If you're on an installed system, hold down shift as the BIOS finishes, press "e" to edit the boot line, cursor down to the line with "quiet splash" etc. and add it to the end of that line - Ctrl-X to boot

---

### Post by ankspo71 on 2010-03-19
Hi,
Here are some links to boot options. 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This one mentions using VESA mode:
[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

An example would be to add vga=771 to the boot command as seen here:
boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash **vga=771** 

In Lucid aplha one, I had to use the noapic option (I think) to boot the live cd. That might work on a installed ubuntu too.

I rarely had to do this so I hope this helps.
Edit: Try the other poster's advice first ;)

---

### Post by e-rebus on 2010-03-19
Thanks guys, I will test it out, see if that helps.

---

### Post by sdowney717 on 2010-03-19
blacklist the driver
> 
#get rid of this to install nvidia driver
blacklist nouveau

---

### Post by gnomeuser on 2010-03-19
and when you hopefully soon get back to a booting system please do report a bug.

ubuntu-bug linux should catch the required information

---

### Post by e-rebus on 2010-03-20
> **keybuk said:**
> Add "nomodeset" to the kernel command-line.

If you're coming from the installer, press a key at the initial logo, F6 for options, and it's the first one.

If you're on an installed system, hold down shift as the BIOS finishes, press "e" to edit the boot line, cursor down to the line with "quiet splash" etc. and add it to the end of that line - Ctrl-X to boot

That got me a little further, I can now boot to command line, but X server still does not work. I tried to install nvidia-current, but it still boots to command line. If I do startx it just hangs, I can't change terminals anymore or do anything else.

Tried to to dpkg-reconfigure xorg, but that does nothing at all. Xorg.log is also empty.

Anything else I can try to fix this?

Thanks!

---

### Post by e-rebus on 2010-03-21
Just tried to update from Ubuntu 9.10 leaving the old kernel intact and with that and "nomodeset" option I was able to boot so the new kernel must be the problem.

---

### Post by Tompalaz on 2010-03-27
everything worked for me until yesterday.
With a new kernel update I can't boot the new kernel nor a old one. Like you state, it won't work in recovery mode. (Why is nouveau even loaded at recovery?) 

Can't see that it have been any nouveau updates recently.

Edit: got it working with xorg-edgers ppa.

---

