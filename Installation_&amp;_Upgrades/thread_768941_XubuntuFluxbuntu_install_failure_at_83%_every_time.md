---
title: "Xubuntu/Fluxbuntu install failure at 83% every time!"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by heyho on 2008-04-26
I'm in the process of trying to setup a box for my workshop, mainly as a jukebox, but also for a little surfing if needed.

Basically, it's an old P2 setup, with 192mb ram - a Siemens motherboard if I recall correctly.  I've tried to install Xubuntu, and Fluxbuntu, but each time, I reach 83% of "installing the base system", and eventually all disc activity ceases, then after a further 10 minutes the system just shuts down!

I've tried different media (the discs are good, as they've installed on other boxes), different hard drives, and even different ram, but it all ends the same way.  The rom drive has been in another system, and did a complete Xubuntu install perfectly.

The main reason I'm persevering with this is because it's the only system I have with an ISA socket, which I need to run the dedicated video card for my keycorp 10" lcd monitor.(Unless this is the problem!)

I've successfully installed puppy 3.01, but would really like to get one of the 'buntus working, as I'm now familiar with some of the great software in the repos.

Thanks, Heyho.

---

### Post by Pumalite on 2008-04-26
Try the Xubuntu Alternate CD. You cannot boot a Live CD with 196 MB of RAM.

---

### Post by heyho on 2008-04-26
> **Pumalite said:**
> Try the Xubuntu Alternate CD. You cannot boot a Live CD with 196 MB of RAM.

Maybe I should have added, it was the alternate CD (the Xubuntu download page  recommends 128+ for the liveCD)- I tend only to use the alternate installer anyhow, as I have more success with my laptops.

Also, I can successfully boot in DSL as well.  Maybe the kernel just doesn't like my motherboard!

---

### Post by Pumalite on 2008-04-26
In case is your monitor, you could edit the boot line with dif VGA=0x317, vga=791, vga=775, etc. If you want to play with boot parameters, here is a load:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi pnpbios=off irqpoll

---

### Post by heyho on 2008-04-26
Thanks for the speedy reply.

Editing boot lines isn't something I've tried before, but I'm willing to give it a go!  I'll have a look at the links you've posted, and update this post with the results - be it good or bad.

Thanks again, it is much appreciated.

---

### Post by heyho on 2008-04-29
Well, after a little digging, it would appear that it is indeed the ISA video card causing me the problems, as far as I can tell, the only GUI operating systems the card has suitable drivers for is windows 95/98, but even that was not easy.  I have 98 up and running, and after a struggle, I have managed to get up and running @ 640x480x16bit colour depth.

When booting into puppy, the only option I'm able to use is xvesa, xorg just refuses flat.  Even when running in xvesa, there are no resolution options available at all.

Before I start playing with boot parameters, would it be likely that I'm wasting my time?  I'm willing to put some time into this if I'm able to get flux/xubuntu running, but if I'm flogging a dead horse, I'll give up now and continue down the '98 path.

---

### Post by Pumalite on 2008-04-29
Never say die. You can only learn from this exercise.

---

### Post by titi_delicieux on 2008-11-03
I had the same problem and I just had to wait about 10 minutes

---

