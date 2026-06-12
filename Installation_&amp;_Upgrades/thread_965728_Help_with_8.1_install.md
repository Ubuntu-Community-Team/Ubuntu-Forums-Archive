---
title: "Help with 8.1 install"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by WozNZ on 2008-10-31
Hi,

I have decided to install Ubuntu 8.1 dual boot with Vista but have a problem with the install. I have a 250Gb drive with a 10gb recovery partition a 110Gb Vista partition and the rest of the disk unallocated.

When I run the install and get to the part where the partitioner is run by default it selects the Vista partition for resize. 

Reading it looks like I should select the use largest contigious free space option but when I do this the after bar just shows 100% disk used by ubuntu while before it has the recovery and vista partitions shown.

How do I make the install use the 100+Gb that is free space on my drive? I DO NOT want to lose the Vista Partition as I want that to remain as a games machine.

Thanks

Warren

---

### Post by desi_jockey on 2008-11-01
> **WozNZ said:**
> Hi,
Reading it looks like I should select the use largest contigious free space option but when I do this the after bar just shows 100% disk used by ubuntu while before it has the recovery and vista partitions shown.

How do I make the install use the 100+Gb that is free space on my drive? I DO NOT want to lose the Vista Partition....

I'm having exactly the same issue.  I already have Vista + XP dual booting with 10GB left unallocated for Ubuntu.  

Similar to Warren, when I select use the largest continuous free space (which is what I have successfully used to install previous versions of Ubuntu), the post partitioning diagram shows the same as a fully guided install.

---

### Post by laney_1 on 2008-11-01
you can try to partition it manually. BUT BE CAREFUL. 

BOOT /boot (30mb)
Root / (10GB)
HOME /home (10GB)   [alter these to fit your unallocated space]
SWAP swap (1 GB) 

use the JFS file system for boot, root and home. and use the ext2 file system for swap.

install grub on /boot.

laney_1

---

### Post by desi_jockey on 2008-11-01
> **laney_1 said:**
> you can try to partition it manually. BUT BE CAREFUL. 

BOOT /boot (30mb)
Root / (10GB)
HOME /home (10GB)   [alter these to fit your unallocated space]
SWAP swap (1 GB) 

use the JFS file system for boot, root and home. and use the ext2 file system for swap.

install grub on /boot.

laney_1

What if I didnt want to create a separate home partition? I already have a partition that Vista, XP and eventually Ubuntu will share.

If I left out the home partition, will it automatically get incorporated into the root partition ?

thanks

---

### Post by WozNZ on 2008-11-01
Solved it a different way. I grew the Vista partition again so it filled the disk and then used the first option in the partitioner that allowed you to select how much of the vista partition to take.

I should not have had to hoop jump like that but have lived around computers since the early days so know you have to :)

If any people that work on the installer see this, might be worth cleaning up the flow here as it might put people off. Ubuntu is meant to be Linux for humans so best not to put people off at the first gate :)

Anyway, this post is the first from my fresh Ubuntu install.

---

### Post by blackened on 2008-11-01
Strange that you were able to solve it that way. In my experience dual-booting with Vista, I've always had to shrink the Vista partition first using Vista's partition manager, then use the installer to add partitions in the free space. Granted I always manually partition, so maybe the issue is only with guided partitioning.

---

### Post by laney_1 on 2008-11-01
> **desi_jockey said:**
> What if I didnt want to create a separate home partition? I already have a partition that Vista, XP and eventually Ubuntu will share.

If I left out the home partition, will it automatically get incorporated into the root partition ?

thanks

yes i believe it dose change to root.

laney_1

---

### Post by michelboutros on 2008-11-02
I also experienced the same problem. To test whether the graph is wrong or it does actually use all the disk:
-I installed Windows Xp on an 8.6GB Virtual HDD using VirtualBox. Resized the xp partition to 4 GB, and left the other 4.6, free.
-I then installed Ubuntu 8.10 using the largest continuous free space, which the graph showed that it will use all the disk.
-When it was done, i restarted the VirtualBox and I got the boot screen where i had to choose between Ubuntu and XP. I tried both, and:

The result was that Ubuntu did use the largest continuous free space (even though the graph during installation showed otherwise) and my XP partition is untouched. Now i can install it on my laptop using the largest continuous free space.

---

### Post by lisati on 2008-11-02
BTW, it's 8.10, not 8.1 - if 8.1 existed it would have been released in January '08, but because it was released in september it's 8.10

---

### Post by michelboutros on 2008-11-02
> **lisati said:**
> but because it was released in september it's 8.10

You mean in October.

---

