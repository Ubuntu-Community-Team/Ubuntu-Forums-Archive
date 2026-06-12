---
title: "Dual booting partitions questions"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by hariskar on 2012-10-12
I have windows 7 in partition C. I want to install Ubuntu to dual boot with windows. The disk has 2 more partitions D and E. D is empty and the size is about 292GB.
How many partitions should I make in D? What size should they have? What should I install in each partition? What should I do to dual boot?
Thank you!

---

### Post by darkod on 2012-10-12
You will need to delete the D partition, not "make partitions" inside it. Ubuntu doesn't install on ntfs. Once you delete the partition it will leave the space as unallocated. Leave it as such, don't create partitions in windows.

If you use the auto method to install, it will use the unallocated space and install with the standard two partitions, root and swap.

If you want different layout, you will need to install manually. In that case you can create a third partition for /home for example.

The size of partition depends. For swap you usually do 2GB or if you want to hibernate you need about 1.5 x RAM size. All the rest goes to the root partition.
Or if you make the separate /home, make root 20GB and the rest for /home.
You usually make partitions with ext4 filesystem, and the swap is only used as swap area, with no mount point.
The mount points for the other partition are / for root and the /home for the separate /home if you are making it.

---

### Post by hariskar on 2012-10-12
Thank you, if I do all above, will it dual boot, or do I have to do something else

---

### Post by darkod on 2012-10-12
It will dual boot. The grub2 bootloader detects win7 automatically and creates the dual boot menu.

---

### Post by hariskar on 2012-10-12
The new partitions have to be primary or logical?

---

### Post by darkod on 2012-10-12
Logical. It's better and it will give you more flexibility later.

---

### Post by ALinuxWindowsBalance on 2012-10-12
Be careful how you name your partitions. 
Windows "names" the drives with letters, and shouldn't be confused with actual labels.
Same with Linux. /dev/sda1 /dev/sda2 /dev/sda3 are all partitions but re-named and ordered.

---

### Post by hariskar on 2012-10-12
So, sda has sda1 (windows), free space 314GB and sda2 ntfs. I should choose free space and create 2 logical partitions (swap and /)? I did this but then nothing booted...
Thank you for replies!

Edit: Now I do it again: In free space above I created e logical partitions sda5 for / ext4 287GB, sda6 ext4 for /home 20GB and sda7 for swap 6GB. I chose device for boot loader sda5. Let's see what happens..

---

### Post by cybrsaylr on 2012-10-12
> **darkod said:**
> If you want different layout, you will need to install manually. In that case you can create a third partition for /home for example.

Have heard a few say this is a good way to go.
How do you do it manually?
Can It still be done by repartitioning if you already have 12.04 installed or do you have to do a fresh install?

Right now I just have 2 partitions: 111GB for 12.04 and 8GB for swap.

---

### Post by darkod on 2012-10-12
> **hariskar said:**
> So, sda has sda1 (windows), free space 314GB and sda2 ntfs. I should choose free space and create 2 logical partitions (swap and /)? I did this but then nothing booted...
Thank you for replies!

Edit: Now I do it again: In free space above I created e logical partitions sda5 for / ext4 287GB, sda6 ext4 for /home 20GB and sda7 for swap 6GB. I chose device for boot loader sda5. Let's see what happens..

The device for the bootloader is only /dev/sda, the MBR of the disk. If it has a number like /dev/sda5 it means a partition and you won't see the grub bootloader since the system is looking for the bootloader on the MBR of the disk, not on a partition.

---

### Post by deadflowr on 2012-10-12
> **hariskar said:**
> So, sda has sda1 (windows), free space 314GB and sda2 ntfs. I should choose free space and create 2 logical partitions (swap and /)? I did this but then nothing booted...
Thank you for replies!

Edit: Now I do it again: In free space above I created e logical partitions sda5 for / ext4 287GB, sda6 ext4 for /home 20GB and sda7 for swap 6GB. I chose device for boot loader sda5. Let's see what happens..

Flip the sizes around. Root(/) only needs to be 20GB, but your home partition where you'll store your personal files should be large.

---

### Post by hariskar on 2012-10-12
Thank you! So this is why it did not boot, I left for boot loader the default sdb...

---

### Post by darkod on 2012-10-12
> **cybrsaylr said:**
> Have heard a few say this is a good way to go.
How do you do it manually?
Can It still be done by repartitioning if you already have 12.04 installed or do you have to do a fresh install?

Right now I just have 2 partitions: 111GB for 12.04 and 8GB for swap.

If the partition size is good for you, you can reuse existing partitions. After you select Something Else and the partition list shows, you will need to select them one by one and click the Change button below.
In the windows that shows, you select to use as ext4 (or swap area for swap), the mount point, and tick the format box for the / partition if you want to delete an existing install.
If you have an existing /home you usually don't tick the format box because you want to keep it.

The bootloader device is a MBR of the disk where you want to, not a partition on the disk.

It doesn't matter if there is already existing installation, just make sure you select the correct options.

---

### Post by darkod on 2012-10-12
> **hariskar said:**
> Thank you! So this is why it did not boot, I left for boot loader the default sdb...

/dev/sdb will also work, but when you have multiple disks you have to tell bios to boot from the correct one. If you make /dev/sdb first option to boot from, it will work.

The main thing is NOT to put it on a partition, as long as it's a disk, it's OK. Of course, it's your job to boot from the correct disk. :)

---

### Post by hariskar on 2012-10-12
OK, dual boot launched, it asked for login and pass, I gave it and it stops at a black command line screen that has my computer name
hk@hkP5K-WM:~$
I types startx and it says: FATAL: Error inserting nvidia_173 (...): No such device

What can I do?

Also can I change the order of boot manager options? I want to put windows 1st.

---

### Post by darkod on 2012-10-12
> **hariskar said:**
> OK, dual boot launched, it asked for login and pass, I gave it and it stops at a black command line screen that has my computer name
hk@hkP5K-WM:~$
I types startx and it says: FATAL: Error inserting nvidia_173 (...): No such device

What can I do?

Also can I change the order of boot manager options? I want to put windows 1st.

Now you are talking about video issues, that's a different ball game. Did you try the cd in live mode first to see if it works fine? Usually if live mode is working, the installed system should also work.

You might need to boot once using the nomodeset parameter if you have nvidia. There are details how to do that here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Note that you don't need to do everything it says there, because you have already done the installation. Focus just on the instructions how to boot first time with nomodeset.

Get the ubuntu working first, making windows the default OS in the menu is not a problem and you will do it later.

---

### Post by hariskar on 2012-10-13
Thank you, I started a new thread about these problems: [http://ubuntuforums.org/showthread.php?p=12293146#post12293146](http://ubuntuforums.org/showthread.php?p=12293146#post12293146)

---

