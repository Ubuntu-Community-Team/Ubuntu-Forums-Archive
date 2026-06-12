---
title: "Kernel or UDEV issue with Ubuntu 12.04 LTS"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by dccrens2 on 2014-09-14
I am a longtime Ubuntu user and am currently running 12.04. A while back I went to install the latest upgrades and patches which I do on a weekly basis. I saw that there was a new kernel 3.2.0-68. I was running 3.2.0-63. I had never had any previous problems accepting recommended kernels and patches so I let the upgrade install. When I rebooted I got a black screen with a blinking cursor. I waited and waited and waited... Nada! I then switch to a new term and saw a repeating message that said:

UDEVD [193]: timeout: killing '/sbin/modprobe -bv usb:"a long string of numbers"' [323]

I have searched the net but haven't found much that could cause this. 

I reboot the machine and let it try to boot again with the same result. I then rebooted and selected the previous kernel 3.2.0-63 in grub and everything booted up and worked fine. I then used apt-get the remove the 3.2.0-68 kernel and updated grub. So, no permanent harm was done. 

While I was able to recover, I would like to find the cause of this. Am I stuck on this kernel? Anyone ever see this?

Thanks in advance for the help...

Dave

---

### Post by JKyleOKC on 2014-09-14
The black screen with blinking cursor usually indicates a graphics driver problem; I see quite a few such problems posted and they seem to vary widely depending on exactly which video adapter your system contains. I'm running the 68 version and had no problems; my video is a relatively old Nvidia chip on the motherboard and I'm using the Nvidia driver rather than noveau.

If you can get to a grub menu when booting, you can select the 68 kernel and press "e" to edit the boot parameters. Find the line that contains "quiet splash" and add the word "nomodeset" after "splash", then press CTRL-X to boot with the edited parameters. That may fix the problem, or may not. If it does, you can make the same modification to the /etc/default/grub file to make the modification permanent. If it doesn't, perhaps searching for alternative drivers is indicated.

Hope this helps.

---

### Post by dccrens2 on 2014-09-15
Jim,
Thanks for this. I will give it a try when I get some time in the next week. I have 2 Nvidia 560 GTX cards. I also am using the proprietary NVIDIA drivers. I am using the 304 drivers loaded from the hardware additional drivers app under system settings. There are newer drivers there as well, version 331. However, when I tried switching to these I get a weird error where  it seemed to hang. I then got a notice that my root partition was 100% full. I had to drop to single user, and purge the new drivers and do and aptitude autoclean. My root partition is 45GB and only at 2% used so whatever it was doing was filling space fast. Wasn't able to determine what the issue was but was able to go back to the 304 drivers.

---

