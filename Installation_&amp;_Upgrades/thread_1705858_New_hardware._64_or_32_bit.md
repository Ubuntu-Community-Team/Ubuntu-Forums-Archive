---
title: "New hardware. 64 or 32 bit ?"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by Dr.Paneas on 2011-03-12
Hello guys,

I've just installed Ubuntu 10.10 32 -bit on my machine. My hardware is Intel Core i5 2500K, ASUS ITX motherboard, 2x2GB DDR3 Corsair So-dimms and Vertex 3 SSD on SATA 3. I use the integrated graphics of Intel.

Do you think I should remove my 32bit installation and then apply a new 64bit one ?
or even with 32-bit it's ok ?

---

### Post by Dutch70 on 2011-03-12
> **Dr.Paneas said:**
> Hello guys,

I've just installed Ubuntu 10.10 32 -bit on my machine. My hardware is Intel Core i5 2500K, ASUS ITX motherboard, 2x2GB DDR3 Corsair So-dimms and Vertex 3 SSD on SATA 3. I use the integrated graphics of Intel.

Do you think I should remove my 32bit installation and then apply a new 64bit one ?
or even with 32-bit it's ok ?

Welcome to UF Dr. Paneas,

Yes if you have a processor that compatible with 64 bit OS's use it, but the 32 bit is fine if you want to stick with it.

---

### Post by uRock on 2011-03-12
I'd go with 64bit. It is faster.:D

---

### Post by uRock on 2011-03-12
Hello and welcome to the forums,

I'd go with 64bit. It is faster.:D

Cheers,
uRock

---

### Post by Hedgehog1 on 2011-03-13
Dr.Paneas,

If you have not yet begun to customize your Ubuntu install too much, installing the 64bit to use all your ram (right now you can use about 3.6 gig of the 4 gig) might be an educational experience for you.

If your computer is only running Ubuntu, you can do a clean install or the 63bit and wipe the disk, no help from is needed.

If you are dual-booting, we can still walk you through reinstalling 64bit without hurting anything (but we need to take a moment to help you plan it, you will have to do a manual install for that).

If you want to install the 64bit, and are dual booting, please do this while running in Ubuntu:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

p.s. If you are happy with what you have, don't sweat it and enjoy Ubuntu.

---

### Post by Dr.Paneas on 2011-03-13
Thanks for the warm greetings guys,

I would prefer to use 100% all of my RAM, instead of using on part of my memory and not all of it. So, I will go with the 64bit.

Maybe a secure ssd  erase with *gparted* or* hddparm* is a better choice. In the past I have seen a kind of performance degradation using the traditional f-disk way.

Here is the link from G.Skill forums which I am going to follow its instructions : [http://gskill.us/forum/showthread.php?t=5901](http://gskill.us/forum/showthread.php?t=5901)

Hopefully my next forum post will be 64-bit :popcorn:

---

### Post by Dr.Paneas on 2011-03-13
Hehe great, I am on 64bit Ubuntu now

However, I have to say that I was faced a little trouble with secure erase. The problem is that disk was frozen.

```

Security: 
        supported
    not    enabled
    not    locked
        [COLOR=Green]frozen[/COLOR]
    not    expired: security count
    not    supported: enhanced erase

```

I tried to unplug/plug the SATA cable that this didn't work out. So eventually, I removed the power connector from the SSD and the plugged it back. Magic:

```

Security: 
        supported
    not    enabled
    not    locked
    [COLOR=Green]not    frozen[/COLOR]
    not    expired: security count
    not    supported: enhanced erase

```

Then just typed the  appropriate command and disk is erased successfully :)
```
 
ubuntu@ubuntu:~$ sudo hdparm --security-erase NULL /dev/sdb
security_password=""

/dev/sdb:
 Issuing SECURITY_ERASE command, password="", user=master

```

Thanks,
Dr.Paneas

---

### Post by Dutch70 on 2011-03-13
Nice work! Don't you feel better already?!?

---

### Post by Dr.Paneas on 2011-03-13
> **Dutch70 said:**
> Nice work! Don't you feel better already?!?

I can't fell the difference, but benchmarks do ;)
btw I've updated the kernel to 2.6.38 prepatched and installed all the new xf86-video-intel, libdrm, mesa-dev and xserver to the latest of ppa-xorg-edgers. Before doing that I was completely unable to play any game...lot's of artifacts on the screen with "zero floating point performance" since I got 0.72 fps on lightsmark :p Hehe, now it's ok :)

Cheers and thanks :)

---

### Post by Hedgehog1 on 2011-03-14
Dr.Paneas,

You, sir, are a 'keeper'.

I look forward to your future postings...

***The Hedge***

:KS

p.s. I am trying not the be ***too*** jealous of your hardware... :D

---

