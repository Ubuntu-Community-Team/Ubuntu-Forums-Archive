---
title: "Unable To Erase Disk And Install"
date: 2024-05-19
forum: Installation &amp; Upgrades
---

### Post by prestoniwnl on 2024-05-19
I'm trying to install Ubuntu, however it doesn't give me the option to erase the drive and install. I've looked at other threads, but they seem incomplete. This is a Lenovo Thinkpad 490s. 

I did sudo parted -l 

Error: /dev/sda: unrecognised disk label
Model: Seagate Portable (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags:

---

### Post by yancek on 2024-05-19
Is this 1TB Seagate drive an internal or external drive?  Is there anything on it, has it been used.  The parted output you posted shows no partition table and no partitions and no filesystems so you an start by creating a partition table (gpt likely bes) then create a partition or partitions to your liking.

---

### Post by BBQdave on 2024-05-19
If you are using 24.04 iso, load it which brings up live session and choice to install. Follow install process, which gives you choices to wipe drive and do a fresh install :)

---

### Post by Rubi1200 on 2024-05-19
From your output:
```
Partition Table: unknown
```

If you use GParted from a live USB you need to first add a new partition table before you can format and add partitions or filesystems.

I assume this is a modern drive for a recent computer so the normal choice would be to add a gpt partition table.

But we need more information on your setup, especially other disks, other operating systems.

---

### Post by prestoniwnl on 2024-05-19
External drive. Has not been used previously, just used it to install Ubuntu. When I go to make a gpt partition it says
Partition(s) 1, 4 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use.

---

### Post by prestoniwnl on 2024-05-19
Tried to add a new partition on gparted. Received this message. 
Partition(s) 1, 4 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use.

---

### Post by Rubi1200 on 2024-05-19
If you plugged in an external drive, you need to unmount it before attempting to write any changes.

GParted will usually show a small key icon indicating the drive is mounted. If you right click on the drive it should offer the option to unmount and then you can try again.

Make absolutely sure it is the external drive you are looking at before making changes. There is a dropdown menu top right in GParted which shows all drives it can detect.

---

### Post by prestoniwnl on 2024-05-19
This is what I see when I go into gparted. It appears i'm unable to mount/unmount. 

[https://imgur.com/gallery/ubunutu-36lMQWP](https://imgur.com/gallery/ubunutu-36lMQWP)

---

### Post by Rick St. George on 2024-05-19
To use GParted to install Ubuntu 24.04, you will need to follow these steps:

Step 1: Install GParted
Which is in the Boot / Install DVD/Thumbdrive via Install process. Otherwise ... To install GParted, open a terminal and run the following command: sudo apt-get update and then sudo apt-get install gparted

Step 2: Open GParted

Once GParted is installed, you can open it by searching for it in the application launcher or by running the command gparted in the terminal.

Step 3: Create a new partition

In GParted, you will see a list of all the partitions on your hard drive. To create a new partition for Ubuntu, right-click on an unallocated space and select &#8220;New&#8221; from the context menu.

Step 4: Set the partition size

In the &#8220;New Partition&#8221; window, set the size of the partition to the desired size for your Ubuntu installation. You need 3 partitions.
a. for UEFI / Boot partition of about 500 MB in size. Flag UEFI / Boot
b. for the main system install and set the file system type to &#8220;ext4&#8221; for Ubuntu. Flag as /
c. for the swap file, 4 GB should do.

Step 5: Format the partitions

Click on the &#8220;Format&#8221; button to format the new partitions. This will erase all data on the partitions, so be careful not to format the wrong partitions.
Note: your post above shows device / sda, but your picture shows sdb (which is a second drive). You should be installing to sda (first drive).

Step 6: Install Ubuntu

Once the partition is formatted, you can install Ubuntu on the new partition. Follow the installation prompts to install Ubuntu on the new partition.

That&#8217;s it! You should now have Ubuntu 24.04 installed on your computer using GParted.

---

### Post by prestoniwnl on 2024-05-19
Rick St. George,

Tried going through your steps, however for some reason I don't think gparted sees my computers hard drive. It only sees the Seagate external hard drive. This is what I see when I disconnect the external hard drive and start up gparted. :)

[https://imgur.com/gallery/ubuntu-2-xPf4hLH](https://imgur.com/gallery/ubuntu-2-xPf4hLH)

Thanks for your help

---

### Post by prestoniwnl on 2024-05-19
I went through the steps with manual installation as well. It appears to go through normally (making a user/pass) and begins downloading. Then it says that it had an error in downloading and shows a very long log.
Here are the images going through the manual partitioning. 

[https://imgur.com/gallery/manual-partitioning-XYSXL47](https://imgur.com/gallery/manual-partitioning-XYSXL47)

---

### Post by MAFoElffen on 2024-05-19
Hold on a bit... Take a breath and relax.

Let me explain in a different way, without "leaving some important steps out"...

If you are using GParted on a new drive without a partition. In GParted: Device > Add "Partition Table" > GPT. It won't let you do anything until you do that.

I see in GParted that your external Drive shows up as /dev/sdb... and is 1TB... from your earlier post. Then I see the screen shot of you in the manual partitioner, and things are "a bit wonky". Meaning what is there in that last post will fail in the installer.

Let me say right off, if I am doing a manual partitioning, I do not use the new installer's partitioner, except after I create partitions with GParted (or manually thru commandline), then go back to the installer. I have enough Bug Reports filed against that partitioner to keep them busy for eons. let's keep you away from those.

If you are going to manual partition the installer then let's do it right, so that it will work, and give you a good install, that you can grow from. Right? What you have in your last post will fail. Lets get you going strong and healthy.

Let me explain why that later screen shot would cause problems. Take this with a grain of salt. I've only had over 25,000 Linux installs in over 15 years. That is a modest count. So what I recommend is just based on what works for me, and the Users I support.

1Gb is about right for what "I do" now as an EFI partition. If you let the new installer do it, it would set that at 750MB. But I usually do that as the first partition, near the root of the drive (not as the second partition). It is fine that it is second,but... As an EFI partition, it is too small. If you set it as 1GB as the first partition, that is all it will ever need. And you will not need to resize it. If you leave it as the seocond partiton, it would be harder to resize partitions in front of that, if you did have partitions that needed resized... Which you do. Make sure that ESP/EFI partition is flagged with both ESP & boot.

The /boot partition is way too small!!! It will not even install into that little of space. Sorry. If u did the installer scripts, the installer will give it at least 1GB to 2GB. My experience has lead me to now give them 3GB. I make them as the 2nd partition.

Third partition. Good choice on making that as swap... but somethings it's better to leave that at the end of the drive. I see you were thinking about swap as a partition instead of a file, which is my first choice. BUT... If later, you decide your choice of the size of your swap was wrong or you outgrow that, and you want to resize it, then you have to move everything after that... Which is a risk of all that data. See where that factor might make sense later down the road? I put swap at the end of a drive. That way what is before it is considered a resize, instead of a move to the left. less risky with that. I know. I have had to recover peoples machines if that failed. 

Next the size of that... I'm old-school and have been around way too long. been supporting Solaris since 2005, with the same structures. My rule of thumb for Desktops is 1.5 to 2 times the amount of system RAM. 4GB is the minimum RAM recommended for Ubuntu. EXT4's overhead for journaling, inodes, and such is 5%. So at that is why 1.5% is usually computed as the minimum partition size. If you make it the same size as your RAM, it will have problems hibernating, sleeping , etc. It can''t put all that into a smaller space. Are you saying your system has less RAM than the recommended? You didn't say how much, so I'll leave that for you to figure out.

Next you have 995GB as "/"... lets talk about that. You need 6-8GB above what the OS takes to exist for updates and a release upgrade. Here is where you start thinking that this system will live past tomorrow... and that if you are manual partitioning... Making a custom install, that you are thinking about making it easier for yourself for the future. With me with that?

Make the "/" partition your 3rd partition. The OS system itself realistically only needs 80GB to 100 GB. Figure on this... Give it 100GB. That will be later mounted as "/"

Then... Do the math... See what is left in your 1TB drive. Figure out how much you need at the end for your swap. Minus that from your left-overs, and create then 4th partition that size for a /home partition. Mount that as /home. That way, if yo uhave to reinstall for the what if's, or do a release upgrade, it doesn't affect your data in /home. It is safer there.

Then add your swap partition based on what is left, on what your new calculations where.

When I am through creating my partitions, I start the installer back up... Go "Other" to get to the manual partitioner, Select that drive as the boot drive / it will find that esp drive to use as EFI. Select each of those partitions, use-as and either format or not, but then set the mounts to what they will be used for... Then continue the install.

Sorry, that is the extent of what I trust the newer partitioner to do. It will not recognize pre-existing filesystems or Volume Managers... Which I have Bug Report filed against it for that.

Any comment or questions?

---

### Post by prestoniwnl on 2024-05-21
Solved! Thank you so much :)

---

