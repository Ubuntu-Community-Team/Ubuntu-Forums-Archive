---
title: "Installing Windows"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Woodsyx on 2008-05-29
Ok I am currently running Ubuntu 8.04 and for various reasons I need to be able to boot into Windows. The hard drive is currently formatted in ext3 and the Windows XP install disk can't see this. Is there any program that allows me to boot with it(live CD) and partition my drive or just reformat the whole thing.

Thanks

---

### Post by SkonesMickLoud on 2008-05-29
Boot into [GParted](http://gparted.sourceforge.net/).

---

### Post by Woodsyx on 2008-05-29
*slaps forehead* I was just at that site I feel stupid for not seeing the LiveCD.

---

### Post by tommcd on 2008-05-29
Here are your options:
1) Boot up a gparted of parted magic live CD. These let you create, delete, or resize partitions. As far as I know Windows likes to be on the first partition on the disk; and it must be a primary partition. So you would have to shrink your Ubuntu partition with gparted/parted magic and create free space in the front of the disk to install Windows to.
2) Start over. Boot up the Windows install CD, delete all partitions (if you have /home on a separate partition you could probably save that). Make sure you have enough room after deleting partitions (minimum 10GB each for Windows and Ubuntu's / partition, and some for swap. Install Windows first to the first primary partition, leaving room for Ubuntu. Then boot up Ubuntu and install it, including swap, to the rest of the space. Put grub on MBR, and you're done.

---

### Post by Pumalite on 2008-05-29
This might help too:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by ans5685 on 2008-05-30
You don't have to free space from the beginning of a partition!!!!
Windows xp and vista can install and boot from any partition primary or logical.
Just fire up the parted magic or gparted livecd and free up some space from the end of the last partition of your drive, its easy just slide the slider to the left of the selected partition,select apply changes and wallah you have free space (size according to your needs).
Then instead of creating a new partition boot into the windows installation cd and tell it to use the freespace.
The final thing you'd need to do after installing windows is reinstall Grub or you won't be able to boot into Ubuntu.

---

### Post by tommcd on 2008-05-30
> **ans5685 said:**
> You don't have to free space from the beginning of a partition!!!!
Windows xp and vista can install and boot from any partition primary or logical.


Just curious, but have you ever installed XP to a logical partition? I have read many times that XP must be installed to a primary partition. Some examples:
Post #2 of this thread:
[http://www.linuxquestions.org/questions/linux-newbie-8/mbr-problem-no-xp-load-after-ubuntu-7.1-install-640268/?highlight=install+windows+logical+partition](http://www.linuxquestions.org/questions/linux-newbie-8/mbr-problem-no-xp-load-after-ubuntu-7.1-install-640268/?highlight=install+windows+logical+partition)

Post #3 of this thread:
[http://www.linuxquestions.org/questions/linux-software-2/reinstall-windows-xp-in-triboot-system-can-i-have-as-many-partitions-as-i-want-635269/?highlight=install+windows+logical+partition](http://www.linuxquestions.org/questions/linux-software-2/reinstall-windows-xp-in-triboot-system-can-i-have-as-many-partitions-as-i-want-635269/?highlight=install+windows+logical+partition)

And the first post of this thread:
[http://www.linuxquestions.org/questions/general-10/primary-partitions-628905/?highlight=install+windows+logical+partition](http://www.linuxquestions.org/questions/general-10/primary-partitions-628905/?highlight=install+windows+logical+partition)

If you search you will find lots more. That is why I thought XP had to go on a primary partition. I have never tried it any other way. Have you? If XP does not need a primary partition, then this is indeed a popular myth.

---

### Post by Pumalite on 2008-05-30
I think that Herman has been able to boot Windows from a logical partition, but I have not learned to do it. I think it's complex. The best installation is with Windows in a primary partition, preferably sda1, installed first. Ubuntu should be installed last. It can boot from a logical partition.

---

