---
title: "error out of disk grub rescue"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by ldouble_e on 2010-07-23
I'm getting an out of disk error and grub rescue prompt. 
It started with an update. I have to unplug my windows HDD if the mbr is being updated or it screws up my mbr. I can usually fix the problem because it loads to the grub prompt. I just do a manual boot and update the grub. However the update somehow corrupted my 2.6.32-23-generic header and I had to delete that header and revert back to 32.22-generic. Now I'm getting that out of disk error.

So I am running ubuntu lucid 10.04 on its own hard drive. sda1 is where my boot sector is located. sda2 is extended and sda5 is my swap and root is (hd0,1).

At the rescue prompt I put in the following commands:
```
ls
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
set
ls /boot
insmod /boot/grub/linux.mod
```

I get expected results all the way up to the last command. After I press enter I get "Error: out of disk". What does that mean and how do I go about fixing the problem?
I am able to get everything running using a super grub disk and having it detect any OS. That makes me think my grub is corrupted. I tried to update the grub from a live cd but got a message: is device-mapper driver missing from kernel. 

Any help is appreciated.

---

