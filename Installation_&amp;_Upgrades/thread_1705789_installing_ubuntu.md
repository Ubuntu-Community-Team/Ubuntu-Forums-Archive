---
title: "installing ubuntu"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by bob321 on 2011-03-12
hello,

I'm am installing ubuntu *right now* so I need your help with this right now please.
I am in the step 5 of the installation, in which I am asked where to  install ubuntu. I have already 2 OS (xp, 7) and would like to install  ubuntu in whatever space there is left in the drive (roughly 15GB that I  made with gparted).
Selecting the free space isn't enough though. I think I have to set some  flags or add a swap or something but I'm afraid to mess it up.
The error displayed is 'no root file system is defined. please correct this from the partitioning menu."
The drive I want to install it on looks like:
device       | type | mountpoint | format? | size | used
/dev/sdb     |      |            |         |      |
  /dev/sdb1  | ntfs |   -        |    -    |140   |50      (this is 7)
  free space |-     |-           | -       |15    | -      (this is where I want to install ubuntu + swap)
  /dev/sdb2  | ntfs |-           | -       |75    |50      (this is xp)

I think I'd like to have a partition for /, swap and /home. This makes it 5 partitions
How can I make an extended partition ?
Is it the same as "logical" partition ?

thanks a lot.

---

### Post by kagerato on 2011-03-12
No root filesystem indicates your current partioning scheme includes no partition for "/", the root of the filesystem tree.  You need to create one, select a filesystem (such as ext4) for it, set the mountpoint to "/", and then format it.

As to extended and logical partitions, they're related but not identical.  Logical partitions exist inside of extended partitions.  You can create an arbitrarily large number of logical partitions inside an extended partition.

When you need more than four partitions on a single disk, you have no choice but to create an extended partition and some logical partitions inside of it.

---

### Post by XsheepX on 2011-03-12
Format that 15gb of space as a new ext4 partition, and set the "Mount Point" to "/"

It should then allow you to proceed.

Since you're a new user, don't worry about the swap much for right now. It should automatically give you a relative amount of swap anyway. If you really wanted to extend it, you could do that while already inside Ubuntu later.

---

### Post by bob321 on 2011-03-12
okay.  So I'm at step 10 now, and I am asked if I want a boot loader.  I actually noticed that it wants to install it into sda, but the drive  that contains the seven and xp OSes and where ubuntu is supposed to be  installed is sdb. This is weird right ?
By the way why would the drive sdb not be named sda, since this is where the systems are ? Can I change that ?

Thanks

---

### Post by XsheepX on 2011-03-12
> **bob321 said:**
> okay.  So I'm at step 10 now, and I am asked if I want a boot loader.  I actually noticed that it wants to install it into sda, but the drive  that contains the seven and xp OSes and where ubuntu is supposed to be  installed is sdb. This is weird right ?
By the way why would the drive sdb not be named sda, since this is where the systems are ? Can I change that ?

Thanks
 			It's asking which partition you want to be installed as the boot loader, so it shouldn't matter. Choose whichever one you want to be the default OS when you startup your machine.

---

### Post by bob321 on 2011-03-12
Are you sure that's what it's asking? Isn't it asking on which drive to put grub ? That could be a problem if I remove sda, which is just a data drive, whereas sdb is the system.
Why did the kernel chose to name the system sdb ?
Wouldn't it be more logical to name it sda ?
What will happen if I remove the sda drive, which I might do someday given that it's just a data drive ?

thanks

---

### Post by XsheepX on 2011-03-12
> **bob321 said:**
> Are you sure that's what it's asking? Isn't it asking on which drive to put grub ? That could be a problem if I remove sda, which is just a data drive, whereas sdb is the system.
Why did the kernel chose to name the system sdb ?
Wouldn't it be more logical to name it sda ?
What will happen if I remove the sda drive, which I might do someday given that it's just a data drive ?

thanks
I'm pretty positive it's asking which partition to begin with on that drive. When you install Ubuntu 10.10, it should completely reinstall GRUB, which is why it's asking.
As for why it's sdb, I have no idea, it may have something to do with the fact that you already have two other OS installed first in one hard drive. If you removed the sda drive, I'm not sure what would happen. I know it wouldn't show up in any of your OS unless you mounted it to view it, which could be bothersome to have to do at each startup.

---

### Post by Hedgehog1 on 2011-03-12
> **bob321 said:**
> hello,

I'm am installing ubuntu *right now* so I need your help with this right now please.
I am in the step 5 of the installation, in which I am asked where to  install ubuntu. I have already 2 OS (xp, 7) and would like to install  ubuntu in whatever space there is left in the drive (roughly 15GB that I  made with gparted).
Selecting the free space isn't enough though. I think I have to set some  flags or add a swap or something but I'm afraid to mess it up.
The error displayed is 'no root file system is defined. please correct this from the partitioning menu."
The drive I want to install it on looks like:
device       | type | mountpoint | format? | size | used
/dev/sdb     |      |            |         |      |
  /dev/sdb1  | ntfs |   -        |    -    |140   |50      (this is 7)
  free space |-     |-           | -       |15    | -      (this is where I want to install ubuntu + swap)
  /dev/sdb2  | ntfs |-           | -       |75    |50      (this is xp)

I think I'd like to have a partition for /, swap and /home. This makes it 5 partitions
How can I make an extended partition ?
Is it the same as "logical" partition ?

thanks a lot.

bob321,

I cannot tell if you completed your install.  You have been given some conflicting advice.

If you want to take a breather, back out of the install and plan it with us first, we can help.

For the record, an extended partition is a 'container' that holds Logical partitions:

[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]

You can see there are two logcal partitions in the extended partition in the picture.

If you want to plan the install (or need to reinstall), please:

Boot from the LiveCD/LiveUSB, select 'TRY' and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

