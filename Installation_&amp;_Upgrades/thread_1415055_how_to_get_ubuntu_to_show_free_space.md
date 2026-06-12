---
title: "how to get ubuntu to show free space"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by daudiam on 2010-02-24
I have about 32 GB of free space. I have installed both Ubuntu and fedora and want to use that free space in both the flavours of linux. Its just not showing in either. Plz help. Using the latest version of ubuntu

---

### Post by darkod on 2010-02-24
If you haven't installed gparted in ubuntu, do that with:

sudo apt-get install gparted

Then open it in System-Administration and create a partition from that space in either ext4 or ext3 type.

In order a partition to be "visible" and used in linux you have to mount it. A simple way to mount it is clicking on it in Places.
In order to mount it automatically it has to be in /etc/fstab. Read more about it and how to do it here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Also there should be plenty tutorials on google.

---

### Post by daudiam on 2010-02-25
I installed gparted. But I already have 4 primary partitions. One of the primary partitions is extended, which contains another primary partition. Can I combine these 2 primary partitions into a single partition, so that I have 3 primary partitions, and I can create a new partition from the 33 GB of unallocated space that I have ?
If one of the primary partitions (other than these 2) is Ubuntu, how can I ADD THE 33GB OF UNALLOCATED SPACE TO IT. I just want to use that free space, to install another OS like Fedora for eg.. That's my primary aim

---

### Post by darkod on 2010-02-25
If you want to install another OS on it, you can't add that space to any partition. If you add it that will only enlarge the partition size for that particular OS or Data partition but you won't be able to install separate OS on it.

You can't have primary inside extended, only logical. That's probably what you have inside your extended partition.

You could post screenshot of Gparted to show things more clearly. Also, you should take into account that windows (if you have it) can only be on primary partition, so that is limiting the options.

---

### Post by cybrsaylr on 2010-02-25
As quick way is to use Terminal to show free space.

Open a Terminal and put in:
 df 
or put in,
 df -h 

to see your used and free space and your partitions.

---

### Post by darkod on 2010-02-25
> **cybrsaylr said:**
> As quick way is to use Terminal to show free space.

Open a Terminal and put in:
 df 
or put in,
 df -h 

to see your used and free space and your partitions.

If I'm not mistaken this shows the used/free space on your partitions. The OP is talking about unallocated space not belonging to any partition.

---

### Post by daudiam on 2010-02-26
i have attached a screenshot of gparted with this. This is taken with fedora (when I installled fedora, ubuntu got deleted somehow, but that's for another post). /dev/sda3 is an extended partition, which is a primary one(as a key is shown with it) In it, there is sda5 which also shows a key to its left, meaning prehaps its also a primary partition. Whatever it is, if I try to right click on the unallocated space (33 GB), and go to the new option, it tells me there are already 4 primary partitions. I only need sda5,sda1 and sda4 as my primary partition. The rest of free space I want to devote to installing ubuntu. Fedora is on sda1.

Also, when I right-click on the partitions with the key to the left, all the options, NEW, RESIZE, DELETE,etc. are all greyed out. Why is that so ?

---

### Post by darkod on 2010-02-26
The keys don't mean primary partition. They are a symbol to show that you can't do some of the tasks on those partitions, and that's because they are mounted.

In linux the primary partition are always marked 1-4 and the logical ones which are inside extended start from 5.

In your case, it's correct that you already have 3 primary and 1 extended partition, a total of 4, /dev/sda1 to /dev/sda4. You can't create a 5th one from the 33GB unallocated space.

One option you could do, is expand the extended partition /dev/sda3 to the left, to swallow that unallocated space inside it. Then once the 33GB unallocated space is inside /dev/sda3 you can create another logical partition from it. Otherwise you can't create a partition from it as it is.

When expanding be careful to expand /dev/sda3 first, that is the extended partition which like a container is holding /dev/sda5 and /dev/sda6 inside.

Also, to avoid the keys symbol, boot from the ubuntu cd into the live desktop, in that case / and /home partitions don't get mounted. A swap partition can be mounted but you will just right-click on it and select Swapoff and that will unmount it. Then if there is no keys symbol next to /dev/sda3 it should allow you to expand it into the 33GB unallocated space.

---

### Post by darkod on 2010-02-26
PS. Why do you have so much unallocated space that is wasted? Except the 31.5GB you are trying to use, you have 6.5GB after /dev/sda1 and 3GB after /dev/sda6. For example you can double /dev/sda6 in size by adding the 3GB unallocated space to it.

If you are willing, I would reconsider the layout on the hdd and maybe install fresh fedora and ubuntu, or the other way around, doesn't matter.

Also, /dev/sda6 is LVM but it's barely 3GB. You can use the hdd much more efficiently.

---

### Post by cybrsaylr on 2010-02-26
> **darkod said:**
> If I'm not mistaken this shows the used/free space on your partitions. The OP is talking about unallocated space not belonging to any partition.

Thanks.
I see that now after finally installing gparted in Ubuntu then opening it to take a look. Never got around to or needed to use gparted before.

---

### Post by daudiam on 2010-02-26
Thanks a lot

I deleted one of the primary partitions (which i thought was redundant), and now I am attaching a screenshot.
Please tell me if I can lvm2 also and extend the 34 GB logical partition to include all the free space in sda3.

Then, without creating a partition from the 38GB unallocated space, can I install ubuntu in that unpartitioned space MAKING IT AN EXTENDED PARTITION instead of a primary partition.

Also, while trying to unmount e:, a message came "Unable to unmount e : daemon inhibited". Why is that ?

Again, THANKS A LOT.

---

### Post by darkod on 2010-02-26
If I understand correctly what you want to do, yes you can. :)

1. Open Gparted from the ubuntu live desktop and expand /dev/sda3 to include the 38GB unallocated space. After that the space will be inside it.

3. Click on the Install icon on ubuntu live desktop and either tell it manually to create a root and swap partition into that 38GB space (for example 36GB root and 2GB swap) or you should be able to use the Use Largest Available Free space option and the installer will use that 38GB space to install ubuntu into it.

But I have a question before you start this. What is the LVM partition /dev/sda6? With a size of only 4GB it looks like the fedora swap. But this is extremely strange setup. You have the fedora / as a primary ext4 partition, but you have swap as LVM. You should rather have the / partition on LVM and the swap doesn't need to be on LVM at all.

There is another reason for this question. If this /dev/sda6 partition is actually the fedora swap, having it on LVM is stopping it being used for ubuntu too, at least not without more complicated manual install of ubuntu. You see, for as many linux installation as you have on the hdd, you can use the same swap partition because you only have one OS working at the same time. This saves space, you don't create swap partition for every distro.

I would get rid of that 4GB LVM partition and create standard 4GB swap area there. That can be used by both ubuntu and fedora. In fedora because you already have it installed, you might need to read about how to set it up to use this new swap, at the start it might complain a bit not being able to find its old swap partition.

Also, if you don't have too important data and setings in fedora, you can redo the whole setup and have both fedora and ubuntu /, and swap, on a LVM partition. That's the best way to use it.

---

### Post by daudiam on 2010-02-27
Thanks again

I think the lvm partition was from a previous install of fedora. Anyway, I will remove it and install ubuntu with a new swap space, and try to configure fedora to use that new swap space.

But, on opening the computer, when I click on the "other" option, it says BOOTMGR is missing. BOOTMGR is a windows thing, is there any trace of it left even now on my computer.

Thanks.

---

### Post by daudiam on 2010-02-27
Thanks again

I think the lvm partition was from a previous install of fedora. Anyway, I will remove it and install ubuntu with a new swap space, and try to configure fedora to use that new swap space. 

My concern is whether the ubuntu so installed will be visible in fedora too and vice-versa

Also, on opening the computer, when I click on the "other" option, it says BOOTMGR is missing. BOOTMGR is a windows thing, is there any trace of it left even now on my computer.

Thanks.

---

### Post by daudiam on 2010-02-27
q

---

### Post by darkod on 2010-02-27
You will have to run the boot info script to check for traces of boot files. You can do it from ubuntu live desktop, and follow these instructions:

[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by daudiam on 2010-02-27
Installing ubuntu in sda3, will I get to read files stored in (fedora as well as ubuntu) from ubuntu and vice-versa ?

---

### Post by darkod on 2010-02-27
The fedora root partition will not get automatically mounted in ubuntu, and vice-versa. You  can mount it manually if you need it occasionally, or you can set it up to mount on startup.

But I'm not sure if there can be permissions conflict because the fedora root partition is owned by the fedora user, and the ubuntu by the ubuntu user.

If you plan to share large files regularly one option would be to have small root partitions which will only contain the smaller files, and have a separate partition which can even have mount point /data to be shared from both fedora and ubuntu. If you plan to share like music, videos, etc that might be a better option.

---

