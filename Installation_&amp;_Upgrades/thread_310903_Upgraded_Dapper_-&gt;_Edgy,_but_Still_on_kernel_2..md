---
title: "Upgraded Dapper -&gt; Edgy, but Still on kernel 2.6.12"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by Levander on 2006-12-02
I've got a box here that I've upgraded on every Ubuntu release, starting on Warty, and now I'm up to Edgy.  The Edgy upgrade hasn't gone so well. (surprise!)  Right now, the computer won't even boot and stops after a kernel panic message.  

What I'm working on right now is it doesn't seem udev is working right with my system.  One thing is that apparently I'm still on a 2.6.12 kernel.  Aren't I supposed to be on a 2.6.17 kernel with the edgy upgrade?

The only thing I remember doing strangely with the kernel package on this machine is that you used to have to install an smp kernel package to take advantage of dual processors.  I did that way back on warty.  Everything else, I've just upgraded as it came.

If the udev stuff won't work with 2.6.12, is there a way to upgrade the kernel on a machine that won't boot?  Like with the LiveCD or something?

---

### Post by pay on 2006-12-02
Boot a liveCD and chroot into your installation```
sudo su
mkdir /mnt/ubuntu
mount /dev/hda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
env-update
source /etc/profile
export PS1="(chroot) $PS1"
```

---

### Post by Levander on 2006-12-02
Okay, then what?

Just pick some 2.6.17 linux kernel package and "sudo aptitude install"?

---

### Post by pay on 2006-12-02
Yeah I guess, Try sudo apt-get dist-upgrade first and check your /boot/grub/grub.conf (nano /boot/grub/grub.conf)

---

### Post by Levander on 2006-12-02
I got the old 2.6.12 kernel to boot by modifying my /etc/fstab and grub configuration.  It was the UUID's added to them by the edgy upgrade that was preventing 2.6.12 from booting.  After booting, I "sudo aptitude install linux-generic", and (most) all is good now.  At least I can boot.  

So, I didn't have to try installing a kernel from a chroot'd environment.  Good thing, that looked risky.

---

