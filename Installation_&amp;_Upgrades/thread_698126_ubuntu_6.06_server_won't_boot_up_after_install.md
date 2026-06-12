---
title: "ubuntu 6.06 server won't boot up after install"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by zmac on 2008-02-15
I installed ubuntu 6.06 with the LAMP option specifically recently.  I partitioned the drive to have 100mb for /boot and then the rest for /.  The install went fine with no error messages.  However, when I remove the install disk and the system restarts, it keeps looping through the same sequence over and over:
[LIST]
[*]Compaq screen pops up
[*]Grub loader pops up
[*]Messages come up saying that the server is loading
[*]Last message is boot
[*]System restarts
[/LIST]

I have tried to put the "noapic" message in the kernel line and that didn't solve it.  This computer was an old Compaq Presario that had Win98SE originally on it.

---

### Post by zmac on 2008-02-19
Anyone have any thoughts???

---

### Post by confused57 on 2008-02-19
I had the same problem on an old AMD K6-2, 500 Mhz:
[http://ubuntuforums.org/showthread.php?t=504076](http://ubuntuforums.org/showthread.php?t=504076)

---

### Post by zmac on 2008-02-26
> **confused57 said:**
> I had the same problem on an old AMD K6-2, 500 Mhz:
[http://ubuntuforums.org/showthread.php?t=504076](http://ubuntuforums.org/showthread.php?t=504076)
Appreciate your help, confused57 - I ended up consulting one of the linux server admins at my work and he recommended centos 3 as a nice server for older boxes - installed really easy and has everything on it - all the best...

---

### Post by az on 2008-02-26
> **zmac said:**
> I installed ubuntu 6.06 with the LAMP option specifically recently.  I partitioned the drive to have 100mb for /boot and then the rest for /.  The install went fine with no error messages.  However, when I remove the install disk and the system restarts, it keeps looping through the same sequence over and over:
[LIST]
[*]Compaq screen pops up
[*]Grub loader pops up
[*]Messages come up saying that the server is loading
[*]Last message is boot
[*]System restarts
[/LIST]

I have tried to put the "noapic" message in the kernel line and that didn't solve it.  This computer was an old Compaq Presario that had Win98SE originally on it.

Sounds like the hardware is not 686 or better (Via C3, for example.)  You would need to install the linux-386 kernel in Dapper.  The installer on the cd boots the desktop cd to do the install, but puts the server kernel on the installed system, so the first time you actually boot the server kernel is when you reboot.

You need to chroot into your new install and install linux-386.  

On Edgy, Feisty and Gutsy, the kernel is named linux-generic.

---

