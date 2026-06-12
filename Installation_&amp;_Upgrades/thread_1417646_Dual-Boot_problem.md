---
title: "Dual-Boot problem"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Exus on 2010-02-27
Hi, i installed Windows 7 (64bit) in my primary hard drive(sda1), with is also where my BIOS boots. And in my other hard drive(sdb1) i installed ubuntu 9.10.
The problem is that i can't boot into ubuntu, it goes directly to Windows 7. I tried to configure the grub2, but it didn't work.
I think that i can solve this problem installing the grub2 in the MBR of the primary drive, but i don't know how.

I used this from the LiveCD:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb


So, how can i configure grub2 to dual-boot?


That's all, thanks.

---

### Post by inclusivedisjunction on 2010-02-27
Why not just change the boot order in your BIOS?

---

### Post by darkod on 2010-02-27
You can install grub to the MBR of your windows disk, but much better option would be to go into your BIOS and find the hdd boot order, and set it so that you are booting from the ubuntu disk.
Right now you are booting from the windows disk and it goes straight to windows.

Otherwise, to add grub2 to the other MBR too, the commands would be slightly different (because you want the other disk as destination):

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

---

### Post by Exus on 2010-02-27
I tried to change the boot order, but it goes directly to ubuntu. Windows doesn't appear in the grub menu.

---

### Post by Partager on 2010-02-27
Check out this, it may help...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Exus on 2010-02-27
Well, i wrote the MBR of the other disc, and it worked.
Thanks to all, and especially darkod who told me the command line code.

---

