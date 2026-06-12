---
title: "installation of 10.04 succeeds but does not boot"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by vsubrama on 2010-06-03
I installed desktop version 10.04 from livecd. I have Windowsx XP already and decided to use dual boot. install was successful, however after rebooting i got the "Grub Rescue" and it does not recognize any commands excelt Ls....

I did run the boot info script and attached is the results file

i tried re-installing ubuntu as well as tried re-installing grub however no change...i still end up with same problem. please advise

---

### Post by darkod on 2010-06-03
Just to see if it works, boot into live mode again and in terminal try:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Make sure in BIOS you are booting from the ubuntu disk, it should be first choice in hdd boot order.

Because you didn't delete the partitions of the first install, you actually have two install now. Even if the above procedur works and you can boot and use ubuntu, I suggest to delete all four partitions (two installs with two partitions each), and make a new install to use the space.

---

