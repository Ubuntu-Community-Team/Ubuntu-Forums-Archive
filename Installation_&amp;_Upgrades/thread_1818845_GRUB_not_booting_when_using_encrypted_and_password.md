---
title: "GRUB not booting when using encrypted and password protected drive"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by djdez on 2011-08-05
Hi Guys,

I replaced the harddisk of my Dell laptop (Latitude d620) with a harddisk which has hardware encryption and a password protection. The software used to configure the drive is called “Wave Systems' EMBASSY Trust Suite (ETS) for Dell”.

After configuring the harddisk, Grub wouldn’t boot and gives the message:
```
Grub loading
error unknown filesystem
grub rescue>
```

This happens when I do a cold boot of the system.
With a cold boot I get a prompt to enter my password and after that I get the Grub error.
When pressing crtl+alt+del at the Grub rescue, the laptop reboots and I get the Grub bootloader screen as it should be.

So the problem only occurs with a cold boot, when the password security of the harddisk kicks in.

I’m using Ubuntu 11.04, the harddisk partitiontable is MBR and the partition itself is ext4.

I already found some post regarding this problem, but no solution so far :(
[http://www.linuxquestions.org/questions/linux-newbie-8/embassy-trust-suite-causes-grub-error-17-a-664636/]("http://www.linuxquestions.org/questions/linux-newbie-8/embassy-trust-suite-causes-grub-error-17-a-664636/")
[http://www.dsi.cnrs.fr/service/securite/Documents/disque_chiffrant_linux.htm]("http://www.dsi.cnrs.fr/service/securite/Documents/disque_chiffrant_linux.htm")

I reinstalled Grub but that didn’t change anything.
The weird thing is that the Windows bootloader doesn’t have any problems, but I want to use Grub.
I Also found Grub4dos([http://gna.org/projects/grub4dos/]("http://gna.org/projects/grub4dos/")) what should do the trick, but this only works with ext2 and ext3, while I’m working on ext4.

I cannot imagine that this can only be done with some sort of Windows/DOS bootloader, so I hope that some of you can push me in the right direction to solve this problem.

Thanks!

---

