---
title: "New Side by Side Install Fail, can't boot Windows 7 or Ubuntu"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by NojoMixin on 2011-10-21
I downloaded Ubuntu last night onto a thumb drive and played with it. Liked it.

So this morning I installed it from the thumb drive to an external drive (Western Digital). I used the Ubuntu installer UI to partician the external drive. I gave Ubuntu 700 GB to play in.

Then came the reboot. Now I'm sad and don't know what to do.

error: no such device: 20xxxxx
grub rescue>

when I type ls I get
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)

I flailed around trying some grub rescue commands I didn't understand. No joy.

I can reboot from the thumb drive. But now it wants a username/password, and won't take the combo I used when I installed from disk. I don't remember it asking for one last night.

I've tried erasing Ubuntu and reinstalling. No joy.

I had work to do today, lol.

Advice?

---

### Post by 23dornot23d on 2011-10-21
Follow the instructions here ... we need your boot info

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

you may have installed the boot loader to hd1 ....... but we need the file above please.

> 
I can reboot from the thumb drive. But now it wants a username/password,  and won't take the combo I used when I installed from disk. I don't  remember it asking for one last night.



sounds actually as if the booloader is on the thumb drive .......

keep it safe ..... and do not modify it ....

use another thumb drive if you must .... to boot from ..... if you have another one .....
or boot from a livecd if you can

---

### Post by NojoMixin on 2011-10-21
I can't get to a terminal, so I can't run the Boot Info Script.

When I boot with the thumb drive I am asked for a user name and password that I don't know.

Last night, when I ran from the thumb drive it just worked. I don't remember entering a user name or password.

This morning, when I installed to disk, I did set a user name and password, but that does not work when I boot from the thumb drive.

I'd be real happy to start all over again, if only I could get back to Windows 7 and the work I have to do today.

I have my Windows 7 install disc. I'm thinking about booting from that, but don't want to loose any data on my system.

---

### Post by NojoMixin on 2011-10-21
I tried fixing my Windows 7 boot with bootrec.exe.

No Joy.

And with bootrec.exe /ScanOs,
I get back 0 Windows installations.

This is not good.

---

