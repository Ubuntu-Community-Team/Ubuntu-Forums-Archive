---
title: "os selection on dual boot"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-03-19
I was wondering how many of these choices where neccesary, and what they are.. and also how many entries will it allow?

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-10-generic
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-10-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-10-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-10-generic (recovery mode)
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-10-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro  single
initrd		/boot/initrd.img-2.6.28-10-generic

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro quiet splash 
initrd		/boot/initrd.img-2.6.28-9-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-9-generic (recovery mode)
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/vmlinuz-2.6.28-9-generic root=UUID=e3923555-dd18-405a-8ee6-16737784112e ro  single
initrd		/boot/initrd.img-2.6.28-9-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		e3923555-dd18-405a-8ee6-16737784112e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by whoop on 2009-03-19
Well they are all of your currently installed linux kernels (normal boot and recovery mode) and your windows os. It will probably grow until you do (another) distribution upgrade. You need at least one (working) kernel to use your operating system but it is advised to keep some more. I always keep the latest kernel and the last working kernel before that. Keeping older kernels is handy for compatibility and if you ever get into problems running your latest kernel.

You can remove old kernels with synaptic. search for linux-image, that should list your kernel installs. Be sure to remove the right ones, and also leave linux-image-generic :-)

P.S. not that there is anything wrong with asking questions like this, but should you be running jaunty on your machine. It's not even beta yet. You could run into serious problems.

---

### Post by joshuapbell on 2009-03-19
> **whoop said:**
> Well they are all of your currently installed linux kernels (normal boot and recovery mode) and your windows os. It will probably grow until you do (another) distribution upgrade. You need at least one (working) kernel to use your operating system but it is advised to keep some more. I always keep the latest kernel and the last working kernel before that. Keeping older kernels is handy for compatibility and if you ever get into problems running your latest kernel.

You can remove old kernels with synaptic. search for linux-image, that should list your kernel installs. Be sure to remove the right ones, and also leave linux-image-generic :-)

P.S. not that there is anything wrong with asking questions like this, but should you be running jaunty on your machine. It's not even beta yet. You could run into serious problems.


Thank you for your response... And believe me I am well aware of the risks of running beta software... and I do not use it as my main machine... I just got bored of vista and wanted to try something new. First it was Windows 7... but that got old too...so now I am using Jaunty which has been amazing so far!

---

### Post by Halow on 2009-03-19
Also a side note, when you remove them with Synaptic, it'll update your grub menu.list automatically to reflect fewer kernels. So, more room, less scrolling when you need to get to Windows.

I make sure to keep an older working kernel as well. After one Kernel Panic I never want to do that again. >_<

---

