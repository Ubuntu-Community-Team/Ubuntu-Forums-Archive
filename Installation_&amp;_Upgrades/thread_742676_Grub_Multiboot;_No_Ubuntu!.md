---
title: "Grub Multiboot; No Ubuntu!"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by xvedejas on 2008-04-01
I just installed the latest version of Sabayon mini, and when grub loads, I get three choices; sabayon, ubuntu, and vista. Ubuntu is the only one that doesn't work. I get this error;

```
Error 13: Invalid or unsupported executable format
```

And pressing "e" when the ubuntu option is selected gives;

```
rootnoverity (hd0,2)
chainloader +1
```

What do I need to do to get this to properly work?

---

### Post by marpstar on 2008-04-01
are all three partitions on the same physical disk?

you might try changing 

```
rootnoverity (hd0,2)
``` to ```
rootnoverity (hd0,**3**)
``` or similar.  It seems like it may be referring to the wrong partition.  There's no reason why GRUB wouldn't be able to boot it.

Good luck.

---

### Post by xvedejas on 2008-04-01
Yes, I have tried that, and yes, they are all on the same physical disk.

I can still access my files fine from Ubuntu though...

---

### Post by xvedejas on 2008-04-02
Well, I probably should have been more specific; when I try to load with the 2 changed to a three, no error appears but -still- Ubuntu doesn't load.

---

### Post by xvedejas on 2008-04-02
Hmm, I think the problem is that it is unmounted; how do I mount it? There is no option to do so in GParted...

---

### Post by housam on 2008-04-02
mounting linux partitions :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/mountlinux_[/COLOR]]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by xvedejas on 2008-04-02
Okay, I have no idea where to mount it or if it matters. And mounting it to a random directory, grub still fails to load it. What do I do?

---

### Post by confused57 on 2008-04-02
> **xvedejas said:**
> Okay, I have no idea where to mount it or if it matters. And mounting it to a random directory, grub still fails to load it. What do I do?
You can use the Ubuntu live cd to install its grub to the root partition:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
```
root (hd0,2)
setup (hd0,2)
```

Grub needs to be installed to the root partition for chainloading to work.

---

### Post by dstew on 2008-04-02
Confused57 is correct. The problem is that your Ubuntu partition is not bootable. It needs a bootloader just like Windows. So, you need to install grub to the Ubuntu *partition* (not the MBR) in order to get it to boot.

---

