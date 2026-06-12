---
title: "Grub prompt after installing Windows 7"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by u-slayer on 2011-01-06
So I just installed windows 7 to my comp and then tried of fix grub by booting from a live cd and running

grub-install --root-directory=/mnt /dev/sda

That command worked, but I was worried when I saw that I had no menu.lst or grub.cfg file in my /boot/grub.

Now I can't get past the grub prompt.

Here are my partitions

sda1  /boot
sda2  /
sda3  windows xp
sda4  windows 7

What do I type into this grub prompt?

---

### Post by wilee-nilee on 2011-01-06
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by drs305 on 2011-01-06
> **u-slayer said:**
> So I just installed windows 7 to my comp and then tried of fix grub by booting from a live cd and running

grub-install --root-directory=/mnt /dev/sda

That command worked, but I was worried when I saw that I had no menu.lst or grub.cfg file in my /boot/grub.

Now I can't get past the grub prompt.

Here are my partitions

sda1  /boot
sda2  /
sda3  windows xp
sda4  windows 7

What do I type into this grub prompt?

Did you mount both your /boot and / partitions first:
```

sudo mount /dev/sda2 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

If this doesn't fix it, please run the boot info script and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by u-slayer on 2011-01-06
thansk drs305, that fixed it.

---

### Post by bandoba on 2011-04-01
Thanks drs305. Your reply helped me too. In my case / and /boot was on the same partition. For that type of configuration, the the point to remember is root-directory parameter for grub-install should point to the mounted / and not to /boot/grub folder on mounted partition. HTH.

---

