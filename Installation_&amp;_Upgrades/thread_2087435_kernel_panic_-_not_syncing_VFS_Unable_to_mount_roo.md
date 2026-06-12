---
title: "kernel panic - not syncing: VFS: Unable to mount root fs -After each Kernal upgrade"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by sdd on 2012-11-23
Hi

I am a longtime fan of Ubuntu but I prefer Gnome so I installed 64bit 12:10 and Gnome. I have also installed the Nvidia binaries (304.43)

I have to say that 12.10 is not as stable or as fast as 12.04 which I have in another partition (thank god). I also get frequent dialogues popping up reporting a system error which I always let report 'to help Ubuntu be better', I fear it is not working!

What is now happening is that after an update where a new Linux Kernal is installed (latest is 3.5.0-18-generic) the PC will not boot. I get a Kernel panic.

[B]Kernel Panic - not syncing VFS: unable to mount root fs on unknown-block (8,1)
PID:1, commL swapper NOT tainted[/B]

I googled and found the answer so I was able to recover. See article here:

[http://askubuntu.com/questions/116635/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-oo-swapper]("http://askubuntu.com/questions/116635/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-oo-swapper")

However what I would like to know is why this happens. Is there a cure. It is VERY frustrating. Yes I can repair it but could I stop it happening.

My understanding is that initramfs is not built correctly during the upgrade of the kernel however it does NOT report this at the time. I then have to boot to 12.04 and plod through the script.

I know we like to make fun of other operating systems but this type of critical issue is unlikely to impress others and bring them over to the 'light side'. 

Regards

Stuart

---

### Post by sdd on 2012-11-26
Could someone please help? 

Should I move this to another thread group or forum?

Stuart

---

### Post by searchfgold6789 on 2012-11-26
I would recommend trying a different kernel, say [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc7-raring/) , but the kernel website is down.

---

### Post by hetmes on 2013-06-23
I was struggling with this today. If I recall correctly, what seemed to happen was this.

- I update the kernel. This breaks the nvidia drivers (mismatched kernel model and client version error message in kern.log)
- reinstalling nvidia drivers seems to succeed but fails to compile the kernel module because the kernel source is not installed. This breaks the kernel in the way mentioned. (VFS, unable to mount etc.)

So, the solution is to apt-get purge nividia*, install the kernel sources, reinstall nvidia.

---

