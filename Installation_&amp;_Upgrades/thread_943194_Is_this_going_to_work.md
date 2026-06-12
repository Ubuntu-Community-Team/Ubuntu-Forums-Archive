---
title: "Is this going to work?"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by lamagy on 2008-10-10
Master Drive: 17gb XP
Slave Drive: 200gb NTFS data. free space 26gb.

i want to install ubuntu on the slave drive and run grub from master drive.

Will there be troubles installing it in a partition at the end of the secondary drive? so i have about 160gb used and wanting to install ubuntu on the remainder.

Do i need to specify where the bootloader will go on step 6 of the install or does it automatically assign it to the mbr of the master drive?

Also at the moment i'm having some 'resize operation failure' i will try another defrag and see if that cures the problem.

If that doesn't help it would creating a partition in gparted help? also what options do i chose such as ntfn,ext3? format, use on /boot, /dev and whatever options there are ont he creating new partition screen.

cheers,

Lama.

---

### Post by tommcd on 2008-10-10
Are these IDE hard drives? If yes, and the 17GB XP disk is master, and the other disk is slave, then when you tell Ubuntu to install grub to the mbr it *should* go to the mbr of the master drive as far as I know. It may give you the option of which hard disk to install to, or it may just go to the mbr of the master drive, which is fine.

 You can also switch the drives so that the 200GB drive is master and the 17GB disk is slave. Set the 200 GB drive as master, and disconnect the 17GB drive for the Ubuntu install. Then hook up the 17GB drive as slave, and add Windows to grub's menu.lst like this:
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(two)|(grub)|(drives)|(hard](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=(two)|(grub)|(drives)|(hard))
see also:
[http://ubuntuforums.org/showthread.php?p=2702832#post2702832](http://ubuntuforums.org/showthread.php?p=2702832#post2702832)
and for everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Either way will work. The advantage of disconnecting the 17GB drive and then reconnecting it as slave is that you can avoid overwriting the Windows XP mbr. So some people prefer this method.

 Ubuntu will run fine from a master or slave drive. Or from a primary or logical partition. That 26GB free space is plenty. The Ubuntu installer can partition that free space any way you want.

Here is a good guide to getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

EDIT: Either way, it is best to set the jumpers to **master** and **slave** instead of using **cable select** to set master and slave.

---

### Post by bogdan_mbe on 2008-10-17
hello,

considering that i've just solved a similar problem, i think it would be nice to write in all the similar threads i've found my solution. from the beginning i must add i was using a windows vista, on a single hdd notebook, and i was trying to install the latest lts ubuntu (8.04).

i was suggested to try to resize partitions with a third party software like gparted live, and i did. i burned a bootable cd of it and used successfully to set my partitions just the way i wanted them.

also i've tried to defrag partitions several times, but it didn't work.

so, for me gparted live was the answer.

---

