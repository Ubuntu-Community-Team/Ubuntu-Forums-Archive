---
title: "Blank screen after upgrade from 12.4"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by jirkarck on 2016-07-25
Good afternoon,

I have the problem after upgrading my Ubuntu 12.04 to 14.04 and I have found the same problem when doing clear instalation of 14.04 on the same HW. I can see GRUB and several lines while booting, but after one second, my monitor goes to energy saving mode and turns off on both analog and digital video outputs. It is the same with "noapic" and "nomodeset" options and while booting into fail save mode. I've tried to connect by ssh and all other services seems to run ok - it is just about the video output. I'm pretty sure that the problem is caused by updated kernel (3.2.16 to 3.13.11), because if I go to GRUB and boot upgraded Ubuntu with old kernel, everything works fine. I'm attaching boot.log and dmesg with old and new kernel. Could you please advise me another fail save GRUB setting or something another to try?

Thank you very much for any idea :-)

---

### Post by nikefalcon on 2016-07-28
Might help to know the make/model is your video card. Also, is it integrated or dedicated? 
Paste the output of: ```
sudo lshw -C video
```
Although if all else fails, you should consider upgrading to 16.04 or just use the old/other kernel.(If that's not going to be an issue.)
Good luck!

---

### Post by nikefalcon on 2016-07-29
In the log files that you provided:
In old.dmesg: 
```
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae  root=UUID=499edec4-eb48-4e68-a9cc-bcd98b430255 ro quiet nomodeset  915.modeset=0 
```
In new.dmesg: 
```
[    0.000000] Kernel  command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-92-generic  root=UUID=499edec4-eb48-4e68-a9cc-bcd98b430255 ro quiet nomodeset  915.modeset=0 
```

The boot parameter you want is "i915.modeset" set to 0 for intel cards, so it should read:
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-92-generic root=UUID=499edec4-eb48-4e68-a9cc-bcd98b430255 ro quiet i915.modeset=0 
```
Note that this might reduce the maximum resolution that can be displayed.

---

