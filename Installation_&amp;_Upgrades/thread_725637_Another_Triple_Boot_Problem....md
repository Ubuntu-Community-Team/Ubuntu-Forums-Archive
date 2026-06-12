---
title: "Another Triple Boot Problem..."
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by ROm222 on 2008-03-15
I reinstall my system (Im using a MacBookPro 2nd generation) and want to have ubuntu 7.10 (desktop) running along with Leopard and WinXP SP2.

I really don't get what Im doing wrong, that's what Im doing:

- Put all my HD into 1 partition and install Leopard. (ok)
- Using boot camp a split (50g ~ 60g ) my partition and install WinXP on the 60g (ok)
- Install refit (ok)
- Now I can boot on both system (Leopard & WinXP) no prob. (ok)
- Pop in ubuntu 7.10 (desktop) and boot the install from the refit menu. (ok)
- Everything goes smoothly then I start the ubuntu install from the live desktop (ok)

[ Here comes the tricky part... ]

- I select manual partition
- Then select the 60g partition that I split in 2 ( 30g / 30g )..
- I select the new partition and take out 1g of that for my swap.
- I select the 29g partition and set the filesystem to ext3 and the mount point to be /
- I select the free 1g and put it as swap.
- Now I got something like:

	...
	...
	...

	/dev/sda3 = /media/Untitled, NTFS
	/dev/sda4 = Ext3 ( / )
	/dev/sda5 = Swap


- I continue the ubuntu installation and set the bootloader to be installed on /dev/sda3 ( I even tried /dev/sda4 )
- Then I install everything and now the problem occur... When the computer restart I can see from refit MacOS, WinXP, Linux (in that same order). But now... only Leopard & Ubuntu can boot... If I select WinXP I get a Cannot find ... <Windows Root>\system32\hal.dll (if I set on /dev/sda3) or "Error loading OS" if I set to /dev/sda4

My question is WHAT AM I DOING wrong!??!! really I don't get it. I think the part where Im screwing up my MBR is when I set the bootloader to /dev/sda3 ( or tried with /dev/sda4) but no success... so where GRUB should go then?

Someone please help I redo the process 2 ~ 3 times already and I always end up with practically the same result I don't know what Im doing wrong... 

I follow the tutorial on "https://wiki.ubuntu.com/MacBookPro" and simply replace the Vista part with WinXP but it doesn't seems to work...

Tks in advance,

Cheers!

---

### Post by Peter09 on 2008-03-16
I have never used it, but there is a utility call supergrub which is supposed to repair and fix grub issue, might be worth a try.

Here is a link

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

PC

---

### Post by sandysandy on 2008-03-16
have a look at these links

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

[http://discussions.apple.com/thread.jspa?messageID=4755362&tstart=0](http://discussions.apple.com/thread.jspa?messageID=4755362&tstart=0)

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

regards

---

