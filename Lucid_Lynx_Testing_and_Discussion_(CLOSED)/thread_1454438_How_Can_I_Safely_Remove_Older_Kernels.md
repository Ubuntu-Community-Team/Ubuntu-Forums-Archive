---
title: "How Can I Safely Remove Older Kernels"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-04-14
How can I safely remove two older kernel versions from my system?
I have 3 kernels installed 2.6.32-19, 2.6.32-20, I would like to remove them
and stay with 2.6.32-21.

Thanks,

Jaco

---

### Post by howefield on 2010-04-14
Remove them with Synaptic Package Manager, then do a sudo update-grub

It can be useful to keep the current and second to last kernels.

---

### Post by petejk on 2010-04-14
Easiest way is using Synaptic.

Search using 2.6.32-19, then 2.6.32-20
and select the headers, headers-generic, and image packages

then either remove or complete remove.

Synaptic will remove then update your grub loader automatically

It can also be an idea to select the complete remove option on the backports-nouveau package for the kernel version you are removing as well, as this can be tricky to purge afterwards.

Pete

---

### Post by drs305 on 2010-04-14
I recommend installing Ubuntu Tweak and letting that GUI app take care of things.

There is a section of the following post called "Removing older kernels". It provides various methods of removing the kernels, including using Ubuntu Tweak and Synaptic:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by jaco223 on 2010-04-14
> **drs305 said:**
> I recommend installing Ubuntu Tweak and letting that GUI app take care of things.

There is a section of the following post called "Removing older kernels". It provides various methods of removing the kernels, including using Ubuntu Tweak and Synaptic:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Thanks for the prompt replies guys, I took drs305's advice and used tweak to remove
the kernels, as this seemed the most painless way to go about it, and it was painless.
Thanks again!

Jaco

---

### Post by VMC on 2010-04-14
If your script minded, here's one from another member that works well:

```
rmkernel () {
        local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
        local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
        local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
        sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

rmkernel

exit 0
```

---

