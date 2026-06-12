---
title: "recover from grub error 17"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by ricolinux on 2008-08-30
Help Please, my trusted box loaded with my UBUNTU files and settings went haywire during a regular update ti got stuck in something and when I did a Ctrl+Alt+Del a boot time all I got a "Grub 1,5 error 17" and now I can get to my UBUNTU setup.
Granted is only a old 600mhz P111,  512mgs Ram, 80gigs main HD with a second HD (120gigs).
I started this box with a fresh install of DAPPER Ubuntu and I've been upgrading it all the way to Heron 8.04, along the way I collected quite a group of applications and training videos and PDFs and now I can't recover. Yes I tried the Live CD but I couldn't get it to boot.
I'm guilty of using Windows but in the last 3 and half years I have used different flavors of LINUX (Mandrake, Red Hat, SuSe, etc) then I discovered UBUNTU DAPPER and I.ve been hooked ever since. I Now recommend UBUNTU to my clients and friends.
If any one could point me on the general direction of links to solve my dilemma I'd appreciated very much, I don't fear the Command Line I like a challenge and I'm very adept a learning by doing.
Thanksm Gracias
Ricolinux :):guitar:

---

### Post by Pumalite on 2008-08-30
Hope this helps:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by caljohnsmith on 2008-08-30
> **ricolinux said:**
> Yes I tried the Live CD but I couldn't get it to boot.

It doesn't sound like your Ubuntu partition is even readable right now, because according to the Grub manual:
> **Error 17** : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 
Can you get any Live CD to boot? If you can, I think you should first run a fsck on your Ubuntu partition:
```
sudo fsck /dev/sdaX
```
If that works, that may be all you need to get Grub working again, but whether your Ubuntu will actually boot OK is a whole different story unfortunately.

---

### Post by Pumalite on 2008-08-30
If you want to know if Ubuntu is there and if you can boot it; get Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Burn to disk and boot from it.
Super Grub can boot anything bootable.

---

