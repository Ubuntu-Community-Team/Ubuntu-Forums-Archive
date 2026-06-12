---
title: "Linux Headers Boot Help!"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Spydr4590 on 2008-08-24
I'm trying to boot off of an old kernel due to a stability issue. I ran ```
sudo apt-get install linux-headers-2.6.24-18
``` Which installed all of the old kernels.

I then edited my boot ```
sudo gedit /boot/grub/menu.lst 
``` I added ```
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/mapper/linux-root ro quiet splash
initrd		/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/mapper/linux-root ro single
initrd		/initrd.img-2.6.24-18-generic
``` However when I try to boot off this kernel after a reboot it gives me error code 15.

---

### Post by spiderbatdad on 2008-08-24
create initramfs for the new kernel```
sudo update-initramfs -c 2.6.24-18
```There might be a longer kernel name? like 2.6.24-18-i686...or whatever.

---

### Post by Spydr4590 on 2008-08-24
I can't seem to get this command to work? Could anyone else explain this further? I checked the help wiki on this command and that didn't help too much.

---

### Post by Spydr4590 on 2008-08-26
Really need some help here so I can make my system stable.

---

### Post by wgrant on 2008-08-26
The headers won't do you any good... you want linux-image-2.6.XX-XX-generic. Have you filed a bug on the issues that you encounter with later kernels?

---

### Post by Spydr4590 on 2008-08-26
I've submited my bug [https://bugs.launchpad.net/ubuntu/+bug/261394]("https://bugs.launchpad.net/ubuntu/+bug/261394") However I just want to downgrade or upgrade my kernel. I'm positive this will fix my issue. If problems like this keep happening I might just go back to windows. Tired of the problems with linux.

---

### Post by Spydr4590 on 2008-08-26
Doesn't matter anymore. After a year of problems with Ubuntu, and video manufacturers. Plus the pain of installing games I want working. I just went back to windows. Thanks for the responses those that replied.

---

### Post by wgrant on 2008-08-26
> **Spydr4590 said:**
> I've submited my bug [https://bugs.launchpad.net/ubuntu/+bug/261394]("https://bugs.launchpad.net/ubuntu/+bug/261394") However I just want to downgrade or upgrade my kernel. I'm positive this will fix my issue. If problems like this keep happening I might just go back to windows. Tired of the problems with linux.

I told you in my post above which package you needed to install...

---

