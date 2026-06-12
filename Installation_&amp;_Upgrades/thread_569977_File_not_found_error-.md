---
title: "File not found error-"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2007-10-07
Hi -
So I finally write after doing a whole lot on my own, but getting no where. Here is my problem - and I think I have written about this a few times before too -

I have 3 HDDs - 
the first one is a 160GB SATA drive - the entire disk has Ubuntu 7.10 on it, and I don't want anything else on it. That is the drive where I have the grub installed as well. In the Grub parlance, it is called hd1 and is mapped as /dev/sda.
the second drive is an IDE 80GB - the entire disk has Kubuntu 7.04 on it, again, I would like to keep it as it is. The Grub knows it as hd0 and is mapped as /dev/hdb.
the third drive is 320GB SATA drive - the entire disk has Ubuntu 7.04 on it, again, not wanting to change it. The Grub knows it as hd2 and is mapped as /dev/sdb.

Now here is the deal - 
With 7.10 still in the beta stage, it keeps updating on pretty much a daily basis - and I don't have a complain with that. My only problem is - when I boot from the grub - there are a bunch of options out there - please look at the snippet from my menu.lst below -

GRUB MENU.LST SNIPPET --------------------------------------------------------------

title		Ubuntu gutsy (development branch), kernel 2.6.22-13-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.22-13-generic
quiet
savedefault
boot


title		Ubuntu gutsy (development branch), kernel 2.6.22-13-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-12-386 root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-386
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-12-386 root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.22-12-386

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.22-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu gutsy (development branch), kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu gutsy (development branch), kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu gutsy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

END SNIPPET ------------------------------------------------------------------------

My first problem is that I can only boot from 2.6.20-15 kernel (which was the one that I installed from the liveCD), the latter ones (2.6.22-12 and 2.6.22-13) give me the "Error 15: File not found, press any key to continue" error.

My second problem is that on my grub - I cannot access my OS on the sdb drive - I have to use the Grub CLI to boot the sdb drive. (I can attach the snippet which points to my sdb drive in the menu.lst file).

I have tried booting from the CLI, reinstalling the Grub, changed the device.map file (for the second problem), but none of them seem to work.

All help is greatly appreciated.

Thanks,
DB

---

### Post by Pumalite on 2007-10-07
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by dhavalbbhatt on 2007-10-07
Thanks Pumalite - but I did try everything on that post. I am beginning to believe that the files /vmlinuz and initrd files are corrupt for whatever reason. Is there a decent way to remove them and reinstall those files?

Thanks,
DB

---

### Post by Pumalite on 2007-10-07
You are going to need better help than I on that.

---

