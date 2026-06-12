---
title: "Boot and run Grub from NEW hdd, not the old hdd."
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by lightbricko on 2009-12-08
Hi,

I had an installation of Ubuntu 9.04 on my old hdd. Now I installed Ubuntu 9.10 on a new hdd. I want to be able to physically remove my old hdd, but according to "Disk Utility" my old hdd is "bootable" but no the new one.

How do I make the new one bootable and run Grub from it?

(I've found a lot of threads on *reinstalling* Grub, but in this case I need to *move* it to another hdd, and maybe there is some other work to do to make the hdd bootable. That's why I posted this as a new question.)

---

### Post by darkod on 2009-12-08
As far as I know Ubuntu does not need the boot flag at all. Don't worry about it. It might be a remain of win install in fact.
The best way to check without unplugging your old drive, is to set the new drive as first in boot order in BIOS. If it boots correctly as you expect, that means the boot process from your new drive is working fine.
The next step would be to remove the old drive and check again if it works.
With multiple drives it all depends whether grub2 from 9.10 installed on the new one, or old one. Just make the change in BIOS and see how it goes.

---

### Post by lightbricko on 2009-12-08
I unplugged the old hdd. After bios, the only thing that happened was that there was a blinking cursor in the top left of the screen. (Not really in the top, actually a few lines down.) There was no error message.

Additional notes:
My Grub version is 1.97~beta4. (It does not matter to me if I need to upgrade to Grub2 or not).
The new hdd is a not a classic hdd but an ssd.

---

### Post by darkod on 2009-12-08
> **lightbricko said:**
> I unplugged the old hdd. After bios, the only thing that happened was that there was a blinking cursor in the top left of the screen. (Not really in the top, actually a few lines down.) There was no error message.

Additional notes:
My Grub version is 1.97~beta4. (It does not matter to me if I need to upgrade to Grub2 or not).
The new hdd is a not a classic hdd but an ssd.

1.97 is grub2. Are you sure you have grub at all on this SSD drive? Even if you installed ubuntu on it the grub2 might have gone to the other drive.

Boot with the LiveCD with Try Ubuntu, and in terminal run:
sudo fdisk -l

Copy the results here. This is the simple and easy way, if we can't figure it out there is more complicated boot script to run.

---

### Post by lightbricko on 2009-12-08
I have booted from the LiveCD, and this is the output from sudo fdisk -l :

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1570da15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60063   482456016   83  Linux
/dev/sda2           60064       60801     5927985    5  Extended
/dev/sda5           60064       60801     5927953+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009c4ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris


> Are you sure you have grub at all on this SSD drive?
No I am not. I have no idea about it.

---

### Post by darkod on 2009-12-08
Ok, your new 9.10 is on the 80GB SSD right?
While in the LiveCD, open terminal and run:
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Reboot without the cd and set the 80GB drive first in boot order in BIOS. See if it will work.

---

### Post by lightbricko on 2009-12-08
Now it works perfectly. Thank you darkod for helping!

---

