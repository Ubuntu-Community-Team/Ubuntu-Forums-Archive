---
title: "Install Ubuntu to an external USB disk"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by tasos_wrc on 2007-11-21
Hi guys,

I am going to buy a 120 GB hard disk. (WESTERN DIGITAL PASSPORT 120GB BLACK USB 2.0 2,5'').
Currently in home I use my company's laptop. Since I don't want to involve laptopp's HDD to any other issue except business, I was wondering if i could install UBUNTU to an external USB disk and thus bypass the internal HDD. In that case I could install anything I need for personal work.

Is there any website related or a post where i could found a solution?
I think that in some solution I found in web....I have to modify the MBA of the internal HDD (this is not allowed for me)

P.S. In laptop POINTSEC is installed...so if I can boot from USB the HDD is not enabled.

---

### Post by Opie32958 on 2007-12-02
I've been wanting to do the same thing. So far I have not been able to do it the way I really want, at least not without screwing up the MBR on the Windows drive. It's easy enough to fix but like you, I doing this on a work laptop and don't care to be messing with it that much. Have you found out anything more?

---

### Post by d-li on 2007-12-03
yes I have install it on 160 GB WD passport. It's very eassy. Just plug your usb disk to your labtop and start from ubuntu cd and when it finishes the loadind then start the setup tool. Change the target drive to usb disk. and 5 or 6 (can't remember) thre is a grub instalitation check box. Notice that it should look like (hd1,5). It's done. End of the setup just boot from usb :). on grub screen pust "e" for editing and change (hd1,5) to (hd0,5) then press "b" to boot. after login screen open terminal be root. edit the grub configuration.
"nano /boot/grub/menu.lst"
and change all (hd1,5) to (hd0,5)
save and exit
All done..

---

### Post by Joeb454 on 2007-12-03
Quick question :)

What if I wanted to do that on an iPod (30GB, it's then gen before the one we're on now lol)

---

### Post by Herman on 2007-12-03
Hello, tasos_wrc
I suggest making a backup of your MBR first, it will only take a few minutes, here is how to back up and restore the boot loader part of the MBR, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

---

