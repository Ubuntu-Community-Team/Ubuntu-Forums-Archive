---
title: "Can't boot live ISO"
date: 2016-10-04
forum: Installation &amp; Upgrades
---

### Post by MadleSs on 2016-10-04
Hi guys. 
I want to dual boot Ubuntu Gnome alongside windows 10, but when I try to run live session I end up in busybox with a message
EFI: Problem loading in-kernel X.509 certificate (-74) 

Anyone knows what the problem could be? 

Thanks in advance

---

### Post by oldfred on 2016-10-04
Is this a PPC?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1541151](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1541151)

Do you have Secure Boot on?

This says it may be a video driver issue, what video driver?
[https://forums.opensuse.org/showthread.php/506718-After-Kernel-update-Problem-loading-in-kernel-x-509/page9?](https://forums.opensuse.org/showthread.php/506718-After-Kernel-update-Problem-loading-in-kernel-x-509/page9?)

---

### Post by MadleSs on 2016-10-04
Secure boot is on yeah, Windows is installed under UEFI and video driver is intel HD graphics 4600 and nvidia gForce GT740m not sure what is PPC sorry

//update
What is weird I was just able to boot into live version of ubuntu. might be some troubles with ubuntu gnme ISO?

---

### Post by MadleSs on 2016-10-04
Dont know what happend, but now Im writting from fresh installation of gnome ubuntu... So thanks for help, guess we can lock this :)

---

### Post by ajgreeny on 2016-10-04
Do you know what happened to make it suddenly work?

Did you boot again to the live system and then install from it or did you make any changes in Win 10 before managing to get this to work, eg, did you turn of secure boot?

In any case, that is great!
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

