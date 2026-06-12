---
title: "No 64-bit disk driver for Dell 2950?"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by dhjdhj on 2008-10-28
Just received a brand new Dell Poweredge 2950 Server and wanted to install Ubuntu on it.

First I tried the desktop Ubuntu but got stuck very quickly (even trying live mode) with an initramfs shell and couldn't go beyond that.

So I downloaded the 64-bit server version to try instead. It gets to the point where it does disk detection but it can't find any drive in the machine.  (There's a Seagate 500Gb SATA drive in the machine).  It offers to let me pick a driver but none of them worked (yeah, I tried them all -- sigh)

Just for curiosity, I then tried installing 32-bit version of the server and it had no problem detecting the drive (I don't know what driver it used though) and I quickly got to the point where I could begin partitioning the drive (and nice to see that LVM support is in there).

But I stopped there....I'd much rather get 64-bit version installed so I can access the full 16Gb of RAM installed on the machine but I've no idea (a) what driver I need (b) if it even exists and (c) how I would install it since we didn't buy a floppy drive for the machine (would USB stick work?)


Would very much appreciate suggestions for how to proceed.

Thanks in advance,
David Jameson

---

### Post by lemming465 on 2008-10-30
You don't mention what version of Ubuntu you tried; I'm guessing 8.04.1.  Maybe 8.10 will do better, though that's not LTS, so you'd have to upgrade after 18 months.

Dell officially supports redhat enterprise 4 and novell suse 9, so Linux is definitely possible.  Their linux.dell.com  site has ubuntu DVD's for some of their desktop machines, but not their servers.  If you need free you could consider CentOS, which is a Redhat Enterprise clone.

A 32-bit version of Ubuntu should be able to address all 16 GiB of RAM, but individual programs will have trouble using more than 3 GiB each, and you'll take a 15% performance hit for not using all the registers and having an extra level of page tables.  So 64-bit will be better if you can get it to work, yes.

The problem in these cases is usually a driver for the disk controller.  You didn't say whether that was the intel X5000 or the optional Perc.  Intel or LSI might have drivers on offer; yes, you should be able to load them off a USB fob without a floppy.

---

### Post by dhjdhj on 2008-10-31
Many thanks for responding, I appreciate that. I knew it was a driver problem but it was not obvious to me from where I could get the needed driver --- some searches I performed did not show anything useful.

In the end, I found that 64-bit Fedora installed with no problem so it clearly had the required drivers. While I would much prefer to use Ubuntu over Fedora these days, my priority is to get the machine up and running to get some needed apps deployed as soon as possible.

If you (or anyone) can point me at a site that can help me find exactly the drivers I need, and how to install them, etc, I would definitely take another shot at it. I have extra hard drives available so that I could just pull out the Fedora system and play around with another system knowing I can just revert to Fedora if I get nowhere.

Cheers,
David

> **lemming465 said:**
> You don't mention what version of Ubuntu you tried; I'm guessing 8.04.1.  Maybe 8.10 will do better, though that's not LTS, so you'd have to upgrade after 18 months.

Dell officially supports redhat enterprise 4 and novell suse 9, so Linux is definitely possible.  Their linux.dell.com  site has ubuntu DVD's for some of their desktop machines, but not their servers.  If you need free you could consider CentOS, which is a Redhat Enterprise clone.

A 32-bit version of Ubuntu should be able to address all 16 GiB of RAM, but individual programs will have trouble using more than 3 GiB each, and you'll take a 15% performance hit for not using all the registers and having an extra level of page tables.  So 64-bit will be better if you can get it to work, yes.

The problem in these cases is usually a driver for the disk controller.  You didn't say whether that was the intel X5000 or the optional Perc.  Intel or LSI might have drivers on offer; yes, you should be able to load them off a USB fob without a floppy.

---

