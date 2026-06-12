---
title: "ata1: softreset failed (device not ready) - failure to boot"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JPorter on 2009-04-09
I've started having a problem after an odd hard lock during an update today, and can't get the system to boot with any combination of root delays, all_generic_ide, noacpi, etc.  Using EXT4 here, on an AMD SB700 southbridge.

The hard lockup was in the middle of a normal round of updates, it was processing something with the font cache when it stopped responding.  On boot I now get "ata1: softreset failed (device not ready)", the usplash starts to do its dance, and then the system claims that /dev/disk/by-uuid/(my uuid) does not exist (which it does) and then drops to busybox prompt.

I figured an extra root delay may help, tried up to rootdelay=130 with no change.

The weirdest part is that I'm now unable to boot from the Jaunty Beta release on LiveUSB, it does the same thing.

Was there some major regression in the ACHI or SATA drivers in yesterday's kernel updates?

---

### Post by jfernyhough on 2009-04-09
> problem after an odd hard lock during an updateThat would likely be what caused the problem. The easiest fix is to reinstall. Otherwise you'll need to chroot in to the installation and fix the broken packages (a Live CD should do the job).

Otherwise, unless you updated your USB install at the same time it's a hardware problem. Have you tried the USB booting in another machine? Does a Live CD work and detect your hardware correctly?

---

### Post by JPorter on 2009-04-09
I was trying to boot with the most recent nightly.  Maybe that's the trouble, some sort of odd kernel regression with the SATA driver.

I'll give it another shot with an older LiveCD and see what happens.  Thanks.

---

### Post by Windoze_Free on 2009-04-11
Hey guys, I'm a noob but I love the freedom that Linux offers!  Mine own eyes have beheld the light of open-source-ation.  I have  Ubuntu Hardy on my desktop and want to put Jaunty on my new Toshiba Satellite 355d.  I downloaded the iso and I used unetbooin to install it from my usb drive.  On the bootup however, I see this message:

[   2.95390] pci 0000.3:00.0 :unsupported PM cap regs version (7)
[   12.552036] ata1: softreset failed (device not ready)

modprobe:FATAL: Could not load /lib/modules/2.26.28-11-generic/modules.dep: No such file or directory

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu6) built-in shell (ash)

Can anyone please tell me what the world is going on?  It seemed to be going fine at first.  I saw the Ubuntu splash and everything.  Thanks in advance for any help.  BTW, I'm running Vista Home Premium sp1
AMD Turion x2 2.00GB   3GB RAM
32bit OS HDD 231GB 47GB free

---

### Post by jfernyhough on 2009-04-12
It sounds like the latest update didn't complete properly. When you first boot up and GRUB pops up, press ESC and choose an earlier kernel. This should get you into the system. Then you can re-run an update (or run sudo dpkg --configure -a ); this should get the newer kernel and modules installed correctly.

---

### Post by zika on 2009-04-12
I do get message like:> [some number] ata1: softreset failed (device not ready)

modprobe:FATAL: Could not load /lib/modules/2.26.28-11-generic/modules.dep: No such file or directory all the time, with 2.6.28, 2.6.29, 2.6.30, but it continues and after that everything is OK, it reads the kernel and I'm living with that (<30second boot, ...) for some time ... file mentioned in that error is OK, and on its place, that is just the first two, three lines on the screen, ... should I be worried ... ?

---

### Post by crysys on 2009-04-17
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946")

Read Daniels response.  It's crazy but it worked.  I unplug my usb stick just after the ubuntu loading screen comes up and plug it right back in.  I managed to get the stick booted and put a fresh install on the hard drive with this trick.  I still see the ata1: softreset error on startup but at least the thing boots for now.

---

