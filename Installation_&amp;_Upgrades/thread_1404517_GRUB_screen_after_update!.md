---
title: "GRUB screen after update!"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by robembra on 2010-02-11
Hi,
 
I have used wubi to install ubuntu 9.10 and everything was working fine until I rebooted and now I get a black screen saying GRUB at the top.
 
I have searched around the internet and I have found this:
[LIST=1]
[*][COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]set root=(loop0)[/COLOR]**
[*][COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro[/COLOR]**
[*][COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]initrd /boot/initrd.img-2.6.31-14-generic[/COLOR]**
[*][COLOR=#800000]sh:grub>[/COLOR]**[COLOR=#800000]boot[/COLOR]**
[/LIST][COLOR=#800000][COLOR=black]Now is says loop=/ubuntu/disks/root.disk is the location if it was installed @ C:\ubuntu but on my system it is F:\ubuntu what do i have to change?[/COLOR][/COLOR]
[COLOR=#800000][COLOR=#000000][/COLOR][/COLOR] 
[COLOR=#800000][COLOR=#000000]Thanks![/COLOR][/COLOR]

---

### Post by meierfra. on 2010-02-11
Those instructions only work some of the time   and only are temporary solution.   For a permanent solution see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

but replace "C:" by "F:"

---

### Post by gungrog on 2010-02-11
You'll need to run:

sudo update-grub2 

in the terminal afterwards, that should make the changes permanent.

---

### Post by meierfra. on 2010-02-11
gungrog: Please have a look at the link I posted.  "update-grub2"  is not a permanent solution.

---

