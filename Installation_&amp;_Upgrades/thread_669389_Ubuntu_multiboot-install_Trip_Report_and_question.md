---
title: "Ubuntu multiboot-install Trip Report and question"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by eponymos on 2008-01-16
I just installed Ubuntu for the first time. I'm a long time Linux (Debian/Gentoo) user so I figured it'd be a breeze.

However, my oldish computer did not boot at all using the live CD, so I figured I'd waste some time hacking away!

Specs: Pentium 4 2.6GHz 1GB RAM. 2 x 200GB ATA IDE HDs Geforce FX5700

1st HD: Wndows XP
2nd HD: 1% Old linux boot pratition (not used) 89% NTFS partition 10% Ext3 (at end)

Problem the first: The Desktop Live CD didn't boot. It would just freeze with the infamous "can't set xferspeed" message.
Solution: Added irqpolling=1 to the kernel options.

Problem the second: The Install utility froze too when scanning the discs. Probably because of the same basic problem.
Ugly solution: 1. formatted the / partition manually. 2. Did a mount /dev/sdb3 /mnt/sdb3; cp -a / /mnt/sdb3.

Problem the third: Grub installation
Solution: Used grubinstall.exe to prepare stage1 and stage2 in C:\boot. I had to use the following to make it boot:
--c:\boot\Menu.lst---
timeout 0
default 0
title  Ubuntu
root   (hd1,2)
kernel /boot/vmlinuz-2.6.22-14-generic irqpolling=1 root=/dev/sdb3 rw
initrd /boot/initrd.img-2.6.22-14-generic.bak
-----
Added c:\boot\stage1="Ubuntu" to c:\boot.ini

Problem the fourth: The installation thinks it's a Live CD, though it's not! It boots directly into gdm which logs in with the user "ubuntu". No passwd!
Solution: ??

I'm kind of tired right now. Could someone please tell me why gdm behaves this way and how to fix it. It should just present a regular log in screen.

Another question.

Why do Linux distributions still require a throwaway cd to install? Why not just use Windows tools (for windows users) and/or bootable USB thumb drive-images to set up the GNU system?

---

### Post by logos34 on 2008-01-16
try one of the methods listed[ here]("https://help.ubuntu.com/community/Installation/FromWindows")

---

