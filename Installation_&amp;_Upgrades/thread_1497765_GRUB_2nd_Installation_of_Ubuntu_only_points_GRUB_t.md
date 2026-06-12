---
title: "GRUB: 2nd Installation of Ubuntu only points GRUB to the later"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by marty1011 on 2010-05-31
Hello. I was installing command-line-only version of Ubuntu from alternate cd. I already have an existing standard Ubuntu installation on a separate partition. Both installations share the same /home partition. When asked to choose the /boot partition, I provided the /boot partition that was used by my previous standard installation. Now that installation has finished successfully, when I try to boot, GRUB only points to the later installation (no X). Is there a way to point GRUB to my first installation as well?

Here is my partition scheme:

sda1(primary) - windows
sda2(primary) - windows recovery
sda3(primary) - Ubuntu (lucid standard root)
sda4(extended) -
sda5(logical) - /boot
sda6(logical) - unallocated
sda7(logical) - Ubuntu (lucid command-line root)
sda8(logical) - /home

I have not upgraded to GRUB 2 from legacy yet.

Thanks a lot in advance. I really appreciate your help.

---

### Post by oldfred on 2010-05-31
You cannot share /boot as the files are identical and can only point to one install. There is not much advantage to a separate /boot anyway for standard desktop use. Only if you have a old system that requires the boot files to be at the beginning of the drive, or running raid or other special (not standard desktop) configurations.
You may be able to share /home as long as the versions are identical but it is always better to create /data and move the data files into /data and link that back to each install.

Several version's ago I created a separate /boot but then realized I really wanted a separate /grub. So I move boot back. With grub2 I do not see much advantage to either for most.


Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

---

### Post by marty1011 on 2010-05-31
Solved the problem by reinstalling the standard Ubuntu. One last question, how do I enter the second installation in grub2? I already have the standard installation in grub2.

[B]Edit: Found solution to this question. These links helped a lot. Thanks
[https://wiki.ubuntu.com/Grub2#Automatic%20Entries]("https://wiki.ubuntu.com/Grub2#Automatic%20Entries")
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")[/B]

---

