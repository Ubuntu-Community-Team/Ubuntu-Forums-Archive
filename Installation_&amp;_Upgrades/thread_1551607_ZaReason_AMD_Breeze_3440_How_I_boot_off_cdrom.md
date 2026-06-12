---
title: "ZaReason AMD Breeze 3440: How I boot off cdrom?"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by audreysmith on 2010-08-12
Hello List,

I just bought an interesting computer from ZaReason:

[http://zareason.com/shop/product.php?productid=16228&cat=249&page=1](http://zareason.com/shop/product.php?productid=16228&cat=249&page=1)


AMD Breeze 3440

Specs:

CPU: Athlon X2 6000+
RAM: 3GB DDR2-800 
Disk: 1TB
Nvidia GeForce 8200 GPU
Size of case: 10.4" x 12.2" x 3.9"
Rear Ports:
6x USB 2.0 Ports
2x PS/2 Ports
1x DVI Video Port
1x VGA Port
1x Gigabit Ethernet Port
Analog Audio I/O Jacks
Front Ports:
2x USB Ports
Headphone Jack
Mic Jack

It came loaded with Ubuntu 32b 10.04 LTS

I like the size.  I can fit it in my backpack.
I take it to work and use the keyboard/monitor there.
Then at night I take it home and do the same.

I see it as an affordable-Ubuntu-Mac-mini on steroids.

I've used it for a couple of days now and I really like it.

I have, however, run into an issue.

I can't get it to boot off of a cdrom.

It always boots off the hard-drive.

On all my other Linux-PCs I just drop a cdrom in the drive and reboot.

With those PCs, they will either boot off the cdrom or give me some kind of UI (like grub).

My question:

Is there any way I can get control over booting via a file in the Ubuntu file system?

---

### Post by earthpigg on 2010-08-12
hi,

typically, you need to enter bios and set the cd to have a higher boot priority than the hard drive. in the few seconds after you *first* turn it on, you ought to see something like "press f10 to enter setup" or maybe delete. whatever the button is, push it.

when you get to the bios setup, look around for something like 'boot order' or 'boot setup'.

if ZaReason (i like the company, but have never purchased from them) has some obscure or unique method of doing this (which i doubt, but it's possible), you may need to [email them]("http://zareason.com/shop/pages.php?pageid=23").

> On all my other Linux-PCs I just drop a cdrom in the drive and reboot.

With those PCs, they will either boot off the cdrom or give me some kind of UI (like grub).

this probably means someone already set it up for you, as i described above. some computers may come setup like that.

---

