---
title: "how will Grub react if i add a new partition"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by b166er on 2008-11-20
Hi

I'm currently running a dualboot between fedora7 and ubuntu hardy.

my partitions look something like this:

sda:
------
    Fedora 7
    Ubuntu
    Swap
    free space
------

I have one copy of Grub installed in the Mbr of sda, and one copy of grub on sda2 (the Ubuntu partition).

So on boot I first come to the "fedora installed grub" (sda), and that takes me to the "ubuntu installed grub" (sda2) that then boots ubuntu.

I know it seams strange, but it works!

What I plan to do now is to remove the swap partition and make a litle bit bigger partition, and put win-xp on it.

I know from experience that messing about with the parttions can mess up Grub. something with it stopping at stage 1.5

so what kind of problems can I expect?
I suppose there will be a bunch of them =)

---

### Post by dstew on 2008-11-20
Grub should not care as long as you don't change or move any of the partitions that it uses, or make new a new partition with a lower number. So, if /dev/sda3 is your swap partition, and you delete it and create a new /dev/sda3, it should not bother grub, as long as you don't move the first two partitons.

You will have much more trouble trying to install Windows into the third partition. It will want to go into the first partition. I am not sure how you can get around that. If you end up creating a new /dev/sda1, and the Fedora and Ubuntu paritions get re-numbered to /dev/sda2 and sda3, then grub will be broken.

---

### Post by b166er on 2008-11-25
ok what i did was to use an old hdd that had windows installed on it.
(it was previously used on this machine)

Then I used Ghost to clone the old partition to my sda2 partion and then added it in grub.
This worked flawlessly.

---

