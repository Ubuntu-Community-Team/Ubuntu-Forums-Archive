---
title: "cpu upgrade to X2 -&gt; kernel oops"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by blazerte on 2008-01-30
Upgraded my cpu from AMD Athlon 64 3200 to Athlon 64 X2 4800. Still running 32 bit kernels, not 64.
Also put in a new Ati agp video card. 

Debian testing partition boots ok showing two cpus, etc., and I put in the radeonhd X driver for the video card. Works fine.

But when I try booting to my Ubuntu 7.1 partition, the kernel (2.6.22-14-generic) oops a bit after fsck.  Necessary to unplug the PC to get it to stop; on/off doesn't work. First time, all I saw was the progress bar locked up. The second time an fsck was scheduled so it dropped into command line and I saw the oops. I had previously changed the X driver to vesa from within Debian but it never gets that far. 

I see a fair number of bug reports relating to booting on AMD 64 X2, but no solutions. 
Is there some voodoo I can put in my grub boot line to get this thing up?

LATER:
It's oopsing after:
* Starting ACPI services ...
24.832000] Oops
          :000 SMP
         Module in kernel made to load kernel null pointer reference (or something like that)

I've tried:
pic=noacpi   :    no help
irqpoll           :    same
acpi=off noacpi   :   lots of other problems, lost interrupts etc.     

I think I need a new kernel,  2.6.22-14-generic doesn't seem to cut it.
What to do ... ?

LATER:
According to responses to this bug:
 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159049](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159049) 
about a similar problem, an upgrade to the latest 2.6.24 kernel is required. 

Odd, because Debian's 2.6.22 kernel works fine. 

Installing a new kernel in a partition that I can't boot sounds tricky. 
I could try to chroot from Debian but think it would be safer to do re-install from one of the Hardy Heron Alpha cd's.

---

### Post by blazerte on 2008-01-30
Neglected to mention that Ubuntu V7.1 install disk didn't boot either.
So tried the kernel on a new Hardy Heron Alpha3 disk. 
Same problem with that install disk. 
LATER:
Tried alpha4 with V2.6.24.2 kernel, same problem. The alternate install disk boots and installs fine, But when you reboot, it hangs.

---

### Post by blazerte on 2008-03-20
Finally, Ubuntu boots live and installs with the latest hardy Heron Alpha 6.
I think that's kernel v2.6.24-11 or -12

But Reboot hangs things up. I need to use the off/on switch to get it started again. 
Shutdown works ok though.

Also the proprietary fglrx driver doesn't work with my new card, (ATI HD 2600 XT, RV630 chip). But I was expecting that, as the latest fglrx drivers didn't work in Debian either. Seems to be a problem with monitor detection also.

So apt-get xorg's radeonhd driver and that works fine. But the xorg ati driver doesn't for some reason, although it works in Debian.

Anyway, getting there.

---

### Post by Jammy4041 on 2008-03-20
I think its because you have used a 32-bit (x86 architecture) rather than a 64 bit version.

Perhaps you could try using a 64-bit disc?

But I would reccommend against it for a while: software support is lacking at the moment.

Maybe in a year or two, but not now.

it's best to go for the 32-bit version at the moment to ensure compatibility.

---

### Post by blazerte on 2008-03-20
Actually, you're right, this time, alpha 6, I install the amd64 version. I haven't tried the 32 bit alpha 6. Maybe that won't work?

But back with alpha3, neither worked. Both the 32 or 64 live disks locked up during boot. So things are getting better ...

---

