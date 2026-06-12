---
title: "Changing from Fedora Core to Ubuntu"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by spahn on 2006-07-13
I have been using Ubuntu for a while and i think it is great.

i just got a new job and there is a co-worker who uses Fedora core 5, and is really good at it, so the company bought me a computer and i installed Fedora Core 5 on it, but i do not like it!

The problem is this: i have not been able to install Ubuntu over it! The Live CD fails and even Knoppix can't find the file system!
Seems like it can't read the file structure.

Any ideas on how i can erase Fedora and do a fresh install of Dapper Drake?

I am at a real loss...

---

### Post by encompass on 2006-07-13
The live cd should work... try the failsafe install setting... or you may be able to do a text based install too.

---

### Post by lordlollo on 2006-07-13
I have recently passed from Fedora to Ubuntu, and I did use the alternate cd (but for raid issues). I'm confident that the live cd should work. Anyway, give a go to the alternate one, if you are still in trouble.

Cheers.

---

### Post by tseliot on 2006-07-13
> **spahn said:**
> I have been using Ubuntu for a while and i think it is great.

i just got a new job and there is a co-worker who uses Fedora core 5, and is really good at it, so the company bought me a computer and i installed Fedora Core 5 on it, but i do not like it!

The problem is this: i have not been able to install Ubuntu over it! The Live CD fails and even Knoppix can't find the file system!
Seems like it can't read the file structure.

Any ideas on how i can erase Fedora and do a fresh install of Dapper Drake?

I am at a real loss...

Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

