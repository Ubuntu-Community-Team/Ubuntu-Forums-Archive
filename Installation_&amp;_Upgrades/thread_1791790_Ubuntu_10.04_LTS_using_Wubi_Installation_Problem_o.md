---
title: "Ubuntu 10.04 LTS using Wubi Installation Problem on IBM Thinkpad R50e"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by matthewhalos on 2011-06-27
There is an installation problem when installing Ubuntu 10.04 LTS using Wubi on my IBM Thinkpad R50e.

My operating system is Windows XP Professional.

After Wubi installed the Ubuntu Installation Files on my hard drive, I restarted my computer.

After restarting, I selected Ubuntu on the selection of operating systems.

First, I saw the introductory logo of Ubuntu (when the ubuntu loads its files).

After that, instead I will saw the installation progress or the installation of language packs, only Black Screen will appear on my Laptop screen.

I have waited for an hour, but nothing happens. It did not pushed through with the installation.

Anyone who has the solution to this problem?

Thanks!

---

### Post by sanderd17 on 2011-06-27
Do you have the iso?

Can you boot from a live CD and see if you have a black screen there too? No need to install it.

---

### Post by bcbc on 2011-06-27
Try the following boot workaround:
i915.modeset=1

See [How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132") for how to do this.

Here're some other links:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[http://ubuntuforums.org/showthread.php?t=1484820](http://ubuntuforums.org/showthread.php?t=1484820)

---

