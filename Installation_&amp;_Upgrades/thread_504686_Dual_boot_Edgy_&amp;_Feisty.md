---
title: "Dual boot Edgy &amp; Feisty"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by titatonneke on 2007-07-19
Hello,

I'm experimenting with Ubuntu. I want to make a dual boot system using Edgy and Feisty. Can someone tell me the best way to organize the partitions? I have a 160GB harddisk and i was thinking to make the following partitions: 500MB swap, 10GB root (Edgy), 10GB root (Feisty) and the rest /home. 

Is it possible to have the same home folder for a user in both edgy and feisty?

Will the bootloader get messed up if i re-install one of the installations or do i need a /boot partition for this?

---

### Post by Herman on 2007-07-19
Hello titatonneke,
It's fun to experiment with Ubuntu and other Linux distros and try different partitioning arrangements. :)

I have tried all sorts of combinations like that and sure, it's possible to install with a shared /home for Edgy and Feisty, just mount the same /home partition when you install. 
If you have files there already, don't format it. It would be better not to put files in there yet though, (you would have backups of all your files on separate media as well, of course),  and then you could just let the second installation run it;s natural course and reformat the /home partition. Then move your files in after both installs are complete. :)

You shouldn't have any trouble booting, whichever Ubuntu you install second will  install GRUB's IPL to MBR and  it should automatically detect the other Ubuntu thats there already and include an entry in the GRUB menu for it. :) 

A "separate /boot partition" means one that has GRUB in it plus the Linux kernel and other files that are part of one of your operating systems.
A "dedicated GRUB partition" is a separate partition that just has GRUB in it and not any files that belong to one OS or another, so your GRUB will be operating system independant. That can be a good idea, I think that's the kind of thing you probably meant.
It is possible, but complicated, to have a "shared /boot partition". I can tell you how to do that, but I wouldn't recommend it except for having fun experimenting. Your menu.lst file from your second install and some other /boot files will overwrite other files from the first install  that have the same name. However, for fun, it can be worked around, ask me if you want, but again, not ideal for the average user.   :)

Actually, it would be better to have one single install for Edgy and another single install for Feisty and forget about /home partitions too, as far as having a useful and stable installation go, but we're not talking 'practical' here, we're talking about having fun, right? :)

Your partitions are okay size-wise, I recommend at least 5.0 GB for root, and you have a nice big hard drive, 10 GB for root each will allow you to install a lot of software, I don't think you'll be able to fill those up. That's fine, too much is better than not enough. :)

Have fun. regards, Herman :)

---

### Post by titatonneke on 2007-07-19
Hey Herman,

Thanks for your reply. I've been using Ubuntu for a while and i really like it. I've got an old computer on which i'm gonna play with different linux distro's to learn more about them. it's not my primary system, so it's ok if it gets messed up once in a while.

---

### Post by Herman on 2007-07-20
That's a great idea, you'll really be able to learn a lot more that way.
Regards, Herman :)

---

