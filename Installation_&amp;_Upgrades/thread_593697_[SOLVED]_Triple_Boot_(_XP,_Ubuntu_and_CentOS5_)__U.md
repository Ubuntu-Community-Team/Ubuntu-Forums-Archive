---
title: "[SOLVED] Triple Boot ( XP, Ubuntu and CentOS5 ) : Ubuntu's Grub lost."
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by shankariyer on 2007-10-27
I searched the forums here, but my case is a bit different.

I had XP and Ubuntu ( Gutsy ) working fine. Then I wanted to triple-boot with
CentOS.

I [read]("http://www.go2linux.org/triple-boot-windows-two-linux") that I'd install CentOS and point CentOS boot-loader to install at the
same place as where CentOS is /dev/hda12 and not /dev/hda1( MBR that
Ubuntu was using )

But, now when ever I reboot, I see CentOS's Anaconda GRUB and it doesn't
Ubuntu. It has CentOS and XP.

Now, what are my options?
Is there a way to install Ubuntu's GRUB back and follow as per the [instruction]("http://www.go2linux.org/triple-boot-windows-two-linux")?

Thanks.

---

### Post by meierfra on 2007-10-27
What boot loader is installed in the MBR?

Depending on the boot loader you might be able to solve your problem by setting the boot flag to the ubuntu partition. (Let me know if you need help with that)

Or, if   your are willing to install Grub to the MBR,  you can follow this howto:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by shankariyer on 2007-10-27
CentOS's GRUB is controlling the show.

I did the following...

1. Logon to CentOS
2. Mount the boot partition of Ubuntu
3. Copy /boot/grub/menu.lst entries of Ubuntu, to CentOS's grub
4. Tweak /etc/fstab

Then I was able to logon to CentOS/Ubuntu/XP !

However, Ubuntu lost all memory on Windows partitions ( NTFS's ), wonder why.

Thanks for the pointers.

---

