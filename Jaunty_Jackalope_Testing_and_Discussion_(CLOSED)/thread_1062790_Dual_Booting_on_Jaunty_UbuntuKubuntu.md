---
title: "Dual Booting on Jaunty: Ubuntu/Kubuntu"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2009-02-07
Hey:

Now that we are at Alpha 4, I am looking to test both Ubuntu and Kubuntu considering the worst of the bugs for my specific laptop has been solved (graphics).  I have done this for Intrepid yet my main beef with it was that when the kernel got an update on both systems, one of them wouldn't get properly updated on Grub (the one I installed first) and I would have to do it manually every time.

Is there a way to have both version update automatically the Grub when kernel upgrades even if the Grub is installed on only one of the partition?

(I know I can get this info on General, but since I am testing Jaunty and I usually dwell in this area of forums I decided to post here)

Thanks in advance.

---

### Post by jfernyhough on 2009-02-07
Chainloading is your friend.

IIRC, something like
```
title Alternative linux boot
root (hd0,1)
chainloader +1

```in /boot/grub/menu.lst

So say Ubuntu is installed on sda1 (hd0,0) and Kubuntu on sda2 (hd0,1). During installation you specify Kubuntu to install its bootloader onto sda2 (not mbr) and Ubuntu has its loader on the mbr. Now Ubuntu will update the mbr loader, and when asked will chainload the loader on sda2. Kubuntu will update and take care of the loader on sda2. In this example, the above grub menu code would live in the Ubuntu config (so in the mbr).

No mess, no fuss. :)

You can tell grub to install a loader in a different place after installation. Using the above examples:

```
$ sudo grub
> root (hd0,1)
> setup (hd0,1)
> root (hd0,0)
> setup (hd0)
> quit

```

---

### Post by PRGUY85 on 2009-02-07
Thanks!  I'll try this now.  I have Kubuntu installed completely on my laptop HDD.  I will now install Ubuntu Jaunty Alpha 4 with your tips and see how it goes.

---

### Post by vishalrao on 2009-02-08
i've actually installed the "kubuntu-desktop" package on my ubuntu installation and made kdm the default. now i can log in to either gnome or kde in the same installation/boot. but i guess you need to have them separate to avoid any other issues...

---

