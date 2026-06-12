---
title: "Custom kernel - kernel panic"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by jswhite on 2010-05-08
I tried compiling up my own kernel, but it doesn't seem to be working out for me. Post compile, I end up with 2 .deb packages (the image and the headers), install both, and reboot. When I reboot, I get the following error message:

> [  1.120815] Kernel panic - not syncing: VFS: Unable to mount root root fs on unknown-block(0,0)..

I've tried compiling using [KernelCheck]("http://kcheck.sourceforge.net/"), following the instructions in the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158"), and following the instructions [here]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild"). Regardless of the route I take, I still end up with that exact same error message. I always have to go back to GRUB and boot up with my old kernel, then uninstall and try again.

Any help here?

---

### Post by BT1 on 2010-05-09
I am getting the exact same thing. I tried compiling on Lubuntu and Xubuntu and that dang kernel panic issue is stopping me from having the kind of optimization that I had on 9.10. Please help us someone!

---

### Post by master_kernel on 2010-05-09
The new version of initramfs-tools does not automatically link the needed scripts anymore.

Do the following to fix it:
```
cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/
```

Then **reinstall** the .deb files.

---

### Post by BT1 on 2010-05-09
> **master_kernel said:**
> The new version of initramfs-tools does not automatically link the needed scripts anymore.

Do the following to fix it:
```
cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/
```Then **reinstall** the .deb files.

"Do it"? What do I do with it? I'm just a novice. :P I tried to run it in terminal but all I got was messages saying "missing destination file operand after" etc.

Thanks for your help so far.

---

### Post by BT1 on 2010-05-09
What I am doing is...

1.) Fresh install of Ubuntu
2.) Download updates, hardware video driver
3.) Download Kernelcheck 1.2.5-4 all.deb
4.) Install
5.) Run the program, "find" the newest kernel
6.) Apply settings
7.) save, quit
8.) Kernel compiles
9.) I restart and try to boot into the newest item on my list, the candela and I get the OP's error.

Where does your code fit in to that process?

---

### Post by ibuclaw on 2010-05-09
If in doubt, use the [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") for tips/guidance.

Regards
Iain

---

### Post by jswhite on 2010-05-09
> **master_kernel said:**
> The new version of initramfs-tools does not automatically link the needed scripts anymore.

Do the following to fix it:
```
cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/
```

Then **reinstall** the .deb files.

1. Both of those should start with "sudo".
2. The first one copied fine. For the second one, I apparently did not have a "postrm.d" directory in /etc/kernel/. So, I made one and copied the initramfs file into it, then reinstalled.

The headers reinstalled without a hitch. When reinstalling the kernel package, I got this:

> Setting up linux-image-2.6.33.3.mordor (2.6.33.3-mordor-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs 2.6.33.3-mordor /boot/vmlinuz-2.6.33.3-mordor
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.333.3-mordor /boot/vmlinuz-2.6.33.3-mordor
run-parts /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.33.3-mordor.postinst line 341.
dpkg: error processing linux-image-2.6.33.3-mordor (--install):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
linux-image-2.6.33.3-mordor

On a whim, I decided to go ahead and reboot since gdebi was showing the status of the package as "installed". To my surprise (given the errors), it rebooted just fine, and according to "uname -r" I'm using the new kernel.

So I'm guessing that error isn't too bad?

---

