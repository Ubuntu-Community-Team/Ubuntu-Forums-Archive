---
title: "Reinstalling Ubuntu 12.04"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by WMichael on 2012-06-07
Currently I have ubuntu 32bit on a 100gb partition,
For some odd reason I can't extend the partition if though I have available space.

Anyway I want to reinstall ubuntu with 64bit in a bigger partition(250gb) 

Would it be possible to do it this way to avoid breaking mbr:

1. Installing ubuntu on other partition
2. deleting previous install of ubuntu and removing partition to extend new ubuntu install. 

Would this overwrite the grub2 and allow me to boot both into windows and ubuntu?

---

### Post by Basher101 on 2012-06-07
you currently ARE using grub2 to boot into both...don't worry, just reinstall it. By the way, you should consider how you will install it: if you make the automatic install, also delete your SWAP partition (because the old one will remain, so you end up with 2 swap partitions). Also be careful to[COLOR="Red"]** not**[/COLOR] touch the windows partition! 

Follow these advices and you will fine


regards

---

### Post by WMichael on 2012-06-07
I mean to say I can't uninstall ubuntu because then that deletes grub2 and messes up my mbr.

So your suggesting that I go ahead installing ubuntu on a partition then formating my old ubuntu with the swap as well.

---

### Post by Basher101 on 2012-06-07
okay let me break it down:

1. boot live cd
2. start Gparted
3. Delete old ubuntu + swap
4. install new ubuntu
5. done

grub will only mess up if you delete it without installing the new one

---

### Post by darkod on 2012-06-07
> **Basher101 said:**
> okay let me break it down:

1. boot live cd
2. start Gparted
3. Delete old ubuntu + swap
4. install new ubuntu
5. done

grub will only mess up if you delete it without installing the new one

+1

If you delete the old install and do the new one a one step, you will not leave your computer unbootable because the new grub2 will be installed also.

---

### Post by nipunshakya on 2012-06-07
And even if you mess up your grub2 by any chances, there is boot repair tool to do the repairing for you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Goodluck.
Happy Linuxing

---

### Post by WMichael on 2012-06-08
Thanks guys for the help.

---

### Post by YannBuntu on 2012-06-11
Hello
additionnal information:
if you want to uninstall any OS: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
or if you want to reinstall Ubuntu: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by ubienewbie1 on 2012-10-15
> **Basher101 said:**
> okay let me break it down:

1. boot live cd
2. start Gparted
3. Delete old ubuntu + swap
4. install new ubuntu
5. done

grub will only mess up if you delete it without installing the new one

I eventually stumbled my way past this sticking point, I think by switching from the regular USB boot (installation) stick to the UEFI USB stick and going straight to the installation menu instead of booting into Ubuntu.  The problem I was having was with step #3 above, which I first saw recommended elsewhere and later found here while looking for a workaround.

The problem is that Ubuntu wouldn't let me remove the main partition because other stuff was supposedly mounted to it. Without being able to do so, Ubuntu was still functional (and would boot, thus no reinstall prompt) despite having no swap and free space partitions.

So, for the benefit of anyone else running into that problem, does anyone have any suggestions for how to wipe out everything with Gparted in 12.04?

---

### Post by nipunshakya on 2012-10-15
> **ubienewbie1 said:**
> 

The problem is that Ubuntu wouldn't let me remove the main partition because other stuff was supposedly mounted to it. Without being able to do so, Ubuntu was still functional (and would boot, thus no reinstall prompt) despite having no swap and free space partitions.

So, for the benefit of anyone else running into that problem, does anyone have any suggestions for how to wipe out everything with Gparted in 12.04?

This is maybe because you didn't boot into Live mode, which is essential for Gparted to Delete whatever partitions your current installations have...

When you boot from your machine, the partitions gets mounted.... and there is no way you can delete them when they are mounted.. so the idea of booting into live mode is suggested so that they dont get mounted and you can delete them without any hesitations... Good Luck with gparted... hope this helps..

---

### Post by ubienewbie1 on 2012-10-15
> **WinuxUser said:**
> This is maybe because you didn't boot into Live mode, which is essential for Gparted to Delete whatever partitions your current installations have...

When you boot from your machine, the partitions gets mounted.... and there is no way you can delete them when they are mounted.. so the idea of booting into live mode is suggested so that they dont get mounted and you can delete them without any hesitations... Good Luck with gparted... hope this helps..

I actually tried it both ways with the same results.

---

### Post by darkod on 2012-10-16
> **ubienewbie1 said:**
> I actually tried it both ways with the same results.

In Gparted, if you see a keys symbol next to a partition, that means it's mounted and can't be deleted. Now, contrary to popular belief, booting into live mode itself is not enough in some cases.

If there is an existing swap partition on the hdd (and in your case there was), the live mode will mount it to use it to work faster. If this swap partition is logical (inside the extended partition), and also if the root is logical, that will make all of them blocked for deleting since they are all together in the extended partition.

In Gparted right-click the swap partition, and select Swapoff. That should remove all keys symbols. After that you can manipulate them.

Deleting the partition is not necessary if you are happy with their sizes and you simply want to reinstall. But to re-use existing partitions you have to use the manual partitioning during the installation, not the auto method. In that case, you click on every partition you want to use, then select the Change button below, and in the window that shows select what to use the partition as, and the mount point. Also whether you want to format it or not.

Since some people "get scared" as soon as you say manual partitioning, and prefer only using the auto methods, for that you need to delete the partitions first and leave the space as unallocated for the autoinstaller to use.

How you do it, is up to you. i always prefer manually because it gives you most control.

---

### Post by ubienewbie1 on 2012-10-16
> **darkod said:**
> In Gparted, if you see a keys symbol next to a partition, that means it's mounted and can't be deleted. Now, contrary to popular belief, booting into live mode itself is not enough in some cases.

Thanks for confirming that I'm not *entirely* crazy. :)

> In Gparted right-click the swap partition, and select Swapoff. That should remove all keys symbols. After that you can manipulate them.

I had done that, but I still couldn't unmount the main partition.  I did get everything working finally last night with a Mint installation (sorry, I was running out of options and patience) on the first try.  The partitioning menus are all the same, and I followed the exact same process as all the failed Ubuntu installs except for one small difference:  With the Mint install, I specified "new partition table" before applying the partitions.  Nothing that ensued seemed any different, so I'm not sure if that actually  mattered.  But, maybe the lack of a partition table previously was screwing things up, including the inability to unmount the main partition?  (If so, you'd think the manual partitioning mode would have a safeguard against proceeding like that.)

---

