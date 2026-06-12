---
title: "insmod error: Unknown symbol"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by sswami on 2013-02-17
Hello,

Can anyone please help me in this? I am having this problem with $`uname -r` 
$3.5.0-23-generic.

1) I have downloaded the code for ivshmem from git://gitorious.org/nahanni/guest-code.git and am trying to build the uio_ivshmem kernel module

2) From nahanni/kernel_module/uio dir, I do a 
- "sudo make" which builds the uio_ivshmem.ko file and then a 
- "sudo make install" which copies the file to:
   cp uio_ivshmem.ko /lib/modules/3.5.0-23-generic/kernel/drivers/uio/

3) I do a "sudo insmod uio_ivshmem.ko" and get the following error:
insmod: error inserting 'uio_ivshmem.ko': -1 Unknown symbol in module

4) I do a "dmesg | tail" and see the following:
[ 183.675921] uio_ivshmem: Unknown symbol __uio_register_device (err 0)
[ 183.675942] uio_ivshmem: Unknown symbol uio_event_notify (err 0)
[ 183.675955] uio_ivshmem: Unknown symbol uio_unregister_device (err 0)

5) I do 'cat /lib/modules/3.5.0-23-generic/build/Module.symvers | grep "uio" ' and get the following:
0x49988737 uio_event_notify drivers/uio/uio EXPORT_SYMBOL_GPL
0x493c2f92 uio_unregister_device drivers/uio/uio EXPORT_SYMBOL_GPL
0xb6583632 __uio_register_device drivers/uio/uio EXPORT_SYMBOL_GPL

6) I do "cat /usr/src/linux-headers-3.5.0-23-generic/Module.symvers | grep uio" and get the same output as in 5) above

7) I found in this link
[http://www.linuxchix.org/content/courses/kernel_hacking/lesson2](http://www.linuxchix.org/content/courses/kernel_hacking/lesson2)
[http://www.linuxchix.org/content/courses/kernel_hacking/lesson8](http://www.linuxchix.org/content/courses/kernel_hacking/lesson8)

that module versioning should always be turned off

8) I do a "sudo make menuconfig" and it shows me that module versioning is turned ON

My question is "Will turning OFF module versioning help?" And if so, how do I do it? If not, what should I do?

I tried both 12.10 and 12.04 and have the same issues in both.
And if this helps "ls -l /usr/src" outputs the following:

linux-headers-3.5.0-17
linux-headers-3.5.0-17-generic
linux-headers-3.5.0-23
linux-headers-3.5.0-23-generic

thanks in advance
-saswati

---

### Post by dino99 on 2013-02-17
why are you not following their howto ?  ;)

[http://www.gitorious.org/nahanni/guest-code/blobs/9d29c6fb0cf454710436d8f9d8ccbd5829be8c58/ivshmem-server/README](http://www.gitorious.org/nahanni/guest-code/blobs/9d29c6fb0cf454710436d8f9d8ccbd5829be8c58/ivshmem-server/README)

---

### Post by schragge on 2013-02-17
Hope these links will help
[list]
[*][http://www.codewhirl.com/2012/04/how-to-compile-a-single-module-in-ubuntu-linux/](http://www.codewhirl.com/2012/04/how-to-compile-a-single-module-in-ubuntu-linux/)
[*][http://tldp.org/LDP/lkmpg/2.6/html/x181.html](http://tldp.org/LDP/lkmpg/2.6/html/x181.html)
[*][http://blog.markloiseau.com/2012/04/hello-world-loadable-kernel-module-tutorial](http://blog.markloiseau.com/2012/04/hello-world-loadable-kernel-module-tutorial)
[/list]

---

### Post by sswami on 2013-02-18
Thank you very much for your prompt reply. The "ivshmem_server" and the ivshmem device are 2 separate things. The "howto" is for "ivshmem_server" and I don't need that. I need only the device.

Any way, please disregard my earlier post. I have been able to resolve the issue. 

regards
-saswati

---

### Post by fdrake on 2013-02-18
> **sswami said:**
> Thank you very much for your prompt reply. The "ivshmem_server" and the ivshmem device are 2 separate things. The "howto" is for "ivshmem_server" and I don't need that. I need only the device.

Any way, please disregard my earlier post. I have been able to resolve the issue. 

regards
-saswati

can you share with us your solution , since I am interested in knowing what you did (did you turm off the "module versioning support" from xconfig?).
Also other ppl facing your same problem in the future may want to know too. :D

---

