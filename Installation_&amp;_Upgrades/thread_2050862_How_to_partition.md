---
title: "How to partition?"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by xdflames on 2012-08-31
Basically, I am trying to install Ubuntu on a previously Windows 7 laptop. I have a 320GB hard drive and will mostly only be using this computer for internet browsing and messing with the Linux OS. I am installing Kubuntu 12.04 through a flash drive and made it into an installer using "Universal USB Installer."

I want to know what to set my partitions to, so that I can have one for the OS (Kubuntu) and one for everything else. Or others if they are needed, as I know nothing about partitioning a hard drive besides that it divides up the drive.

So, what type and size should I give each partition to do what I want?

Edit: To add a bit more, the main thing I need to know is how should I divide up my space with my 320GB hard drive? The reasons I want to know is because most guides I see, people are using a 100GB or less hard drive, and I am not sure if that should change how much space I use.
Edit2: The reason I want to do this is so I have a home partition for all of my data, so when I want to upgrade or change my OS, I can do so without worrying about losing any important data, and do not have to worry about backing up anything before hand. Plus, I need to understand partitioning at some point, and this is a good reason to do so.

---

### Post by SeijiSensei on 2012-08-31
Do you want to preserve the Windows partition and setup a dual boot arrangement?

In dual-boot settings, I will assign a small partition to /boot, another partition to Windows, a third to swap, and make the rest of the disk an extended partition.  Within that I'll usually assign 10-40 GB to the filesystem root, /, then make the rest a single large partition that I mount as /home.

Something like this:

```
/dev/sda1 - /boot (512 MB)
/dev/sda2 - Windows (50-100 GB)
/dev/sda3 - swap (usually 2 X physical memory, say 4-8 GB)
/dev/sda4 - extended
            logical partitions within the extended
            /dev/sda5 - / (20-40 GB)
            /dev/sda6 - /home (rest of disk)
```

Sometimes I'll create another partition of 20-40 GB into which I can install new Linux versions for testing.  That will use /boot and /home as well.

If I only intend to have a single Linux installation and nothing else, then I'll usually just have three partitions for /, swap, and /home.

---

### Post by xdflames on 2012-08-31
> **SeijiSensei said:**
> Do you want to preserve the Windows partition and setup a dual boot arrangement?

In dual-boot settings, I will assign a small partition to /boot, another partition to Windows, a third to swap, and make the rest of the disk an extended partition.  Within that I'll usually assign 10-40 GB to the filesystem root, /, then make the rest a single large partition that I mount as /home.

Something like this:

```
/dev/sda1 - /boot (512 MB)
/dev/sda2 - Windows (50-100 GB)
/dev/sda3 - swap (usually 2 X physical memory, say 8 GB)
/dev/sda4 - extended
            logical partitions within the extended
            /dev/sda5 - / (20-40 GB)
            /dev/sda6 - /home (rest of disk)
```

Sometimes I'll create another partition of 20-40 GB into which I can install new Linux versions for testing.  That will use /boot and /home as well.

No, I do not want to keep Windows installed. However, having an option for another OS install could be useful. But right now, I just want to have a seperate partition for my OS (Kubuntu 12.04) and one for my files so when I want to update my OS or install a different one, I do not have to worry about losing any files.
Edit: I also need to know what size I should set each partition, with me having a 320GB HD. Also, why it should be that size so I will know what to do when I partition another hard drive in the future.



Edit: Figured out a better solution for this is to just ask if this will be fine for what I plan on doing.
I will be making the following partitions:
/dev/sda1 swap 8191 MB
/dev/sda5 ext4 30719 MB
/dev/sda6 ex4 281158 MB

Is this okay? I've decided against making another partition for another OS, since I can reduce the size of /home later and make another.

---

### Post by SeijiSensei on 2012-08-31
> **xdflames said:**
> 
/dev/sda1 swap 8191 MB
/dev/sda5 ext4 30719 MB
/dev/sda6 ex4 281158 MB

That's fine, though if you really expect you'll want to install another OS at some point, I'd allocate the space now and leave it unformatted.  Resizing partitions is possible, but it can be tricky.  I'd also create a small /boot partition in this case as well.  That way both OS's can put their respective kernels in the same /boot and GRUB will see them both.  It can be as small as 256 MB, but I'd go with 512 MB so you don't run out of space if the kernels get updated frequently.  So this model would be 

/dev/sda1 - /boot (512 MB)
/dev/sda2 - swap (8 GB)
/dev/sda5 - / for OS1 (20 GB)
/dev/sda6 - empty partition for OS2 (20 GB)
/dev/sda7 - /home (remainder of drive)

I usually make the /boot partition be ext2 as its not large enough to make journalling worthwhile.

---

### Post by xdflames on 2012-08-31
Okay, thank you very much! Finally get to mess around with Kubuntu.

I got it installed and it is working very well. Now it's time to hunt around to find out all of the things I can do with this.

---

