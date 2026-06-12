---
title: "Making grub changes permanent"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by DeanoCYM on 2013-01-26
Hello all,

I just re-installed ubuntu 12.04lts on my desktop and have some problems booting up. 

My PC boots into grub rescue because it can not find my root partition; I have to type the following every time to get it to work:
```

  set prefix=(hd1,msdos1)/boot/grub
  set root=(hd1,msdos1)
  insmod normal
  normal

```
Any ideas how to make these changes permanent? I think the root cause is something to do with an incorrectly set UUID of the drive with the root partition, but I am a bit out of my depth and have been stuck now for about a week.

All software is up to date with the default Precise repos. 

Any help is much appreciated,

Rhys

---

### Post by sudodus on 2013-01-26
You find lots of information about grub here
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

Have you tried the automatic way, to run
```
sudo update-grub
```
and reboot?

The settings you need can be fixed by entering them in the file

```
/etc/grub.d/40_custom
```
or should I say, copy the relevant part of 
```
/boot/grub/grub.cfg
```
when it works, and enter it into
```
/etc/grub.d/40_custom
```

This should be a piece of text like this
```
menuentry "Ubuntu ..."{
...
...
}
```

and run
```
sudo update-grub
```
to make it active (to move it into /boot/grub/grub.cfg)

---

### Post by DeanoCYM on 2013-01-26
Thanks for the info, I'll try this when I get home.

---

