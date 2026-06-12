---
title: "Upgraded to 10.4, now XP won't boot"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by rug77 on 2010-04-29
Hi all,

I've looked in the grub.cfg file, and it has :

```
#

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 569841139840f2d3
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

When I select to boot XP, the screen goes blank for a few seconds before re-displaying the Grub menu.

I only really use XP for gaming, but I would like to be able to play them ...

Please does anybody have any ideas how to fix this - it worked perfectly well before the upgrade today.  And I waited for the actual release to ensure it was going to be OK :(

Matt

---

### Post by okayneil on 2010-04-29
Ubuntu 10.4 is delayed due to this bug. 

> #BUG570765 came up earlier this week and it's bringing up the fact that when installing Ubuntu 10.04 LTS on a system with another operating system present, GRUB2 will not show the other operating system once installed for the dual/multi-boot system. It doesn't matter whether the other operating system is Microsoft Windows or another Linux installation, but the GRUB2 boot-loader doesn't offer you the option to boot that OS, just Ubuntu.[Source]("http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng")

I realise this doesnt help, but why not just wait for 10.4 to officially come out then upgrade again (if thats even possible)

---

### Post by rug77 on 2010-04-29
I didn't realise that it had been delayed - there was no warning on the update manager - which was there last night but gone this morning.

Good news however - I've found out what I did wrong, and (better still) a fix.

During the upgrade there is a section where the grub configuration asks for your bootable partitions to install grub to.  I included the windows partition - which then led to the MBR on that partition being overwritten.  Foolish perhaps, but not clear at the time ...

By following the instructions on ***[this page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)* **, I was able to restore the MBR, and am sorted.

Looked for hours, then found the answer 30 minutes after posting ...

Matt

---

### Post by sadara@dds.nl on 2010-05-01
thanks rug77!
like you, i overwrote my MBR on the XP boot device.
using testdisk i restored it very quickly and simply.

---

