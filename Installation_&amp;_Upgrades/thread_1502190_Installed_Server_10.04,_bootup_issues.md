---
title: "Installed Server 10.04, bootup issues"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by cocco_fi on 2010-06-05
Installed 10.04 from USB stick to a prepartitioned disk as follows:

Volume - mountpoint
/dev/sda1 - /boot
/dev/sda2 LVM VG System:
/dev/System/root - /root
/dev/System/swap - swap

During the installation I set up GRUB2 in the MBR of /dev/sda.

Upon first boot after installation I'm welcomed with GRUB error 15 and some comment about not finding stage 1.5. Ok this disk used to host 9.10 on it with Grub Legacy in the MBR, maybe the install didn't manage to overwrite it? All partitions mentioned above were formatted during install but the whole disk wasn't (other LVM volumes with data in VG System).

I've been trying the 10.04 desktop install and latest sysresccd, and I've reinstalled GRUB2 on /dev/sda, now I'm at least getting the GRUB2 when booting up but no menu, just the GRUB> prompt. From the prompt I can see the contents of /boot and everything seems to be in order, but loading the kernel from the grub prompt ends up with a kernel panic, no matter how I point to the root fs (I've tried root=/dev/System/root, root=/dev/mapper/System-root and root=UUID=...) I always end up with the following:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```So basically my situation looks a lot like this: [http://ubuntuforums.org/showthread.php?t=1170612](http://ubuntuforums.org/showthread.php?t=1170612).

Any pointers what to try next? I dled SuperGrubDisk but for some reason that won't boot from USB, I just get unetbootin looping (the server doesn't have a cd drive). For some reason also the 10.04 desktop livecd will not install lvm2, I just get some error when it tries to install watershed(?). I'm assuming my problem stems from my initrd not ecognizing the root volume on LVM, but I frankly have no idea how to fix it. This is also my first contact with grub2, how can I make it use a specific initrd? :confused:

---

