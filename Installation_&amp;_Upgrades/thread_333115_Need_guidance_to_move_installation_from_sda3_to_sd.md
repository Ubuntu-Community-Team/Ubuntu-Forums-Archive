---
title: "Need guidance to move installation from sda3 to sda1 [Resolved]"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by atul_dapper on 2007-01-06
Hi folks!

I have deleted XP completely from my workstation, but need some help getting Dapper to boot from first partition.

[LIST]
[*]XP existed on /dev/sda1 and Dapper Drake exists on /dev/sda3.  
[*]Used dd if=/dev/sda3 of=/dev/sda1 and copied everything over to /dev/sda1
[*]Now, Dapper exists on /dev/sda1 and /dev/sda3, but I want to get rid of /dev/sda3 and use /dev/sda1 only.
[*]Changed /etc/fstab and /boot/grub/menu.lst on /dev/sda1 to refer to /dev/sda1.
[*]Because XP was installed first/earlier, I think the MBR was from XP
[*]I had not installed GRUB to MBR, but instead to /dev/sda3
[*](Earlier, when XP existed I had created a linux.bin, copied it to c:\linux.bin and edited boot.ini so that it would show up a boot menu with Dapper in XP.
[/LIST]

Well, I am unable to boot from /dev/sda1.  It keps booting from /dev/sda3.  I must be missing some major steps.  Please can someone provide help/guidance to enable this booting from /dev/sda1.

Thank you in advance for any help you can give.

Regards.

**[EDIT]**
Please ignore the above request, I could get through and can now use the system as desired.

-  I changed the GRUB [COLOR="Red"]menu.lst[/COLOR] on /dev/sda1 to point to [COLOR="Red"]root (hd0,0)[/COLOR] and it worked.  *(The kernel entry already pointed to /dev/sda1.)*
-  A partition size / superblock mismatch error was reported while booting which I was able to fix using [COLOR="Red"]e2fsck -f /dev/sda1[/COLOR] followed by [COLOR="Red"]resize2fs[/COLOR].

Solved!

---

