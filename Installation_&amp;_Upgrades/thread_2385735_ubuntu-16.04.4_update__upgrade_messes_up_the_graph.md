---
title: "ubuntu-16.04.4 update / upgrade messes up the graphics on eeepc 1005HA"
date: 2018-02-24
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2018-02-24
Hi,
  I installed ubuntu-mate 16.04.4 on my old laptop, an eeepc 1005HA (kernel  vmlinuz-4.10.0-28-generic) and everything was fine. However, after running twice "apt update followed by apt upgrade", that installed the kernel vmlinuz-4.13.0-36-generic, the screen was almost covered by a big black square on the left side. The problem must have to do with the resolution because during my repeated attempts at getting a correct install sometimes resulted in a screen resolution of only 800 x 600 instead of the normal (maximum) of 1024 x 800 with no other option available. I have installed various flavors of ubuntu over the years on this laptop without ever seeing this problem before.  Thanks for hints! D-E

---

### Post by kerry_s on 2018-02-24
if you hit esc just as it starts booting you should get into grub, then you can select the old kernel

---

### Post by dieter-erich on 2018-02-24
Hi Kerry, thanks, but this means that I never ever can run updates! I shall be bound for ever to an older version. No way to find out what is wrong in the newer versions?

---

### Post by kerry_s on 2018-02-24
that's not true, you can still update it just gets you back to a fully working system for now.

my guess is your going to have to boot with a flag of some sort, like "nomodeset" , not sure what your vid is, i'm thinking intel?

your computer is old, they might have blacklisted/dropped support for your graphics.

i'd just google around, others have got to have the same issue.

---

### Post by tinylagarto on 2018-02-24
This now was happening a lot with kernel 4.13.

If you want to use a supported kernel but older and probably functional in your case you could install kernel 4.4. I think the package name should be *linux-image-generic*.

---

### Post by mörgæs on 2018-02-27
[https://ubuntuforums.org/showthread.php?t=2376580](https://ubuntuforums.org/showthread.php?t=2376580)

---

