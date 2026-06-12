---
title: "GRUB Error 18"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by winniedemon on 2008-11-03
I recently got a new 250GB hard drive for my Dell Inspiron 6000, and want to set up dual boot with Windows XP and Ubuntu 8.10

I installed Windows first on a 150GB partition (I didn't realize Ubuntu could shrink partitions) and got that working. I then put in the Ubuntu CD, and made 2 new partitions, 60GB ext2 for my root directory (is there any merit to choosing other formats?) and 3GB for swap, leaving me with ~30GB unallocated.

After I installed Ubuntu, I restarted my computer and got GRUB error 18. I've read that this sometimes occurs when things exceed 137GB, but I have no idea how to fix this problem.

Thanks in advance for your help!

---

### Post by renzokuken on 2008-11-03
one option would be to use the livecd and gparted to shrink the partition in question, and the reinstall grub (should be a guide somewhere)

heres an example

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but make sure you know which disks/partitions are which on you setup first.....e.g. change hd0 to the correct drive

---

### Post by winniedemon on 2008-11-03
> **renzokuken said:**
> one option would be to use the livecd and gparted to shrink the partition in question, and the reinstall grub (should be a guide somewhere)

heres an example

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but make sure you know which disks/partitions are which on you setup first.....e.g. change hd0 to the correct drive

But simply shrinking the partitions to fit within 137GB would defeat the purpose of buying a new hard drive in the first place. I'd like to keep my partitions as specified (that is, Windows at 150GB, Ubuntu at 60GB, and ultimately use the leftover as a shared drive).

Is there a way to put what GRUB needs at the beginning of the disk so I can preserve everything else?

---

### Post by renzokuken on 2008-11-03
well i've just done a bit of reading and it seems you need to have the linu kernel in the first 1023 sectors of the harddrive........not overly sure how to do this though personally but i bet its very hard to do successfully without screwing your XP install

my personal suggestion would be to start from scratch and use a different partitioning scheme.

e.g.

15gb Windows
15gb Ubuntu
1gb Swap
then the rest as a large storage area that is accessible (ntfs-3g?) from both OSs

if you dont fancy reinstalling windows.....maybe scratch the ubuntu install, reduce the XP partition right down and then install ubuntu in the remaining space.

---

### Post by caljohnsmith on 2008-11-03
> **winniedemon said:**
> 
Is there a way to put what GRUB needs at the beginning of the disk so I can preserve everything else?
Unfortunately, just putting Grub at the beginning of the disk is not enough; you also have to put all of Ubuntu's boot files within reach of BIOS, so that means the entire /boot directory. You could use Ubuntu's partition editor gparted to shrink your Windows partition at its beginning by ~200 MB, and then create a ~200 MB /boot partition at the front of your drive. If you the reinstall Ubuntu, all you have to do is specify that first 200 MB partition with a /boot mount point, and you should hopefully be all set. Let me know how it goes or if you run into trouble. :)

---

### Post by winniedemon on 2008-11-04
> **caljohnsmith said:**
> Unfortunately, just putting Grub at the beginning of the disk is not enough; you also have to put all of Ubuntu's boot files within reach of BIOS, so that means the entire /boot directory. You could use Ubuntu's partition editor gparted to shrink your Windows partition at its beginning by ~200 MB, and then create a ~200 MB /boot partition at the front of your drive. If you the reinstall Ubuntu, all you have to do is specify that first 200 MB partition with a /boot mount point, and you should hopefully be all set. Let me know how it goes or if you run into trouble. :)

I ended up doing a variant of this. Since I had the free space, I figured I'd just move everything to the right by the 200MB. In retrospect, this was a poor choice because it took a long time to move everything. Either way, I reinstalled Ubuntu and everything works fine now. Thanks for the help!

---

### Post by caljohnsmith on 2008-11-04
You're most welcome, and that's great news you got it working. Cheers and have fun. :)

---

