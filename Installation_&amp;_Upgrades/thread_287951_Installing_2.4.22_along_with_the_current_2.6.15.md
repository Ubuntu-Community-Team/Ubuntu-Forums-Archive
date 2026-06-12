---
title: "Installing 2.4.22 along with the current 2.6.15"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by siddharth.jain on 2006-10-29
Hi,

I am using kubuntu 6.06 (dapper).

> 
$ uname -a
Linux s0600142 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux


For a project, I need to use the 2.4.22 kernel! I want to do some tweaking in the 2.4.22 source, compile it, install it and test it.

Is it possible to use my current kernel (2.6.15) for development and compiling the 2.4.22?

I downloaded the 2.4.22 source from [http://www.kernel.org/pub/linux/kernel/v2.4/]("http://www.kernel.org/pub/linux/kernel/v2.4/") and followed the instructions given here: [http://www.howtoforge.com/howto_linux_kernel_2.4_compile_debian]("http://www.howtoforge.com/howto_linux_kernel_2.4_compile_debian")

I had some problems in compiling which I got around by using an older version of gcc (gcc-2.95) and an older version of binutils, specifically the assembler (as - GNU assembler 2.15).

However, when i try to boot into the new kernel, I get the following error:
> 
Schedule_task(): keventd has not started
kernel panic: VFS: unable to mount root fs on 03:02


I have made sure that ext3 and ext2 support is baked into the kernel (i.e. it is not <M> but <*> in menuconfig)

I have googled extensively, but nothing really worked.

My menu.lst is as follows:
> 
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.4.22
root		(hd0,1)
kernel		/boot/vmlinuz-2.4.22 root=/dev/hda2 ro quiet splash
savedefault
boot

title		Ubuntu, kernel 2.4.22 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.4.22 root=/dev/hda2 ro single
boot


If someone could help me figure out where I'm going wrong, I will really appreciate it.
If you can post a link with some instructions, that will be great as well.

I am relatively new to kernel hacking (this is my first experience). Is it possible to continue to use my current configuration without any problems, and at the same time test the tweaked 2.4.22 kernel? Will everything else work the same way in the 2.4.22 kernel (like KDE)? These might be dumb questions, but I am new to this. 

Cheers,
Sid

---

### Post by siddharth.jain on 2006-10-30
I did manage to make it work. 
But, KDE is not working. Would it be better if I use another desktop system which has fewer kernel dependencies? Could anyone suggest some other desktop environment for this?

---

### Post by niallb on 2006-11-13
> **siddharth.jain said:**
> I did manage to make it work. 
But, KDE is not working. Would it be better if I use another desktop system which has fewer kernel dependencies? Could anyone suggest some other desktop environment for this?

Hi,
glad to hear you found some progress.
I only came across this post today, but would
have recommended that you build your 2.4.x kernel
without modules so that you can leave your distributions module management tools intact.

Is that in fact what you did?
Could you attach a copy of your .config file so that we can see what options you chose.

You will need to edit your xorg.conf file I expect
to make "kde" work. The "driver" module in your
file is probably not available under 2.4.22.
Try compiling a framebuffer into your 2.4 kernel
and then seeing if you can run X with that driver.

Your problem is very unlikely to lie with KDE,
but with X itself, so changing desktop is very unlikely to change things.

Could you confirm that X fails to run completely,
or are you actually seeing X come up, but KDE failing to run.

Is it a hardware dependency that forces you
to use this kernel release? 
If so, what is it out of curiosity?
There may be alternatives.

If a 2.4 kernel is a show stopper, you might
look into using Debian Sarge which still supports
2.4, but will be similar enough to Ubuntu that most
of what you have learned will still be relevant.

Good luck. It's an interesting problem!
NiallB

---

