---
title: "Several Problems with netbook install"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by Shadow13 on 2011-01-16
Yesterday I decided that I would like to install Ununtu on my netbook, as i currently run it on my desktop and am a huge fan.  It ran fine off of the USB that I was using as the installer, but when I went through the full installation and tried to boot into it it told me that it gave up waiting on root device.  I've looked through several threads but none of them seem to fix my problem.

Here is what I have tried:

1. deleting the line that says 
  search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
[FONT=Verdana]
2. downloading the iso again and doing another install

In normal circumstances I would most likely just give up and live with Windows, however my
problem is that when attempting the second install, at the partitioning portion, it only showed
my previous Ubunutu install and the one I was currently attempting, so I told it to use entire 
partition.  Now Windows 7 does not come up as an option in the bootloader.  Have I completely
wiped out that OS? 

I saw in some other posts that the boot info script was often helpful in these situations, so 
I am attaching it.
[/FONT]

---

### Post by C.S.Cameron on 2011-01-16
Boot failures on systems with Intel D945 motherboards

Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 8.10. This may cause the system to drop to a busybox initramfs shell on boot with a "**Gave up waiting for root device.**" error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (Bug 290153).

---

### Post by Shadow13 on 2011-01-16
after typing Exit, it booted after a very long time

however, in the /boot/grub directory, There is no menu.lst file.  

It might also be useful to state that I am attempting the latest netbook version of ubuntu.

Now that it is booted, it is also unable to connect to my wireless network.

---

### Post by Quackers on 2011-01-16
Grub2, which is probably what you are using, doesn't use menu.lst, so it's empty anyway, and changes to it have no effect.

---

