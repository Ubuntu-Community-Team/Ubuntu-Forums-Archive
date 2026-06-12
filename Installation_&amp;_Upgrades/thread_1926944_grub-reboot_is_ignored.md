---
title: "grub-reboot is ignored"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by stn21 on 2012-02-17
Hi,

on ubuntu 10.04 server I try 

```

grub-reboot 2
Searching for GRUB installation directory ... found: /boot/grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> savedefault --once --default=2
grub> quit

Do you want to reboot now? [y/N]
```Looks fine to me. Except for the fact that the setting is ignored completely. The next reboot simply starts the default first menu-entry.

What is wrong here?

THX, stn

---

### Post by raja.genupula on 2012-02-17
you can change it in two ways 

* edit your grub.cfg  file 

* but better than that and safe ways we have .  almost all GRUB related operations you can perform by using Grub-Customizer . 

[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)


that will helps . 

all the best and let us know if anything comes up .

---

### Post by stn21 on 2012-02-17
> **raja.genupula said:**
> ... * edit your grub.cfg  file ...

Good, that is what I thought too. How do I have to change it? There are already lots of lines that refer to "saved states", so why is it not working?

THX, stn

---

### Post by stn21 on 2012-02-17
> **raja.genupula said:**
> ... * but better than that and safe ways we have .  almost all GRUB related operations you can perform by using Grub-Customizer . ...

That looks good for the usual customization of the boot-menu, thank you for the tip.

For the problem of this thread it does not seem to have any relevance. The boot-menu works good enough as it is. The only thing that does not work is temporarily changing the default menuitem for the next reboot. (That is what grub-reboot should do).

---

### Post by raja.genupula on 2012-02-18
so you want a automatic boot into previous boot operating system , I got a link for you with good enough explanation . please look at here 

[http://superuser.com/questions/137875/can-grub-be-configured-to-remember-the-last-os-you-booted-into](http://superuser.com/questions/137875/can-grub-be-configured-to-remember-the-last-os-you-booted-into)

All the best .

---

### Post by stn21 on 2012-02-20
> **raja.genupula said:**
> so you want a automatic boot into previous boot operating system , I got a link for you with good enough explanation . please look at here 

[http://superuser.com/questions/137875/can-grub-be-configured-to-remember-the-last-os-you-booted-into](http://superuser.com/questions/137875/can-grub-be-configured-to-remember-the-last-os-you-booted-into)

All the best .

Thank you raja. That link explains how to get grub to remember the last chosen menu-item.

Grub-reboot is a bit different. It sets the selection for the _next_ reboot and _only_ for the next reboot. Any reboots after that go to the default selection again.

This should work. Especially since grub-reboot has no other purpose and has only one commandline-option. Only it doesn't. Looks like a bug to me. Unfortunately I have no idea where to start looking for a solution.

Any ideas ?

THX,stn

---

