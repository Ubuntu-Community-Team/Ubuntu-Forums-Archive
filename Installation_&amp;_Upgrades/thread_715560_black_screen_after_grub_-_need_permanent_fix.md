---
title: "black screen after grub - need permanent fix"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by brett611 on 2008-03-05
I just installed Gutsy on my kid's laptop.  Long story short, when booting I get a black screen after the Grub countdown finishes.  I backed into a "solution" but its pretty mickey mouse.  I checked other posts with no luck, specifically [http://ubuntuforums.org/showthread.php?t=678219&page=1](http://ubuntuforums.org/showthread.php?t=678219&page=1), which was closest to my situation.

If I esc during grub and select 'recovery mode' it'll scroll a bunch of code that means nothing to me.  Eventually it stops at a command prompt.  Typing "exit" will then successfully launch Gutsy and everything works fine.

So I decided to edit grub a bit.  Heres the orig grub menu entry:
```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0ea3116-4e04-4bb1-9e7d-638b807864fb ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0ea3116-4e04-4bb1-9e7d-638b807864fb ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I changed the first section to mimic the 2nd (recovery mode) section:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0ea3116-4e04-4bb1-9e7d-638b807864fb ro single
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Now at least it'll go straight to the prompt, I type 'exit' and I'm in the money.  However, I'm at trained monkey status now.  I don't know what the changes I made really mean, why they "work" and more importantly - how to permanently fix it!

Thanks in advance!
Brett

---

### Post by PmDematagoda on 2008-03-05
Actually you did not have to mimic the entire entry of the Recovery Mode, just make the entry look like this:-
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a0ea3116-4e04-4bb1-9e7d-638b807864fb ro quiet **[COLOR="Red"]nosplash[/COLOR]**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
That will suffice, it will also mean that Ubuntu would boot up as normal except without the splash screen.

---

### Post by brett611 on 2008-03-05
Thanks - I'll give that a shot this weekend and advise

---

