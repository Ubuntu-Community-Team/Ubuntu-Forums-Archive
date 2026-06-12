---
title: "Grub question for tribooting Gutsy/Vista/Hardy"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by andrewsomething on 2008-01-29
So I went ahead and created a new partition on my drive to install Hardy for bug testing purposes. The install went smooth and grub works, but I've got some questions. 

First off here's a map of my drive:

Gutsy sda3 <-> swap  sda4 <-> Vista sda2 <-> Hardy sda1

Now, grub was automatically reinstalled when I installed Hardy. What is that going to mean to me? 

If I upgrade the kernel for Gutsy will I have to add it by hand to the menu.lst in Hardy's /boot/grub/?

If I wipe the wipe the Hardy partition how do I return to using the Gutsy grub? Reinstall from a live cd? The info's all still there in Gutsy's /boot/grub/

Any one got any ideas or tips for what I'm doing? No problems yet, I just want to make sure I can fix any thing before it happens.

Thanks!

---

### Post by confused57 on 2008-01-29
> **andrewsomething said:**
> So I went ahead and created a new partition on my drive to install Hardy for bug testing purposes. The install went smooth and grub works, but I've got some questions. 

First off here's a map of my drive:

Gutsy sda3 <-> swap  sda4 <-> Vista sda2 <-> Hardy sda1

Now, grub was automatically reinstalled when I installed Hardy. What is that going to mean to me? 

If I upgrade the kernel for Gutsy will I have to add it by hand to the menu.lst in Hardy's /boot/grub/?

If I wipe the wipe the Hardy partition how do I return to using the Gutsy grub? Reinstall from a live cd? The info's all still there in Gutsy's /boot/grub/

Any one got any ideas or tips for what I'm doing? No problems yet, I just want to make sure I can fix any thing before it happens.

Thanks!
You could add a configfile entry to your Hardy menu.lst to boot Gutsy:
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)
something like:
```
title  Gutsy on sda3
configfile  (hd0,2)/boot/grub/menu.lst
```

Another possibility would be to reinstall Gutsy's grub IPL to the mbr, using the live cd, and add a configfile to boot Hardy:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

```
title  Hardy on sda1
configfile  (hd0,0)/boot/grub/menu.lst
```

With a configfile boot entry, you wouldn't need to manually change the entry in case of a kernel update.

---

### Post by andrewsomething on 2008-01-29
Thanks, I hadn't heard of this method before. It sounds like just what I want.

---

### Post by andrewsomething on 2008-01-30
Thanks again!

Works perfectly. I restored the Gutsy grub to the MBR and added the Hardy configfile.

Here's a tip for any one else trying this: Since the MBR isn't actually broken in this case, and you can boot into Ubuntu, you can do this all with out going to a LiveCD. Seems obvious, but every guide I've ever seen about reinstalling grub assumes you can't boot into Ubuntu. It'll save you a few minutes.

---

