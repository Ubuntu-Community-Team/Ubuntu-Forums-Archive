---
title: "RAID 1 with Vista"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by rampage on 2008-11-13
This issue is driving me insane and I hope someone can help me out with it

I have:
1x 250GB SATA II (JBOD) Drive with my Operating systems on it
Windows Vista Ultimate x86
Ubuntu 8.10 x86

2x 500GB SATA II (RAID 1) Containing all my media and things I will never want to lose

When I installed Ubuntu 8.10 right from a fresh partition
Grub menu comes up but when I select any option my computer will just reboot again

I had to pop in the Vista recovery disc and do a bootrec /fixmbr to restore Vista again and of course no Grub... Any ideas on getting grub to work?

If anyone can help I would love to hear your input... Thanks Ubuntu Community rocks!

---

### Post by inobe on 2008-11-13
some reading is involved

[https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%208.10%20(Intrepid%20Ibex)%20Tips](https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%208.10%20(Intrepid%20Ibex)%20Tips)

check method 1

the alternative cd

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by caljohnsmith on 2008-11-14
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
And we can work from there if you want.

---

