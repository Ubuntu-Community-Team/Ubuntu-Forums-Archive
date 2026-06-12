---
title: "Can't start other distros properly"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by duffmckagan on 2005-06-28
I installed the following distros in the following order.

WindowsXP , CEnt OS, Slackware, ubuntu.

Ubuntu detected all of them fine.

But now the problem is , when I boot to Cent OS, it gives me error saying cannot perform <required tasks> due to Read - Only file system.

Whats wrong?

This started happening only after installing Ubuntu Hoary.

---

### Post by Xian on 2005-06-28
In your /boot/grub/menu.lst append the 'ro' parameter to the kernel line of the entry for CentOS. For example, you would want it to look similar to this:
```
kernel	/boot/vmlinuz root=/dev/hda2 ro quiet
```

---

### Post by duffmckagan on 2005-06-28
[QUOTE=Xian]In your /boot/grub/menu.lst append the 'ro' parameter to the kernel line of the entry for CentOS. For example, you would want it to look similar to this:
```
kernel	/boot/vmlinuz root=/dev/hda2 ro quiet
```[/QUOTE]
 Thanks for the reply.
But that ro thing was already there. That was the thing that I actually had suspected.
But still the same thing is still happening.

Frustrated, I formatted everything, after backing everything, and simply installed just Ubuntu.
Thats what I liked the most. Installed Slackware seperately on another comp. I don't want Slackware to interfere with others.

Again, thanks for the reply.

---

