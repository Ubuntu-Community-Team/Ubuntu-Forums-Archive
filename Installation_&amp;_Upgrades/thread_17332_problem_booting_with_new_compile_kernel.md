---
title: "problem booting with new compile kernel"
date: 2005-02-27
forum: Installation &amp; Upgrades
---

### Post by isaac on 2005-02-27
HI,

    I have followed the steps in compiling kernel in Wikipage but when I tried to run the newly compile kernel I have error stating

"Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

the problem is that my kernel is mount the same to the root=/dev/hda1 which is the same as the default  kernel (2.6.8.1-3-386)  i have install .

     To be more detail this is what i have add in my menu.lst in the /boot/grub directory.

title  Ubuntu, kernel 2.6.81
root (hd0,0)
kernel /boot/vmlinuz-2.6.8.1 root=/dev/hda1 ro quiet splash
savedefault
boot

the sturcture and the spec is the same for my working kernel 2.6.8.1-3-386.

but the porblem about unable to mount root happens to my newly compile kernel.

Can anyone tell me what is wrong here? 

thanks in advance =)

---

### Post by isaac on 2005-02-28
i have soft part of the problem.

i enter the /boot and make a initrd image file using 
# mkinitrd -o initrd.img-2.6.8.1 2.6.8.1

then edit my grub in menu.lst

put this command in right after kernel line

initrd  /boot/initrd.img-2.6.8.1

and it works the system can boot but ith a bunch of errors.. 

logically it should have because i juz copy the same config file in 2.6.8.1-3-386..

can anyone tell me why this happen? is my way of initrd image file correct?

thanks in advance

---

