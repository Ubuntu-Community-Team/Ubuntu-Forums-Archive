---
title: "Installation Failure - Grub Boot Loader"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by SeanMC on 2005-05-22
Hi, I am new to Linux and am trying to install into a partition that previously had XP Pro installed. My hard disk has two partitions one which I want to keep that has an image of my xp install in case I want to back, and the one where XP was.
I have deleted the old XP partition and allowed ubuntu to setup the partition whic it has done to;
primary ext3 / bootable
logical swap
and my existing ntfs partition

but then the installation fails because it cannot install the Grub boot loader.

Any help would be greatly appreciated. ](*,)

---

### Post by Xian on 2005-05-22
I know this sounds silly, but it has failed every time that I've ever installed it on my box -- on the first try. However, it always installs when I select the 'Continue' option after failure, goto the install menu, and choose to run the install grub process again. Might be worth a try.....

---

### Post by SeanMC on 2005-05-22
Thanks for the reply, I have re-created the partitions with a small partition for the boot loader and this seems to have worked OK.

It's a learning process I guess, very different to Windows!!

---

