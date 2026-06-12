---
title: "[Solution] booting problem with 7.10 / I/O error on fd0 fd1 etc"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by yogeshmk on 2007-11-19
Hello all,

This is further to my earlier thread "Disappointed with 7.10" and a contribution to another thread which asked for help with 7.10 booting problem. I have found solution (rather a workaround) to the problem. Since many people are having problems booting with 7.10, I thought of startng a new thread so that the solution does not get lost inside a thread.

Problem:
---------
While booting with 7.10, you see a prompt at the very start of boot process which says
[...] /sbin/modprobe abnormal exit..
later the process freezes at around 84% saying " loading IDE-Floppy module for Linux-IDE .. " and never goes forward
or
with Alternate CD, you see erros like "I/O error on fd0" (may be fd1 for some)
[...] Unexpected interrupt..
and later you are presented with a BusyBox shell (ash) with a (initramfs) prompt..

Cause:
--------
To the best of my guess, this is a bug in the default 7.10 kernel. (specifically in modprobe?).

Solution/Workaround:
--------------------------
while booting, hit <Esc> to see the boot options presented by GRUB. You'll see something like below. (I don't know why so many kernels got built into my system.)
#####################
<snip>
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386

title		Ubuntu 7.10, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=7b475186-eed5-4a5d-9fca-a2384ee1cdc8 ro single
initrd		/boot/initrd.img-2.6.17-12-386

<snip some more lines>

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

</snip>

Now, select the third kernel from the list to boot with. Boot will go smoothly in a short time. That kernel is kernel 2.6.20-16-386. the newer version is the one that has our bug.

Making this permanent:
----------------------------
Once you boot, change to root (sudo) and edit the file /boot/grub/menu.lst and comment the 3 lines each for first two kernels with a '#' in first position. So next time when you boot, this kernel won't be considered for booting. Also *read* the file from the start, it has self explanatory info on booting. It's easy to understand.

(My guess) where this solution may not work:
------------------------------------------------------
is when your system does not have so many kernel images to choose from. In case you did a clean install, you *may* not have so many images to select (just a guess, not sure). I did  a gradual upgrade from 6.06->6.10->7.04->7.10, so probably all old kernel images were lying in my machine.
You don't have "kernel 2.6.20-16-386", you may be out of luck. (getting it from somewhere else *could* be an option, but I'm not too sure whether it'll work)

Hope this helps others and end their frustration.

--
~ yogesh

---

