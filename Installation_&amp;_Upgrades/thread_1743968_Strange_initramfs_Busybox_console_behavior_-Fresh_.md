---
title: "Strange initramfs Busybox console behavior -Fresh Install 11.04 AMD64"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by subru77 on 2011-04-29
Hello, 

I did a fresh 11.04 install on my Dell 1501 AMD64. Installation went fine. 

But the following craziness happens every time I boot my machine. 

1) At first, on selecting Ubuntu from the Grub Menu , machine hangs with the Grub background.

2) I force shut down at this point. ( pressing the power button) 

3) Second boot does not hang, but gets to the Busybox initramfs command prompt. 

4) If I wait 5 min and then type "exit" it boots into Ubuntu and the computer functions fine until the next boot. 

I do not know how to explain this better :( 

Please help and many thanks in advance !

---

### Post by Eljay1959 on 2011-05-04
I have the same problem (but in 32 bit).
Have you noticed on the first boot attempt that GRUB has a countdown before it blanks out to its background and the 2nd attempt (which works) has no countdown? I have no idea what is causing that but it is odd.
In any case it's extremely annoying.  
I originally thought it might be a problem with having with having Windows dual boot previously set up but I have now done a completely re-partitioned disk, fresh, Ubuntu only installation and have the same result.
Anyone with any info ???  please :)

---

### Post by Linuxneophyte on 2011-05-23
I am having the same challenge on my son's HP DV9819 with dual core AMD Turion X2 and 4GB of RAM.  Ubuntu 11.04 is installed as a second OS on the system. It also, will boot if I wait just a couple minutes and type exit. Any suggestions?

---

### Post by jtmoree on 2011-06-26
Did you ever figure this out?  It seems to me that any system update that creates a new initrd image for the boot process does not work and renders the system unbootable. 

I have had to re-install many times to figure this out.  My current workaround is once the system gets screwed I boot with the backed up version of the initrd copy the original (/boot/initrd.img-2.6.38-8-generic) over the new one.  System boots fine after that.  I'm looking for bug reports but most boot issues for 11.04 are grub related.

I do have a raid partition that I'm using.  This may have to do with this bug [https://bugs.launchpad.net/ubuntu/natty/+source/mdadm/+bug/778520](https://bugs.launchpad.net/ubuntu/natty/+source/mdadm/+bug/778520)

My array is not degraded as in the bug but could still be affected.

---

