---
title: "adding grub in  already installed Ubuntu 9.10"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by surnj1 on 2010-01-11
I installed Ubuntu 9.10 from a liveCD and I did not install Grub using advance option in the installation.

How do i install grub 2 to the Ubuntu partition using liveCd ?

Thanks,

surnj1

---

### Post by darkod on 2010-01-11
Do you mean you disabled installation of grub? Grub is installed by default, so unless you told it not to install, it's there somewhere. If you have more then one hdd it might be on the drive where you don't expect it to be.

You should be able to install grub2 from here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look under option 2) Using Ubuntu 9.10 live cd. You would need to execute both sections of the code because if you never had grub2 installed then you don't have grub.cfg file existing.

---

### Post by surnj1 on 2010-01-11
Yes I disabled installation of grub during OS installation.

I will try your solution and give you feed back later as I can not open the link given from my work.

Thanks,

---

### Post by oldfred on 2010-01-11
Are you intending to install grub2 to the ubuntu partition or the MBR?

I installed grub2 to the partition when I installed Karmic alpha and received warning messages everytime I updated. But it worked although they claim some changes that may move some grub files may break it. If you have two hard drives it is better to install it to the MBR.

Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

grub-setup --force /dev/sda2

---

### Post by surnj1 on 2010-01-12
Thanks for the advise
I had fedora on another partition so I added Ubuntu in its grub menu
I am fine now

Thanks,

---

