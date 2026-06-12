---
title: "grub is not loading in fresh 9.10 install. UUID problems?"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2010-07-03
I just reinstalled 9.10 and I discovered a bug right off the bat. When I booted up for the first time, I got to the GRUB menu and selected a kernel. I was confronted with this message:
```
error: no such device : ba123456-7890-abcd-efghijklmnop
Failed to boot default entries
Press any key to continue
```
No biggie, I just deleted the line containing the UUID from the GRUB menu.

Now (up and running) I looked for a permanent fix to this bug. I found [THIS]("http://www.backports.ubuntuforums.org/showthread.php?t=1337254") thread. I followed the directions in Post #1 and edited the grub.cfg file so that a section of it looks like this:```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
set root=(hd0,1)
linux /boot/vmlinuz-2.6.31-15-generic root=UUID=ba123456-7890-abcd-efghijklmnop ro quiet splash
initrd /boot/initrd.img-2.6.31-15-generic
}
```
Normally I would have just permanently deleted the line with the UUID. However, since I decided to use the condensed version, I have run into two different problems.

1. It won't boot. It won't give me a prompt. It won't let me see the GRUB menu. All I get is an error message:```
error: you need to load the kernel first
```

2. When I booted from a CD after discovering the error, I tried to fix the grub.cfg file, but it doesn't appear to exist any longer. There is only one file in **/boot/grub** called "**grubenv**"


So, any ideas? Anyone know how I might fix this?

---

### Post by anthony62490 on 2010-07-03
bump

---

### Post by darkod on 2010-07-03
I guess that's why ubuntu says not to edit the grub.cfg directly.

Now you can't boot at all, right? If you didn't try to change grub.cfg, you would be able to boot with removing the search line from the boot lines. And then the fix was easy, but when you have your hdd ubuntu booted.
It's slightly more complicated if you can't boot at all, because you have to do it from chroot.

So, the main question now is, can you boot at all your hdd installation or not?

---

