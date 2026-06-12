---
title: "Need help in Ubuntu installation problem"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by ahjiefreak on 2008-02-13
Hi there,

I am quite new to Ubuntu and I have  Vista installed on my laptop beforehand. 

I did a live cd installation on Feisty Fawn using Guided option.
However, later on i found out there is some problem on Ubuntu and decided to remove it.

I made a mistakes by remove the partition which contain the Ubuntu right away. When I boot up again, my pc could not load Win Vista.

It gives me Grub error 17 when I try boot up with the Ubuntu Live Cd in my cd rom.

Please help me how to recover or reboot back my windows upon power up. Appreciate alot.

Thanks.

---

### Post by R13120(1&lt; on 2008-02-13
unfortunately Microsoft no longer includes a boot CD. 
they decided that setting one side of their partition as recover would be enough,
so unless you want to buy vista new (bad idea) or try going through there customer disservice and asking for a disk (they will laugh).
i think the only way would be to install Xp and then upgrade to vista. since you have the product key  this option shouldn't cost you any thing and xp is pretty easy to come by. 

you could always make good on the warranty and save time.

---

### Post by ahjiefreak on 2008-02-13
hi

But I have my contents and stuffs in Windows vista:(

Any clue how to load the Vista back?

---

### Post by ghantoos on 2008-02-13
You could try install grub back.

Or just reinstall ubuntu Gutsy (not feisty) to boot back to your other OS.

Cheers,

---

### Post by ahjiefreak on 2008-02-13
Hi,

Could you show me how to reinstall grub back? I inserted the live cd and there is grub version 0.97 on it.

But I do not know how to proceed with them.

---

### Post by ghantoos on 2008-02-13
So that grub works, he'll need a list a boot option (in the menu.lst file)

You should create a grup bootable floopy disk while trying to figure out how to reinstall windows' bootloader..:-/

Boot into the installation liveCD, then, do not install anything: try to follow the indications on the site below:
[http://gentoo-wiki.com/HOWTO_Bootable_Floppy_with_GRUB](http://gentoo-wiki.com/HOWTO_Bootable_Floppy_with_GRUB)

You'll be able to find many howtos on this subject.

Hope this helps,

Cheers,

---

