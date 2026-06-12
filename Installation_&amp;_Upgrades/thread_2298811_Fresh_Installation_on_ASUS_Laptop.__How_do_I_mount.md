---
title: "Fresh Installation on ASUS Laptop.  How do I mount my other partitions?"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2015-10-13
Hello everyone :-)

I just couldn't figure out how to use the partition manager and create a bootable version with EFI on an ASUS laptop.
So I used the option "Delete Disk and Install Ubuntu 15.04".

More on that on thread :
[http://ubuntuforums.org/showthread.php?t=2298732](http://ubuntuforums.org/showthread.php?t=2298732)

It worked! However my last two partitions which I want to mount under "/home", and under "/home/username/Data" were not mounted.  I tried to do that with Gparted, but it doesn't give me the option.

What do I need to do in order to have there partitions mounted?
I would prefer a GUI solution than the terminal if that is possible.

Thanks everyone :-)

---

### Post by oldfred on 2015-10-14
I believe the gui solution is Disks, but it often sets wrong parameters.

Not really difficult to copy & paste, changing UUID or mount points to yours.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Ifaistos on 2015-10-14
Hello and thank you for your answer!

I tried the easy way first.
Disks did the job but messed up the system (I think).

Now the system boots, but when I go enter my password, I see that it is accepted and I get a black screen (like a terminal with some error) for a fraction of a second, and then I am thrown back to the password screen.

Now I can only log in via the guest session.
During the guest session I can see all the mounted partitions.
Did I "break" the system?

btw.. I maybe using only Linux for years now, but I have only basic knowledge.  So why do you prefer /mnt?
And is there a way to mount at /mnt but still see the partition "hanging" under /home/username in Nautilus?

Thanks!

Here is a small guide to the solution for someone who has the same problem with me:
[http://ubuntuforums.org/showthread.php?t=2298860](http://ubuntuforums.org/showthread.php?t=2298860)

Many thanks to the community for all their help!
Viva Ubuntu!!

---

### Post by oldfred on 2015-10-14
I use /mnt for data partitions and link all the folders back into /home.

If you want to directly see it just as one entry then you do need to mount directly to /home, but Nautilus (at least it used to) creates two entries in left panel. One with underscore at end that then does not work as you can only have one mount of a partition.

Only if you totally manually install with Something else do you have to create all the partitions you want.
I prefer to use gparted to create partitions in advance, as it seems slightly easier. but then use Something Else to select (choose) which partition is is /, swap etc. If you partition in advance it auto uses the ESP and auto finds swap, so you do not mount choose them during install.

If you have or had Windows and UEFI boot you already have an ESP - efi system partition. Generelly desktops installs do not need a separate /boot but LVM or LVM with full disk encryption does have /boot as a separate partition. With /boot as a separate partition you must be careful and delete old kernels (which you should do even if not separate partition). Many users with LVM and /boot fill /boot and system crashes. Then difficult to houseclean old kernels.

If a newer user a separate partition for /home is easier than separate data partition(s). But then you still can have a smaller / (root) which is more efficient. Only if installing a lot of large games, may you want a somewhat larger /.

---

