---
title: "686 Kernel Help"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by h3h_timo on 2006-08-02
Ive read that because i have a Centrino Duo Processor, my system will scream even faster with the 686 kernel.  What is the difference between the 686 and 386 versions, and how would i do this?

Thanks for any help!

---

### Post by christhemonkey on 2006-08-02
The 686 basically allows the kernel to take advantage of improved instruction sets for your CPU (or something like that... basically it lets you go faster :) )

To install the 686 kernel:
```
sudo apt-get install linux-686 
```

---

### Post by h3h_timo on 2006-08-02
Thanks a ton :grin:

---

### Post by az on 2006-08-02
Duo means hyperthreading, I think.  In that case, 686-smp would be even better...

sudo apt-get install linux-686-smp

---

### Post by remat457 on 2006-08-02
I have been wondering about 386 v 686 also. I have an AthlonXP  2100 and Dapper installed the 386 kernel. I have also heard that after kernel v2.6 selection should not be necessary any longer. Which would be optimal?

Sorry for the dumb question, but I am new to this whole kernel tweaking thing...

thanks

---

### Post by h3h_timo on 2006-08-02
duo is a processor with physically two cores

hyperthreading is when the processor tries to emulate two cores

so instead of 686-smp... is there an even better version for core duo??

---

### Post by gva on 2006-08-02
Hello,

Thanks to all for the information above. I also have a duo core processor. When I installed the -686smp kernel, and tried to boot it hangs at the "Mounting root filesystem stage."

The entry from my /boot/grub/menu.lst for this is:
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

The one for the 386 kernel is:
title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

which works fine.

Does anyone know what the problem might be?

Many thanks.

---

### Post by christhemonkey on 2006-08-02
Can you select recovery mode (? think its that) from the GRUB menu whilst booting?
This will give more information as to the problem.

And, linux-686 and linux-686-smp both point to the same kernel.

---

