---
title: "Differences in kernels"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2011-03-09
Hi guys,
(been a while)

I'm trying to find documentation on the key differences in the different "flavours" of kernels available during (mostly expert-mode) installation.

At some time during the installation process the following options are presented:
> 
The list shows the available kernels. Please choose one of them in order to make the system bootable from the hard drive.| 

Kernel to install:

linux-generic
linux-preempt
linux-server 
linux-virtual
linux-image-generic
linux-image-generic-lts-backport-maverick
linux-image-preempt
linux-image-server 
linux-image-server-lts-backport-maverick
linux-image-virtual
linux-image-virtual-lts-backport-maverick
linux-image-2.6.35-25-virtual
linux-image-2.6.35-25-server
linux-image-2.6.35-25-generic
linux-image-2.6.35-23-virtual

etc, etc

Some of the options are pretty obvious, such as "server" for servers & "generic" for more generic systems such as desktops, but other, such as "virtual" are ambiguous; is the kernel optimised for the the VM host (Dom0) or clients or both? 
& what the heck is preempt? preemptive strike into some 3rd-world back-water country? must be, because there's very little in the way of documentation available on the subject..... (I know it's actually a low-latency build, but in the absence of any docco's, I can just make stuff up as it suits me)

For something so **fundamentally important** to a system, I would've expected at least **some** documentation to be available (maybe under [https://help.ubuntu.com/community/Kernel](https://help.ubuntu.com/community/Kernel)).

Is anyone able to give a brief explanation of the differences in these kernel options?

---

### Post by freakalad on 2011-03-10
Some more available kernels available post-install:

> 
linux-image-386
linux-image-ec2
linux-image-generic
linux-image-generic-lts-backport-maverick
linux-image-generic-pae
linux-image-generic-pae-lts-backport-maverick
linux-image-itanium
linux-image-mckinley
linux-image-rt
linux-image-server
linux-image-server-lts-backport-maverick
linux-image-ume
linux-image-virtual
linux-image-virtual-lts-backport-maverick
linux-image-xen


Again, some are pretty obvious (ec2, xen), but others not (mckinley, rt)

---

### Post by b0b138 on 2011-03-11
Some, im not sure either.

some are just meta packages that point to the newest one, like linux-generic points to linux-image-generic points to linux-image-2.6.35-25-generic. So when 2.6.35-27-generic (for ex.) comes out, the linux-generic package gets flagged for an update, which in turn installs -27 as a new package.  This also applies to server,virtual,preempt

The lts-backport-maverick is the 2.6.35 kernal from maverick, as lucids was 2.6.32

The virual is intended to be run in the guest. xen, not sure.

mckinley says something about ia64?? i guess it goes with itanium.

the rt kernel is i think a low latency kernel, useful for audio apps. Default in ubuntu studio i think?

pae is the physical address extension so you can run more than 4G ram on 32 bit.

ec2 is some amazon cloud thing thats above my pay grade lol

---

### Post by freakalad on 2011-03-14
Thanks for the info.

Much of it I've been able to extrapolate myself, of at least hazard a guess, but it would be *extremely* "handy" to have some sort of official documentation, to at least confirm or correct those guesses.

For example, I've recently come to realize that the linux-*-virtual kernels are intended for use on the VM host (I use KVM myself), but I've been under the impression that the kernel was an image optimized for a VM client (such as paravirt hardware drivers).
But when I loaded this kernel on my host, it went ahead & disabled all my USB interfaces (bye-bye keyboard) & my NIC. To an extent I can understand why USB might be disabled (USB is a host-driven serial interface & uses up precious CPU-cycles), but raises concerns re other serial devices, such as SATA (they're OK, but still...). 
But why on earth would the NIC be disabled?

I've also managed to dig up some info on the *preempt, and it seems to be a kernel optimized for low-latency use (with the options). Similar to the *-rt, if I were to guess (& in the absence of any docco's, that's all I can do) 
This would be extremely handy for HPC, such as VoIP.

All I'm saying is: some documentation on kernels available from the official repo's would be very nice, so that I can make an informed decision.

---

