---
title: "install stops on line uncompr.linux,ok,booting the kernel"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by boyan on 2006-05-13
help me please,ubuntu installs perfectly on my laptop,but on my desktop stops at the third line which says uncompressing linux ... ok, booting the kernel.
i am newbie and this despleases me much not to run on my amd 2400,asus board
may be the sth simple with the bios which i dont know???
please help

---

### Post by DarthMandeep on 2006-05-13
I had a similar problem. First thing to do is figure out if you're having the exact same problem I had.

When Grub (the thing that shows you what operating systems you have installed on your computer) starts up, select Ubuntu and hit "e".

This will allow you to edit the line. Remove the word "quiet" from it, and hit enter to boot the kernel.

You'll see a lot more messages on the screen now, telling you exactly what the kernel is doing.

If the kernel stops and says something like "waiting for root drive" or "Alert! can't find /dev/hdaX" then you've stumbled onto the same issue that made me want to cry.

The way I (think I) got around this was to boot with an older kernel that worked, and do a " sudo update-initramfs -u -k 'uname -r' "  After that the kernel booted without problems. Though I did do some other stuff, like installing mdadm, so I'm not positive what fixed it. If you don't have any other working kernels on this box, you could boot a live-cd, mount the Linux partition, and chroot into it. From there you could update the initramfs.

If you got a different error message, something that doesn't involve the root filesystem, please post it here.

Edit: You know, I've also got an AMD proc on an Asus motherboard. I guess this is a hardware + kernel hiccup?

Edit Edit: Ack, wait, the darn thing won't even install? Is that right? Oi, I don't know what to do then. :(

---

