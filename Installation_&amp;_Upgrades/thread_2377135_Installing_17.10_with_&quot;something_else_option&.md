---
title: "Installing 17.10 with &quot;something else option&quot; - will the swap file be created?"
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by sbdesign on 2017-11-09
I read that 17.10 uses a swap file instead of a swap partition. If I use the "something else" install option and have 2 partitions "/" and "/home" will the swap file be created just like in the "use the whole drive" install option? If not, how do you set up 17.10 to use a swap file?

---

### Post by Dennis N on 2017-11-09
You will automatically have a swap file if no swap partitions are present. You don't have to create it.

```
dmn@Sydney-vm:/$ ls 
bin    dev   initrd.img      lib64       mnt   root  snap      sys  var
boot   etc   initrd.img.old  lost+found  opt   run   srv       tmp  vmlinuz
cdrom  home  lib             media       proc  sbin  **swapfile**  usr  vmlinuz.old

```

---

### Post by efflandt on 2017-11-10
I have not used any swap partition for many years, especially when running from flash memory (SD card) or SSD. Just curious if the swapfile in 17.10 takes up space, or is it dynamically sized if you need it? I know that swap can be minimized by altering swappiness.

---

### Post by rattskjelke on 2017-11-11
> **efflandt said:**
> Just curious if the swapfile in 17.10 takes up space, or is it dynamically sized if you need it? 
I installed Xubuntu 17.10 and used it for a couple weeks before going back to 16.04.3 LTS. I don't know if the swap file is dynamic. I used the "something else" option to install it on a laptop with 4 GB RAM and it created a swap file in the / partition that was about 1.1 GB. I did not see the size vary, but none of my applications ever use enough memory to cause swapping, and I have the sysctl set to minimize swapping.

---

