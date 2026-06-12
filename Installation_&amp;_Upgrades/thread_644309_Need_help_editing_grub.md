---
title: "Need help editing grub"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by John Azelvandre on 2007-12-18
Hello.  I need to edit my grub/menu.lst so that the generic kernel boots instead of the i386 kernel.  Here is my menu.lst right now:
```

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e9561b43-f750-47a5-9d6c-4c7d4df9dfaa ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

Is it simply a matter of deleting the first two entries, or is there something more to it?  I don't to mess up my grub.  Thanks.

---

### Post by taurus on 2007-12-18
What exactly is the problem?

---

### Post by John Azelvandre on 2007-12-18
The problem is I need the generic kernel by default, not the 386 kernel.  My wireless driver (ipw2200) does not properly load on the 386 kernel.  I just tried the generic kernel, and it works great.  Who knows why.  

So, is it simply a matter of reordering the items in menu.lst?  Putting the generic first?

EDIT:  I should also set things up so that the generic kernel remains the default through future updates, at least until this weirdness with i386 and ipw2200 is resolved.

---

### Post by culmore on 2007-12-19
hmm

near the start of the file /boot/grub/menu.lst. You will see the line

default         0

just after the initial comments. The number, in this case zero corresponds to the entry that will be booted by default. So if you want a different entry rather than the first one change the number according. So lets say you wanted the third entry to be the one that is booted by default, change the line to

default         2

Hope this helps!

---

### Post by John Azelvandre on 2007-12-19
Thanks.

Would it be better -- would there be any advantage -- to rearranging the entries instead of changing the number of the default as you suggest?  Anyone have any opinions on that?

In any case, I can easily do what you've suggested.

---

### Post by Matej_C. on 2007-12-19
it's almost the same, but you loose a chance to boot i386 kernel (to be right, you can easily write it in there again)
choose what is better for you, do you want to use it again?
if no, delete it
if yes, just change default kernel number or rearrange them

there's nothing to talk about more i think :popcorn:

---

