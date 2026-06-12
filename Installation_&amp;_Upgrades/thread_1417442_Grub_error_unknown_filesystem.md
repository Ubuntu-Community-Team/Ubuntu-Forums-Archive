---
title: "Grub error unknown filesystem"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by palz2015 on 2010-02-27
I just installed ubuntu 9.10 on my 8 gb flash drive using the startup disk creator. I did some partitioning using this live drive and when I rebooted, I get this:

GRUB loading. 
error: unknown filesystem
grub_rescue>

I know absolutely no grub rescue commands. I try fsck, sudo, logout, et cetera. I had an issue like this before, and I had to reinstall ubuntu to the local drive. Can you help??

---

### Post by darkod on 2010-02-27
Did you delete the ubuntu partition maybe? In that case grub will not be able to find its config files and will report an error. Did you have ubuntu installed on the hdd at all?

You can also try running the boot info script for more details. You can run it from the live desktop which you can boot with the usb stick. Instructions to run it are here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

