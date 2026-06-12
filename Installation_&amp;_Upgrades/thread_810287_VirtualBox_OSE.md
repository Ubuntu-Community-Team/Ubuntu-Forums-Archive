---
title: "VirtualBox OSE"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Submarine13 on 2008-05-28
Really need a hand from you guys! Having lots of trouble getting this to work. I have installed virtual box and it is setup and running in 8.04.

I have setup a winxp boot and go to run it. But before it starts an error box comes up and says:
"
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

"

Can someone, anyone help me get it working. Nothing i have tried is working!

---

### Post by erdalronahi on 2008-05-28
Did this problem appear today? Then it is because of the new kernel that came with the latest update. 

I use the non-ose version and had to reinstall the virtualbox package.

---

### Post by barnex on 2008-05-28
I can confirm this problem appeared today, after the kernel upgrade. My ose version was running fine until the update, now I have the same problem. 

Unfortunately, virtualbox-ose-modules-2.6.24-17-generic is not yet in the repos. I guess I'll just wait till they appear and then install them.

---

### Post by Submarine13 on 2008-05-28
I have tried installing it but before and got a simalar (if not the same) error. But yeah I tried it today and it won't work.
Is there a way round it or do I just have to sit and wait?
How and when will i know when and how to fix it?

---

### Post by barnex on 2008-05-28
> **Submarine13 said:**
> 
How and when will i know when and how to fix it?

I would try this: ```
sudo aptitude install virtualbox-ose-modules- <HIT TAB>
```

and see if the tab completion suggests virtualbox-ose-modules-2.6.24-17-generic. If so, complete the line and you are ready to install the modules. I hope the modules for the new kernel will be added to the repos soon. 

Hope this helps.

---

### Post by simon_w on 2008-05-28
> **Submarine13 said:**
> I have tried installing it but before and got a simalar (if not the same) error. But yeah I tried it today and it won't work.
Is there a way round it or do I just have to sit and wait?
How and when will i know when and how to fix it?

You should simply be able to boot into your previous kernel (2.6.24-16) from grub and use VirtualBox OSE as previously.  When the new modules are available in the repos, you can install them and use VirtualBox with 2.6.24-17.

---

### Post by Submarine13 on 2008-05-28
sorry to say neither worked for me. I did that terminal thing and it said i had the old kernal thing - the.16 one. 

And when I booted into the .16 one it said exactly the same error message..

Still need help :P

---

### Post by barnex on 2008-05-29
**Solved:** the needed modules appeared in the repos today. Install the correct one like this:

```

sudo aptitude remove virtualbox-ose-modules-2.6.24-16-generic
sudo aptitude install virtualbox-ose-modules-2.6.24-17-generic 

```

Worked perfectly for me. Hope your mileage doesn't vary.

---

