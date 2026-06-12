---
title: "making GRUB (or GRUB 2) the default"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by ffej2ffej on 2011-11-25
I bought a used computer with Win Vista (!) on it.  I installed UBUNTU and had a perfect dual-boot machine.  
After using it a while, I realized what a piece of Microsoft windoze vista is.  I downloaded and installed Windows XP and it works fine.
The problem is that the installation of UBUNTU I had before is still there but the machine boots to Windows with no prompt or menu or anything.
I also tried to boot from an UBUNTU install disk in hopes that I could find a utility within Linux to set this option for me.  If there is such a utility, I did not find it.
While booted from the install disk, I tried apt-get remove grub-pc followed by apt-get install grub-pc.  Didn't work.](*,)

---

### Post by darkod on 2011-11-25
You only need to reinstall grub2 to the MBR of the disk.
Boot again with the ubuntu cd in live mode, open terminal and run:
sudo fdisk -l (small L)

That will list the partitions. There should be two for ubuntu (at least), one of linux type and the other linux swap. Note down the name of the linux partition, for example it will be /dev/sda5.

In case it's not sda5 just change the number 5 with what is correct.

You reinstall grub2 to the MBR from live mode with:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

As I said, in the first command change the 5 if your ubuntu partition is another number. Don't change anything else.
Reboot and it should be fine. First time the grub2 menu will probably say Vista, boot ubuntu once and simply run in terminal:
sudo update-grub

That will detect the XP and change the entry in the boot menu.

---

### Post by ffej2ffej on 2011-11-25
First of all, I wish to express my sincere thanks to Darkod for his quick and accurate reply.  Your response worked beautifully and I now have my dual-boot computer back where it was.
Second of all, if I could figure out how to mark this thread as solved, I would.  (Did I take an *extra *stupid pill today?*)*

---

### Post by drs305 on 2011-11-25
Welcome to the Ubuntu Forums.

You mark a thread SOLVED via the 'Thread Tools' link at the top right of the original post.

Happy Ubuntu-ing !

---

