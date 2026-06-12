---
title: "Multiple Kernels"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by LeNath on 2006-12-06
Hi,

I have just reinstalled Ubuntu Dapper on my laptop, and immediately proceeded with necessary updates (Synaptic came up suggesting available updates).

Something that never happened to me before is now occuring:

When GRUB is loaded, it shows up 2 versions of Ubuntu, with 2 different kernels.

```
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot
```

Here are my questions:

. Why is this now happening?
. Can I get rid of the outdated kernel? If yes, any preferred method?
. Is it wise to do so?
. What are the consequences of leaving it as is?

Thx a bunch for your answers!

Nathan.

---

### Post by Zelut on 2006-12-06
Let me see if I can just break down your questions simply..

1) kernels are updated fairly regular for security updates and added hardware support.  It is (generally) the best idea to use the latest kernel release and in this situation I would suggest it.

2) You can get rid of the outdated kernel but you may not want to just yet.  I generally leave at least one previous kernel installed just in case I do run into some trouble in the future I can easily revert to the previous kernel via the GRUB menu.

3) If you do want to remove the kernel you can simply search for that kernel version in Synaptic Package Manager and select it for removal.

4) The consequences of leaving it as is?  ...not much.  You've got one kernel taking up a few megs of hard drive space, but thats about all.  I wouldn't worry about it.  I've had a system with current & 10 previous kernels still installed before I cleaned it up and it didn't affect a thing other than a longer GRUB menu.

Hope it helps and thanks for sending me the question.  I will write up a tutorial for this on the blog this week!

---

### Post by LeNath on 2006-12-07
Thx a lot for the reply!
Keep up the good work on the blog!

---

