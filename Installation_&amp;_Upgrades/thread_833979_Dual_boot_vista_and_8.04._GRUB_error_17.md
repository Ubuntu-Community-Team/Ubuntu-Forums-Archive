---
title: "Dual boot vista and 8.04. GRUB error 17"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by MSdefecter on 2008-06-19
Hi,
First of all I know there are lots of posts relating to this but I have installed vista and then reinstalled on a seperate hard drive ubuntu 8.04. I used to have xp and 7.10 setup on a dual boot and that went fine but 8.04 and vista seem to be far more hostile towards each other beacuse when I try to boot from my ubuntu drive I get a GRUB error 17 appear. When I boot from vista it works fine suggesting that grub now no longer installs into the windows mbr like it would under xp. I am unsure of the exact command to use and which editor use to edit GRUB to point to my vista hard drive. I was wondering if anyone knew the best way to dual boot these two OS's and in what order to do everything as a fresh reinstall of both systems is not to much of a problem as long as it solves it. I would prefer not to resort to WUBI if it can be helped so any assistance would be greatly appreciated.

---

### Post by logos34 on 2008-06-19
> **MSdefecter said:**
> when I try to boot from my ubuntu drive I get a GRUB error 17 appear. When I boot from vista it works fine suggesting that grub now no longer installs into the windows mbr like it would under xp.

maybe the ubuntu disk was first in the Bios hard disk boot order at installation time, or else it's on an ide disk and windows is sata (grub sees/scans ide/pata controller first). The installer writes grub by default to the mbr of whatever disk is first in the bios '(hd0)'.

Since you appear to be getting the error before the menu screen, you could try booting to the ubuntu livecd and check /boot/grub/menu.lst--the 'root' lines (and 'groot') should read '0' **(hd[COLOR="Blue"]0[/COLOR],?)** if you're booting from the ubuntu disk.  If the latter is your setup, the windows entry at the bottom should have [mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") included.

If you manage to fix the ubuntu boot, but vista refuses to boot from grub, you could try [EasyBCD method ]("http://neosmart.net/wiki/display/EBCD/Linux")to dual boot.

Follow the troubleshooting steps here:

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
[http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

