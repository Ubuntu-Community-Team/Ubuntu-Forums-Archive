---
title: "Update Help"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by PJOS13 on 2009-12-05
Hi!

I'm new to Ubuntu and I'm using Wubi. 5 minutes ago Ubuntu asked me for an update, something about linux... I didn't payed attention and I just click "OK", then it asked for a restart and I restarted the computer, but when I tried to boot Ubuntu I got a black screen saying that I have to press tab for help to view the valid commands, but I don't know what to do. So, what should I do to get my Ubuntu running again? What command should I use?

---

### Post by PJOS13 on 2009-12-05
I have more information, the screen says:

[I]"
[CENTER]GNU GRUB Version 1.97 beta4[/CENTER]

[Minimal BASH- like line editing is supported. For the first word. TAB list possible command completions. Anywhere else TAB list possible device/ file completions] 

sh.grub>
"[/I]
So, how I get Ubuntu running again.

PD: Sorry, my English is  terrible...

---

### Post by Saudiboy666 on 2009-12-05
i just had the same problem too :(
after the update ubuntu wont start anymore

---

### Post by u.b.u.n.t.u on 2009-12-05
At boot where you can start Ubuntu 9.10, try selecting the previous kernel version. The one before the update today.

---

### Post by PJOS13 on 2009-12-05
> **u.b.u.n.t.u said:**
> At boot where you can start Ubuntu 9.10, try selecting the previous kernel version. The one before the update today.

It doesn't let me choose between the kernels. When I boot Ubuntu it just show me that screen...

---

### Post by u.b.u.n.t.u on 2009-12-05
> **PJOS13 said:**
> It doesn't let me choose between the kernels. When I boot Ubuntu it just show me that screen...

What version of Ubuntu have you got installed?

What are your computer specs?

May I ask what your first language is?


UPDATE

The issue may relate to grub.cfg found at /boot/grub/grub.cfg

Here is a post giving general information about grub.cfg, look at point 5.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This page gives more information, and has the same example as you have given
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)


The question may be one of how to repair grub.cfg

---

### Post by deadite66 on 2009-12-05
same here update just broke wubi.

---

### Post by daonaob on 2009-12-05
The same happened to me today. Won't display GRUB menu, just the command line.
Anyone have any ideas what caused it?

---

### Post by darkod on 2009-12-05
From other thread here in the past few days, the kernel update from 31-14 to 31-15 seems to be causing this. Can't be 100% sure, just what I noticed. And this only happens in wubi, not the side-by-side dual boot install.
It seems something in the kernel update does not function correctly in wubi. But the update is offered just like in the other install types. I have done that update on both my desktop and netbook, working fine, but they are side-by-side installs not wubi inside windows. I prefer not to use linux inside windows.

---

### Post by u.b.u.n.t.u on 2009-12-05
The 2.6.31-16-generic kernel update works my wubi Ubuntu 9.10 virtual inside Windows 7.

There was a minor glitch, I had to reduce the bit color from 24 to 16 at boot. Prior to that kernel panic and blank screen.

---

### Post by PJOS13 on 2009-12-05
> **u.b.u.n.t.u said:**
> What version of Ubuntu have you got installed?

What are your computer specs?

May I ask what your first language is?


UPDATE

The issue may relate to grub.cfg found at /boot/grub/grub.cfg

Here is a post giving general information about grub.cfg, look at point 5.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This page gives more information, and has the same example as you have given
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)


The question may be one of how to repair grub.cfg

I have Ubuntu 9.10, I have a Dell Vostro 1510, and my first language is Spanish...

I tried with the answers of the links, but it didn't work, the question is, how can I return to grub menu mode?

edit: when I try to boot something, I get "error  no loaded kernel".

---

### Post by deadite66 on 2009-12-05
i had more luck following the replies in the launchpad bug report of this problem.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic 
boot
```

2.6.31-16-generic panic'ed so used 2.6.31-15-generic
once ubuntu started up normaly i removed all 2.6.31-16 packages in synaptic and all is well again.

---

### Post by u.b.u.n.t.u on 2009-12-05
Unfortunately I simply don't know. I have looked into the problem and it appears to me that the grub configuration file was essentially corrupted by the update. I can only speculate how such could have happened, eg being overwritten, but I just don't know for sure. I am speculating.

If taking the premise that the problem lies with grub.cfg then I would look at repairing that. The primary function of grub is to act as a boot loader.

As a suggestion, possibly open grub.cfg and ensure it is valid, accessing such by way of a live CD for example.

My wubi virtual install of Ubuntu 9.10 is completely up to date and this error did not occur.

So as a starting point:

1. live CD boot into Ubuntu 9.10
2. go to /boot/grub/grub.cfg
3. check to see if grub.cfg is correct

As we have no other possible leads to follow at this time, maybe this would be a good start?

---

### Post by u.b.u.n.t.u on 2009-12-05
> **deadite66 said:**
> 
2.6.31-16-generic panic'ed

Same experience here. My boot settings were in 24 bit color and reducing that to 16 bit color enabled 2.6.31-16-generic to work.

---

### Post by PJOS13 on 2009-12-05
> **deadite66 said:**
> i had more luck following the replies in the launchpad bug report of this problem.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic 
boot
```

2.6.31-16-generic panic'ed so used 2.6.31-15-generic
once ubuntu started up normaly i removed all 2.6.31-16 packages in synaptic and all is well again.

Hey! thank you! It worked!

but I still have a problem, I have to do that every time I want to boot Ubuntu... So, how I recover my old menu?

---

### Post by deadite66 on 2009-12-06
try 'sudo update-grub2' it was one of the things i tried before removing the new 2.6.31-16 kernel packages.

---

