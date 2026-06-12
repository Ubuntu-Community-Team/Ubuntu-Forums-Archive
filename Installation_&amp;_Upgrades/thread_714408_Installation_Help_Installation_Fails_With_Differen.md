---
title: "Installation Help: Installation Fails With Different Ubuntu Versious"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Surfrock66 on 2008-03-03
I have been trying to install Ubuntu on one of my home computers and it repeatedly fails.  I have tried multiple editions, including:
Ubuntu 7.10 w/LiveCD
Kubuntu 7.10 w/LiveCD
Ubuntu 7.04 w/LiveCD
Ubuntu 7.04 Text Installer
Ubuntu 6.06 Text Installer

The specs of my system are:
MSI KT4V MB
ATI AthlonXP 1500+
768 Mb RAM
ATI Radeon Video Card
No PCI Cards

The computer would only boot so far, and in each distro it would fail at the same place with the same error message.  I used PuppyLinux 3, and that booted fine, but I want to use Ubuntu!  I tried all sorts of options I read about (acpi=off, etc) but it never worked.  Here's the output:

Call Trace:
[<c0105b70>] doIRQ+0x40/0x80
[<c0104233>] common_interrupt+0x23/0x30
[<c0101e00>] default_idle+0x0/0x60
[<c011c092>] native_safe_halt+0x2/0x10
[<c0101e3d>] default_idle+0x3d/0x60
[<c0101409>] cpu_idle+0x49/0xd0
[<c03d77f5>] start_kernel+0x365/0x420
[<c03d7230>] unknown_bootoption+0x0/0x260
=======================
Code: Bad EIP Value.
EIP: [<00000000>] 0x0 SS:ESP 0068:c03d3f64
 <0>Kernel panic - not syncing: Fatal exception in interrupt

Any help is appreciated, I have disabled everything I can in the BIOS related to IRQ, but I'm having no luck whatsoever.  The best I get is a boot to BusyBox, which then freezes and does nothing.

---

### Post by Pumalite on 2008-03-03
Have you tried to update your BIOS?

---

### Post by Surfrock66 on 2008-03-03
I am pretty sure, there was a version C on the MSI site (dated like 2004) that's the one I have, I don't know if there's an openbios alternative, this one is pretty dated, there isn't even power control on it (aka, after the OS shuts down you have to hit the power button)

---

### Post by Pumalite on 2008-03-03
Maybe you should try setting your BIOS to 'default values'

---

### Post by Surfrock66 on 2008-03-03
did it, didn't help.  Any idea if it's the kernel version, since Puppy3 worked fine?

---

### Post by Pumalite on 2008-03-03
You could give Hardy Heron Alpha5 a try if you can afford it (it's in development, a.k.a as unstable)
I have it. Works fine, but who knows.

---

### Post by Pumalite on 2008-03-03
[http://cdimage.ubuntu.com/releases/hardy/alpha-5/](http://cdimage.ubuntu.com/releases/hardy/alpha-5/)
If you decide to try it, go for the Alternate CD.

---

### Post by Surfrock66 on 2008-03-03
I will try that, though I'm not sure it'll work, I'd love to better understand what is really going wrong.

---

### Post by Surfrock66 on 2008-03-04
OK, Hardy Alpha failed as well.  Here's some other pieces of info:

The BIOS is the most current one available.

For all of the distros I've tried, there's the following behavior:
Booting a text based installer brings up the error message above.

Booting to a live CD either shows the error "Unexpected IRQ Trap at Vector 10" tons of times then shows the orange progress bar which freezes, OR boots to busybox where my ps/2 keyboard won't let me type anything.  I can't find what conditions result in one outcome or the other.

I'm at a loss, any, any ideas?

---

### Post by Pumalite on 2008-03-05
Check for hardware incompatibility at the Ubuntu site.

---

### Post by Surfrock66 on 2008-03-05
I found a few forum posts about hardware incompatibility, but nothing relating to my hardware, is there a page you're thinking of you could point me to on the main site?

---

### Post by dstew on 2008-03-05
Are you sure your disks are OK? Do they work in other machines?

---

### Post by Surfrock66 on 2008-03-05
Yes, I installed it on my new laptop with one of them, and on my fiancee's laptop with one of the other ones.  With all the different distros, I've got like 6/7 discs around!

I even put a new drive in the computer, so it's not that either.

---

### Post by dstew on 2008-03-05
It is weird that the Alternate Install CD do not work.

The only thing I can think of right now is that there is some interrupt system problem. For the Live CD, did you try the **noapic nolapic irqpoll** kernel options?

And, there are [other ways to install ]("https://help.ubuntu.com/community/Installation")besides using a CD-ROM. Network installation is one possibility. The [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") program might work for you.

---

### Post by Surfrock66 on 2008-03-05
those flags did the trick, thanks a ton brother, brings my last computer back to life!

---

