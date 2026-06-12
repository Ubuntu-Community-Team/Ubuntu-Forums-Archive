---
title: "Kernel issues with upgrade from 7.04 to 7.10"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by barrack on 2007-11-18
I just recently upgraded from Feisty to Gutsy and for the most part everything is running fantastic, except for one somewhat major problem.

After all updates were done, Ubuntu now doesn't load with consistent success. Everytime I boot up, I get four messages that say "Cannot allocate resource region." After a few moments it will go to the splash screen with the progress bar. At that stage, it will just hang. Sometime a reboot will help, sometimes not. This is with kernel 2.6.22-14.

When in the GRUB stage of the boot up, I decided to try an older kernel, 2.6.20-16. Everything worked just fine with this one. There are no messages about resource regions and definitely no hang ups with booting.

My question is this: is there a fix coming to address the issue with kernel 2.6.22-14? or is there a way so that it boots up with kernel 2.6.20-16 without me having to go into the GRUB menu everytime?

This is an aside if anyone feels to answer: what's the difference between these kernels?

I am running ubuntu 7.10 gutsy on a compaq presario c563 laptop.

---

### Post by tajreed on 2007-11-18
Not a one off problem. You can boot the -16 kernel by editing the /boot/grub/menu so that -16 starts automatically. The first boot kernel in the menu is 0, so count down to the -16 kernel and enter the appropriate nr at "default num".
 
I solved the booting error on -14 by adding "all_generic_ide" without the quotes to the end of the -14 boot string. Try it out when first booting up. If it works,  edit the /boot/grub/menu  file.

This issue, at least mine, was reported as a bug.

---

### Post by barrack on 2007-11-19
> **tajreed said:**
> I solved the booting error on -14 by adding "all_generic_ide" without the quotes to the end of the -14 boot string. Try it out when first booting up. If it works,  edit the /boot/grub/menu  file.

How do I go about adding what you said to the string?

---

### Post by mikewhatever on 2007-11-19
Hi barrack,

the boot error you saw is a known one. I've been getting it with Edgy, Feisty and Gusty, plus some preview kernels. It has been discussed on the forums and launchpad.net. Here's one thread about it [http://ubuntuforums.org/showthread.php?t=415239](http://ubuntuforums.org/showthread.php?t=415239)
There seems to be no solution so far. (I don't know what all_generic_ide do, you might want to check first.) Luckily, as far as I am aware, it is purely cosmetic.

To boot the kernel you want by default you'd have to edit /boot/grub/menu.lst file.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by barrack on 2007-11-19
> **mikewhatever said:**
> To boot the kernel you want by default you'd have to edit /boot/grub/menu.lst file.
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

I followed the very easy instructions on this link and i was able to boot the -16 kernel by default. Quick and painless and no "resource region" message and no hang ups at the load screen!

Thanks!

---

### Post by tajreed on 2007-11-19
I needed the -14 kernel so that i could use Virtualbox. So I added "all_generic_ide" to the -14 boot line and it worked.

At boot during the 3 second countdown, hit esc. You can select the -14 kernel and edit the boot line with "e". Instructions are there. After editing the -14 boot line, hit enter then see if it will boot. Hit "b"

---

### Post by barrack on 2007-11-19
> **tajreed said:**
> I needed the -14 kernel so that i could use Virtualbox. So I added "all_generic_ide" to the -14 boot line and it worked.

At boot during the 3 second countdown, hit esc. You can select the -14 kernel and edit the boot line with "e". Instructions are there. After editing the -14 boot line, hit enter then see if it will boot. Hit "b"

Okay, so I am willing to do this now that I understand a little more of what's going on. What I don't quiet know is where you intend for me to add the line "all_generic_ide"

This is what is looks like right now:
```

root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=87f723db-7b60-4375-84ff-d99cdbcac70f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Am I to add another line after "quiet" or does it go somewhere else?

Thanks so much for the help so far!

---

