---
title: "After auto upgrade to Hardy boot hangs"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by peac on 2008-05-08
I used the auto upgrade and it ran flawlessly - except when it rebooted at the end the boot process hung. I tried adding noapic and acpi=off to the kernel string as suggested in several threads, but no luck. Finally tried using the 2.6.22-14-generic kernal, rather than the 2.6.24-16-generic. This seems to work, although I'm getting a lot of errors when I try to adjust the display (e.g. "Failed to execute child process "compiz" (No such file or directory)", "File to execute child process "metacity"..."). Unfortunately I can't see all of some windows so navigation is a bit of a pain.

I've tweaked the /boot/grub/menu.lst to reverse the kernel listing order so that I can boot without ESCing into GRUB setup mode. I've also turned off "quiet" so I can see better where it's failing. The normal kernel (24-16-generic) seems to hang when it's trying to load hardware drivers. 22-14-generic gets all the way through, also it does fail on "setting kernel variables", and it forces me to reset the display every time.

This has not been a pleasant upgrade process. Any suggestions for how to get this working again would be welcome.

I'm running a Dell Inspiron 8200 laptop - 1.7GHz Pentium with 256 MB RAM - pure Ubuntu. It ran great with the previous version, but Hardy has not been as easy.

---

### Post by fancyl on 2008-05-08
I'm having the same problem, I think. I'm a fairly new linux user and this is really discouraging me. I don't know where to even start solving this problem. If someone would please include a detailed solution, I would really appreciate it.

I'm on a DELL Vostro 200, from Japan. I upgraded smoothly from Gutsy a week ago, but have been having the same problem with kernal 2.6.24-16-generic hanging on startup. I have just started scrolling down to 22-14 every time I start up.

Thanks.

---

### Post by peac on 2008-05-08
Sounds like the identical problem, fancyl. With Gutsy I did have to add noapic and acpi=off to the boot string, but other than that never had a problem. Good news / bad news: Gutsy was my first time with Linux and it worked so well that I don't know what to do to trouble-shoot the Hardy problems! I'm hoping that someone has suggestions, otherwise my next step will be to download a CD and try a completely clean installation. Hate to have to reinstall my apps, but that's one way to narrow down the problem.

---

### Post by peac on 2008-05-10
Well, I gave it my best and still can't get Hardy to work. I've come to the conclusion that Hardy is not quite baked yet. I'm reinstalling Gutsy.

---

### Post by fancyl on 2008-05-16
I was hoping that all the security updates and program updates this past week would solve my problem, but it hasn't fixed itself yet. Does anyone else out there have any suggestions for us?

---

### Post by iaculallad on 2008-05-17
Try browsing this [Link]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/201673/comments/12"). Seems like you have similar problem.

---

