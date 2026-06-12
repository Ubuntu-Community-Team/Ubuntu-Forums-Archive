---
title: "Unused Kernel Not Listed in Synaptic"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-12-16
I took kernel 3.1.5 directly from kernel.org and tried to configure and compile it myself.  I did something wrong because it wouldn't boot up completely.  I went to remove it like usual with Ubuntu Tweak, but it wasn't there.  I also tried finding it directly in Synaptic, but it wasn't there either.  I know it's still on my system, but I don't know of any other ways to remove it.

Does anyone have any ideas?  Should I just delete the "linux-3.1.5" folder in /usr/src, the "3.1.5" folder in /lib/modules, and then go to /boot and delete the files "System.map-3.1.5", "config-3.1.5", "vmlinuz-3.1.5", and "initrd.img-3.1.5"?  (Then run "sudo update-grub", of course)  Or is there more to it than that?

I followed this guide to install the kernel:
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html")

---

### Post by GreenRaccoon on 2011-12-16
I just found this thread: [http://ubuntuforums.org/showthread.php?t=1601630&page=2]("http://ubuntuforums.org/showthread.php?t=1601630&page=2").  This thread seems to list the files that I need to delete manually, so I updated the list in my first comment.  I am always very wary of doing things manually, so I would appreciate it if someone who knows what they're doing could confirm this list.

---

### Post by GreenRaccoon on 2011-12-30
> **GreenRaccoon said:**
> I took kernel 3.1.5 directly from kernel.org and tried to configure and compile it myself.  I did something wrong because it wouldn't boot up completely.  I went to remove it like usual with Ubuntu Tweak, but it wasn't there.  I also tried finding it directly in Synaptic, but it wasn't there either.  I know it's still on my system, but I don't know of any other ways to remove it.

Does anyone have any ideas?  Should I just delete the "linux-3.1.5" folder in /usr/src, the "3.1.5" folder in /lib/modules, and then go to /boot and delete the files "System.map-3.1.5", "config-3.1.5", "vmlinuz-3.1.5", and "initrd.img-3.1.5"?  (Then run "sudo update-grub", of course)  Or is there more to it than that?

I followed this guide to install the kernel:
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html")

Bump.

Could I have someone double check that this is correct? To remove the 3.1.5 kernel, I was thinking of doing this:
1) In /usr/src, remove the "linux-3.1.5" folder.
2) In /lib/modules, remove the "3.1.5" folder.
3) In /boot, remove the files "System.map-3.1.5", "config-3.1.5", "vmlinuz-3.1.5", and "initrd.img-3.1.5".
4) In /var/lib/dpkg/info, remove the files "linux-headers-3.1.5-030105.list", "linux-headers-3.1.5-030105.md5sums", "linux-headers-3.1.5-030105-generic.list", "linux-headers-3.1.5-030105-generic.md5sums", and "linux-headers-3.1.5-030105-generic.postinst" (all of the "linux-image..." ones are missing).
5) In /usr/share/doc, remove the folders "linux-headers-3.1.5-030105" and "linux-headers-3.1.5-030105-generic" (the "linux-image..." ones are missing here too).
6) Run "sudo update-grub".

It'd be great if someone who knows Linux better than I do could confirm/modify these steps.

---

