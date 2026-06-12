---
title: "help modifying linux kernel"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by dustinmarlowe56 on 2010-07-28
Ok, so I have been playing around with Ubuntu for about eight months now and I have learned a good bit about it. Now I want to start experimenting with modifying the linux kernals that ubuntu runs on. 

My question is this: How would I go about removing any unecessary drivers or parts of a kernel that I know for a fact I would not need for an installation on a specific system, such as if I have an ATI graphics setup and there fore want to remove all other graphics options in the kernel. and also, would such modifications have an impact on the speed of a system both during the boot cycle and while in general use? Would it also cause the amount of ram needed for the system to idle or run?

Thanx

---

### Post by Icarus315 on 2010-07-28
This is something I would like to know too: is there a way to find out exactly what modules are needed for your specific system and then build a kernel which has ONLY those modules.  With optional loadable modules as well like VirtualBox and others.

Then, is there a good primer aimed squarely at beginners on how to compile the latest kernel with what you have found to be needed?

I'd like to be running a custom kernel and perhaps *you* can point me towards the knowledge to do so!

---

### Post by dustinmarlowe56 on 2010-07-28
here is a link to how to modify and compile them, thats all i know so far.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Icarus315 on 2010-07-28
That link doesn't address Lucid directly.  I know I should fall under the "reasons to NOT compile kernel" BUT I'd like a minimal kernel that I can keep up to date myself from kernel.org.  With ONLY what I need, nothing more or less: small footprint.  Of course I probably wouldn't be able to run the absolute latest like 2.6.35 but something newer than the standard Lucid kernel that behaves well with the rest of my system is my goal.

Edit: There is also -> [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
for newer generic kernels!

---

### Post by QIII on 2010-07-28
Take care to look at the "Reasons..." sections and determine if what you want to do is really worth it.

What I would recommend is this...

Either dual boot (that is, have an independent installation) or use a  virtualization solution (VirtualBox, for instance) to have a copy of  Ubuntu that you can trash to your heart's content.  That will allow you  to make horrid mistakes without ruining your "day to day" installation  while you experiment and break your system -- which you will inevitably  do.

Two key ideas here:  1.  DO BACKUPS  2. DON'T experiment on your primary OS.

In the link posted, take a look at some of the resources at the bottom.

Here is another resource that may be very helpful:

[http://kernel-handbook.alioth.debian.org/](http://kernel-handbook.alioth.debian.org/)

You might speed up your system, you might slow it down.  You might use less RAM, you might use more.  That's the sort of stuff you will find out.  But don't be subjective.  Use your "day to day" version to get some measurable benchmarks and test and record what you get after your modifications to your experimental installation.  You can certainly speed boot by removing things you can remove, but you might also render your system inoperable if you remove stuff that really needs to be there.  But that is what makes what you are talking about so worthwhile.  You can *learn*.

---

### Post by Icarus315 on 2010-07-28
> **Icarus315 said:**
> That link doesn't address Lucid directly.  I know I should fall under the "reasons to NOT compile kernel" BUT I'd like a minimal kernel that I can keep up to date myself from kernel.org.  With ONLY what I need, nothing more or less: small footprint.  Of course I probably wouldn't be able to run the absolute latest like 2.6.35 but something newer than the standard Lucid kernel that behaves well with the rest of my system is my goal.

Edit: There is also -> [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
for newer generic kernels!

I'm now running 2.6.34 generic from the kernel mainline ppa.  Everything appears to be working including the proprietary ATI driver and Virtual Box.  I think this is as close to "bleeding-edge" I should come. ;)

---

