---
title: "How to install Ubuntu 10.04 and Winows 7 dual boot with seperate hard drives?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by ThatPerson on 2010-06-21
Hi,

I'm a n00b at dual booting and I plan on installing Ubuntu 10.04 on a separate hard drive than my Windows 7 64 bit one in a dual boot situation. I have read that you can do this by unplugging the Windows hard drive, install Ubuntu on the other one, and than plug the Windows hard drive back in and everything will be fine and dandy. Is this correct? If it is, will I have to manually set the Primary and Secondary drive (in the BIOS I think?:-k), or will it automatically do that.

Thanks,
ThatPerson

---

### Post by wilee-nilee on 2010-06-21
This link should be helpful.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Mark Phelps on 2010-06-22
> **ThatPerson said:**
> Hi,

I'm a n00b at dual booting and I plan on installing Ubuntu 10.04 on a separate hard drive than my Windows 7 64 bit one in a dual boot situation. I have read that you can do this by unplugging the Windows hard drive, install Ubuntu on the other one, and than plug the Windows hard drive back in and everything will be fine and dandy. Is this correct? If it is, will I have to manually set the Primary and Secondary drive (in the BIOS I think?:-k), or will it automatically do that.

Thanks,
ThatPerson
Wilee-Nilee provided you a good link for details, but the simple answer is that, after you reconnect the Windows drive, continue to boot from the Ubuntu drive.  Once in Ubuntu, it is a simple matter to have the GRUB menu updated to automatically add an entry for MS Windows.

What you're doing by disconnecting the MS Windows drive is the best approach because it prevents the problem some folks have had when they accidentally installed GRUB to the MS Windows boot partition.

---

### Post by ThatPerson on 2010-06-22
Thanks for the reply, but how exactly would I update the GRUB menu to recognize Windows?

Thanks,
ThatPerson

---

### Post by darkod on 2010-06-22
Personally I advocate to learn few basic things about bootloaders, instead of taking the easy way out and removing hardware. Sooner or later you need to learn.

But to answer your direct question, once both disks are connected again and you boot into ubuntu, in terminal just run:

sudo update-grub

If you pay attention during the install there is NO WAY to put grub2 anywhere except where you want it. Whether you know or want to learn where does it go and how does it work, that's a different question. :)

---

### Post by ThatPerson on 2010-06-22
> **darkod said:**
> Personally I advocate to learn few basic things about bootloaders, instead of taking the easy way out and removing hardware. Sooner or later you need to learn.

But to answer your direct question, once both disks are connected again and you boot into ubuntu, in terminal just run:

sudo update-grub

If you pay attention during the install there is NO WAY to put grub2 anywhere except where you want it. Whether you know or want to learn where does it go and how does it work, that's a different question. :)

Thanks for the quick reply! I guess I should learn about boot loaders, but for now I'm just getting started in Linux so I guess I'll take the easy way out \\:D/ .

---

### Post by darkod on 2010-06-22
> **ThatPerson said:**
> Thanks for the quick reply! I guess I should learn about boot loaders, but for now I'm just getting started in Linux so I guess I'll take the easy way out \\:D/ .

No problem, just don't think you can avoid learning various things much longer. ;-)

---

