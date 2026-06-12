---
title: "Kernel 2.6.31-10 broke my system on boot"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shakaran on 2009-09-09
Hi, I have a friend laptop with Karmic and ATI Radeon HD 2600. When I did:
sudo apt-get dist-upgrade 

And then reboot, his system dont init. If I choose kernels like 31-8 or 31-6 or 31-6 (he only have these) dont init!

I am worry. His system only show a black screen with a dash on top. I cant write anything. With recovery mode, I get the console, but if I write:
sudo /etc/init.d/gdm start
The gdm dont start yet.

How to solve this? Some tricky command for run gmd? some log for find errors and fix it?

Thanks, all help is appreciated!

---

### Post by dino99 on 2009-09-09
you can test the graphic hypothesis : change driver to default

search errors with dmesg
look at log in /var/log

---

### Post by shakaran on 2009-09-09
> **dino99 said:**
> you can test the graphic hypothesys : change driver to default
Could you give more information to change? Maybe xorg.conf change driver to vesa? or other?

---

### Post by dino99 on 2009-09-09
> **shakaran said:**
> Could you give more information to change? Maybe xorg.conf change driver to vesa? or other?

if the distro is not an dist-upgrade, you probably don't have xorg.conf (karmic use a builtin) but you can create one for specific need (xorg-configure)

---

### Post by PhilippeK on 2009-09-09
Similar problem: after upgrading to kernel 2.6.31.-10, impossible to reboot my laptop:
It stops at a black page with following message:
  [I]Booting 'Ubuntu , Linux 2.6.31-10-generic'
out of range pointer 0x400040
Aborted. Press any key to exit[/I]
Pressing any key brings the same page back. 

Thank you for assistance to unlock my computer.

---

### Post by dino99 on 2009-09-09
this error have been  discussed yet on this forum

search: out of range pointer

some threads too on launchpad

google is your friend

---

### Post by shakaran on 2009-09-09
I find a semi-fix for my friend. I change Driver to vesa, and then start (but with bad resolution).

He filled a bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/426821](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/426821)

---

### Post by PhilippeK on 2009-09-09
Grand merci Dino!

---

### Post by VMC on 2009-09-09
> **shakaran said:**
> And then reboot, his system dont init. If I choose kernels like 31-8 or 31-6 or 31-6 (he only have these) dont init!Your topic says "....Kernel 2.6.31-10 broke my system", yet your tried the previous kernels and they too failed to boot. I don't think its the kernel, but what else came along with it. I have yet to have a new kernel fail to boot my system. 

Please give us more info regarding your video card. Is it Intel, ATI, nVidia , etc?

---

### Post by Woody1987 on 2009-09-09
Same thing happened to me, i have to boot into recovery mode and then select resume and it works with the nvidia driver.

---

### Post by dinxter on 2009-09-09
> **Woody1987 said:**
> Same thing happened to me, i have to boot into recovery mode and then select resume and it works with the nvidia driver.

if you can reach recovery and then boot ok using resume then i would suggest you try disabling the splash option in grub and see how that works out
- edit /boot/defaults/grub and remove 'splash'
- run update-grub

at worst it may allow you to see whats going wrong where as you boot

---

### Post by shakaran on 2009-09-09
> **dinxter said:**
> if you can reach recovery and then boot ok using resume then i would suggest you try disabling the splash option in grub and see how that works out
- edit /boot/defaults/grub and remove 'splash'
- run update-grub

at worst it may allow you to see whats going wrong where as you boot

I try editing on first menu grub (pressing key e and editing kernel line) I put "ro single", and remove quiet and splash. But it not working in this way.

I think that is a problem with the lastest libdrm or mesa with KMS.

---

### Post by ranch hand on 2009-09-09
Well, I for one, am glad to see this thread.  I run a Radion 2400 PRO  and -8 and -9 were rough on me.  With the new update to -10 I have even enabled the ATI driver on 1 of 4 32bit variations and 1 of 4 64bit variations and they are both working and booting.

I hate to sound like I am enjoying the troubles of others but I prefer to look at it as ejoying the spreading of the FUN.

---

### Post by jlacroix on 2009-09-09
I have this same problem. I've had it for at least a month or longer. The only thing I can figure out is that it's NOT an X problem because this problem happens before the step where X inits. I've filed a bug report but nothing has come of it. Changing around video drivers for me doesn't help, further implying it's not an X issue. Furthermore, it happens with the Live CD too.

---

### Post by VMC on 2009-09-09
Maybe a look at some log outputs would reveal something. Like 'dmesg' or 'Xorg.0.log'.

It appears to be getting better with kernel and lib updates. My Intel i865 almost works now. When alpha3 rolled around, I would barely get 30 seconds before screen freeze. Now sometimes I get 30 - 40 minutes.

---

### Post by jlacroix on 2009-09-09
> **VMC said:**
> Maybe a look at some log outputs would reveal something. Like 'dmesg' or 'Xorg.0.log'.

It appears to be getting better with kernel and lib updates. My Intel i865 almost works now. When alpha3 rolled around, I would barely get 30 seconds before screen freeze. Now sometimes I get 30 - 40 minutes.

In my case, I haven't noticed anything incriminating in any of the logs.

---

### Post by xebian on 2009-09-10
Not a problem here.  2.6.31 is now stable.  So .32 could be the kernel for karmic?

---

