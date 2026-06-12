---
title: "Power outage during Gutsy upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Bandit09 on 2007-10-19
Hey all. I seem to have very bad luck. I was in the process of upgrading kubuntu 7.04 to kubuntu 7.10, and it was at 64% installing the updates, and then I had a power outage. Upon turning my machine back on, it won't work. It gives some PCI errors and then says cannot mount root fs.

It says:

24.533979 Kernel panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)

Is there anyway i can resume the updgrade or restore my machine? I really don't want to lose everything on my machine, as I've got many important things on there.

Any help would be much appreciated.

Thank you!

---

### Post by tgalati4 on 2007-10-19
Boot a Live CD (preferabley Dapper or Feisty) and try to mount your partition and locate your data.  If you find your /home directory, now would be a good time to start burning CD's or buying some new flash drives for data transfer.

---

### Post by Bandit09 on 2007-10-19
Thanks for your reply!

Unfortunately I'm a linux noobie. I do have a feisty live CD....could you please explain to me in a little greater detail on what I need to do?

---

### Post by Bandit09 on 2007-10-20
bump - can anyone please help me out?

I'd greatly appreciate it.

Thanks!

---

### Post by heldal on 2007-10-21
The new kernel probably won't boot because it doesn't have a proper ramdisk-image with drivers for your hardware. If the upgrade was aborted your system should still have the old kernel installed. Try to boot that into recovery-mode as X probably won't work at this point.

Then rebuild the boot ramdisk (initrd) for all installed kernels with the command "update-initramfs -c -k all". The you should be able to boot the new kernel if only the appropriate driver-packages were installed before the powerfailure.

If you now can boot the new kernel in recovery-mode with working network try

```
dpkg --configure -a
apt-get update
apt-get upgrade
```

There may still be a few packages missing, but you should be able to get those using the instructions in [http://ubuntuforums.org/showthread.php?p=3588158#post3588158](http://ubuntuforums.org/showthread.php?p=3588158#post3588158)

---

### Post by Rockman4140 on 2007-10-26
I've had a similar issue. It was installing packages when my laptop battery cut off. (I had it plugged in but it wasn't charging) I attempted to repair a broken system with the Gutsy disk, which didn't work for me. GRUB reports my old kernel as 7.10, so I figured I'd install Gutsy through Alternate Install. 

My question is what would be some good steps to merge my old Feisty Install with my Gutsy install. Is there some sort of way to export a list of downloaded packages that I could use to re-download? I moved my Home folder over, and I never noticed how many folders are in there, but what are some other steps I could take?

---

