---
title: "Dual-boot failure: 10.04 installed, XP won't boot"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LooseCanon on 2010-04-27
After downloading the 10.04 release candidate the other night (to test its compatibility with my wireless adapter), my installation of Windows XP will not boot. It shows up the same as usual in GRUB, but once I select it, the screen stays a single blinking cursor indefinitely.

I'm really not excited about the idea of reinstalling windows and all the other software I put on there. Is there a way to make GRUB load my installation properly?

---

### Post by oldfred on 2010-04-27
Looks like we have spam:confused:

Post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Did you choose to install grub in more places than just the MBR of sda. If you installed grub to the windows partition you overwrote the windows boot loader.

---

### Post by LooseCanon on 2010-04-27
Thanks for your speedy reply! :D


> **oldfred said:**
> Did you choose to install grub in more places than just the MBR of sda. If you installed grub to the windows partition you overwrote the windows boot loader.

I believe I did install it to multiple locations: that would be because I'm new to Ubuntu and ***it recommended it***.

The install instructions said to install grub to all partitions if I wasn't sure which one was the primary; it did *not* inform me that doing so could damage another installation. :mad:

I knew windows would overwrite grub back when I first installed, so I did things in the right order; I believed that grub didn't do that, but became a sort of gateway, from which you could boot linux or windows.

Now what?

(I'll work on getting you the results of that script--I probably won't be able to do anything with it until tomorrow afternoon--but it sounds like you already know what the problem is.)

---

### Post by oldfred on 2010-04-28
The script will tell us for sure. But if you want to read ahead see this page. If you go up to the main page are the other main windows/grub issues we see. Site is from meierfra who maintains the boot script.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

He recommends testdisk which works well from Ubuntu or any linux and is often installed on most linux repair CDs, but you also can run windows repairs that usually work from the windows CD.

---

### Post by LooseCanon on 2010-04-29
> **oldfred said:**
> The script will tell us for sure. But if you want to read ahead see this page. If you go up to the main page are the other main windows/grub issues we see. Site is from meierfra who maintains the boot script.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

He recommends testdisk which works well from Ubuntu or any linux and is often installed on most linux repair CDs, but you also can run windows repairs that usually work from the windows CD.

testdisk did the trick! I went ahead and followed his instructions on that, and it worked like a charm. Thanks so much for your help!

---

