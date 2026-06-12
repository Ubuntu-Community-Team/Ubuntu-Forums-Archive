---
title: "Ubuntu partition &quot;not bootable&quot;"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by kafpauzo on 2007-11-10
I just installed Ubuntu from CD. Now when I try to boot from the newly installed HD partition, my boot loader says that the partition is "not bootable". How can I make it bootable?

Should I give more information? I installed Ubuntu 7.10 from the regular desktop CD for AMD64. I have 4 GB RAM and a couple hundred GB HD on two drives.

I did not use the Ubuntu installation tools to create partitions. I already had a lot of partitions, which I arranged quite some time ago when the computer was new. Thus I installed Ubuntu on a partition that already existed.

I've never seen this problem when I've installed Windows on these partitions, so my boot loader (boot-selection program) seems to be working fine, and it seems I know how to use it correctly.

During the Ubuntu installation I unchecked "Advanced" / "Install boot loader". Does this make the Ubuntu disk non-bootable?

I assumed that "boot loader" means the program that you use to select which system to boot. I don't expect "boot loader" to mean something that makes the partition bootable. In other words, if I had left "Install boot loader" checked, I suppose my current boot-selection program would have been replaced with a new boot-selection program. I do *not* want that replaced.

The partition where I installed Ubuntu has 20 GB. I chose ReiserFS -- but surprisingly my boot loader still thinks it's a FAT partition. Maybe this has something to do with what happened before installation. I had to format the partition as FAT, because the Ubuntu live CD died during CD boot when I tried with the HD partition unformatted, but worked correctly once the HD partition was formatted (which I found very odd, an OS installation CD should boot regardless of HD partition formatting). Thus during the Ubuntu installation the partition was formatted again, this time for ReiserFS. I would expect this to also change the byte that indicates the partition type, but it still says FAT. Should I change this byte? If so, what should I select?

Or if that isn't the solution, is there some tool I can use to make the partition bootable?

By the way, my first impression of Ubuntu on the live CD was very positive indeed, so I really hope you can help me get it to work!

---

### Post by mocqueanh on 2007-11-10
Okay, i suppose after install Ubuntu, you cant boot into Ubuntu, and you only can boot into Windows as usual previously.

During Linux installion, you have to let Linux distro install boot loader ( GRUB, or LVM, but GRUB is popular ). Boot loader is a small program, it installed in your MBR, MBR is the firt partition of your HDD, let you boot in to OS.

After this, you will have a boot menu, let you choose which of OSes in your PC to boot in.
Dont worry, Ubuntu boot loader will discover your Win partition and let you choose boot from Win or Linux in the boot menu.

I'm using Xubuntu alternative, the alternative CD has a option: Rescue broken system > Reinstall GRUB, i can reinstall my GRUB boot loader here, when i reinstall Windows, or if i miss install GRUB like you.

I dont use Live CD like you, so i dont know how to reinstall GRUB using Live CD, i think you should reinstall Ubuntu.


Or, i think if you have Hiren Boot CD, Ultimate boot CD, these CDs have MBR (Master boot record) tool, let you restore your boot loader, you can make new boot loader (not GRUB - boot loader of Linux )



P/S: during Windows installion, Win auto install itself boot loader without ask you, and the Win boot loader only discover other Win OSes, it dont know Linux OS, and you dont have Linux option in Windows boot menu.
Of course, Microsoft developer can make their Windows discover Linux, but they dont. Because their business ethic (i think so), they need money as much as possible

---

### Post by kafpauzo on 2007-11-10
Thanks for the reply! You helped me get on the right track, I have now found descriptions of what to do.

It wasn't clear to me that Linux needs a special boot loader in addition to my boot loader.

In case you're interested, on my machine the Ubuntu boot loader cannot detect my Windows partition the way you said, because the Windows partition is completely hidden. You see, my boot loader uses a special trick that allows you to have any number of boot alternatives. The loader re-writes the MBR as needed for each boot alternative. When I boot from one partition, all the other boot partitions are completely hidden, because they are not included in the MBR for that boot alternative. This has lots of advantages!

Thus I can't just replace my boot loader with Ubuntu's boot loader. But according to the descriptions I've found, at least one Linux boot loader doesn't need to reside in the MBR, and can instead be in the Linux root partition, where it can be invoked by my boot loader.

I haven't installed this yet, because suddenly I have to run. But first I wanted to thank you for putting me on the right track!

---

### Post by hotweiss on 2007-11-11
See if this guide helps you:

[http://jguk.org/2007/11/master-boot-record-mbr-fix-for-laptop.html](http://jguk.org/2007/11/master-boot-record-mbr-fix-for-laptop.html)

---

