---
title: "no menu or auto boot from grub prompt"
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by gmunger on 2006-05-07
When I boot my system I get a grub prompt, but nothing more.

I just installed ubuntu 5.1, sata drives, no dual boot. One drive has an old Fedora install on it, but this is mounted to /media/sdx so I don't think it affects anything. 

If I enter the grub commands manually it boots fine:
[I]root (hd0,0)
kernel  /vmlinuz-2.6.12-10-386 root=/dev/sda2 ro
initrd   /initrd.img-2.6.12-10-386
boot[/I]

These same commands are in the /boot/grub/menu.1st, I do have a separate boot partition (comments and following entries are removed):

[I]default         0
timeout         10
hiddenmenu

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash
initrd          /initrd.img-2.6.12-10-386
savedefault
boot[/I]

[COLOR="Red"]Is there is something missing from my menu.1st file?[/COLOR]

---

### Post by adam.tropics on 2006-05-08
I have heard of a few people having Sata issues, but as for menu.lst, it seems basically good. You could always try one of the Grub recovery methods. Check out post#2 here. It links to a couple ways of recovering/reinstalling Grub. Good luck!

---

### Post by gmunger on 2006-06-19
I found another related post here
[http://www.ubuntuforums.org/showthread.php?p=1062367#post1062367](http://www.ubuntuforums.org/showthread.php?p=1062367#post1062367)

Yesterday I removed the second sata drive and grub worked fine from then on. In my case I'll just keep the second drive out rather than trying to remap.

---

