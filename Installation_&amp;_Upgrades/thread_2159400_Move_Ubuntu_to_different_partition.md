---
title: "Move Ubuntu to different partition"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by bvm1228 on 2013-07-03
I am new to Linux and when I installed Ubuntu from my USB Drive, the installation seemed to put my install of Ubuntu into a different partition than the one that I made for it. When I installed it I clicked "Install alongside Windows 8" put it never seemed to give me an option to pick the partition to install it on. So how do I move it to the partition that I made for it?

---

### Post by dino99 on 2013-07-03
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by grahammechanical on 2013-07-03
You cannot move Ubuntu to another partition. Each partition has it own unique identifying number and Ubuntu is keyed to the UUID of the partition it is on. If you copy and paste Ubuntu to another partition you will not be able to boot it. You should have used the Something Else option. That lets you choose partitions to install into. By selecting to install alongside Windows you told the installer to make its own space where it could.

You basically need to remove Ubuntu and re-install using the Something else option. Linux Secure Remix has an OS-remover tool and a boot repair tool. You will need to repair the boot system otherwise Windows will not load.

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You then need to remove the partition that Ubuntu is on at present by resizing other partitions and you can reinstall Ubuntu where you want to using the Something Else option.

It may be possible to resize and move the present partitions to get Ubuntu where you want it. But where ever the partition is, it makes no difference in the long run. Uses Windows tools to resize Windows partitions. Use Gparted to move-resize Linux partitions.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You might want to run Gparted from the live session and give us a screen shot of your partitions. Then you may get more detailed advice.

Regards.

---

### Post by Mark Phelps on 2013-07-03
If you shrunk the Win8 OS partition as a side effect of installing Ubuntu, there is a very strong likelyhood that it won't boot anymore.  If I was you, I'd try booting into Win8 to confirm that it still boots and still works.

---

