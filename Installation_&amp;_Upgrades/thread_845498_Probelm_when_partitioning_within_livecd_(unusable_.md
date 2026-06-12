---
title: "Probelm when partitioning within livecd (unusable space)"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by RonLut on 2008-06-30
Hi.
I had Ubuntu 8.04 64bit installed but now I'm reinstalling it to a 32 bit version, but I have a problem when partitioning:
I have (after I deleted [in the partition editor] all linux partitions) now:
sda1 36.7GB ntfs Windows XP
free space 22GB
sda4 101GB ntfs shared space between win. and lin.

Now when I try to create 3 patitions from the free space:
logical SWAP 2GB
primay EXT3 / 10GB
primary EXT3 /home 10GB

in the last step (after I have 2 linux partitions created [doesn't matter which]) it shows me that the free space is unusable and I can't create the last linux partition.
What should I do?
Thanks :(

---

### Post by uidb4056 on 2008-06-30
There is a limit of four primary partitions on a disk or 3 primary and one extended, inside one extended partition you have no limit to create logical partions. Then you must delete first the linux partitions you have created and create one extended partition with all free disk space, then inside this partion you can create your linux partitions as a logical partition.

---

### Post by SkonesMickLoud on 2008-06-30
You're running into the 4 partition limit.

Simple fix:  Create an extended partition that is the size of 2 of your planned partitions.  Then create 2 Logical partitions inside of your one Extended partition.  Personally, I have my Swap and ArchLinux partition created as Logicals inside of an Extended.  Mine looks like this:

[img]http://img.photobucket.com/albums/v99/echo3bravo/partitions.png[/img]

The aqua/cyan partition at the end of the drive is the Extended partition with the 2 Logical's inside of it.

---

### Post by RonLut on 2008-06-30
hmm.... how do I create extended partition with the installer?:oops:

---

### Post by logos34 on 2008-06-30
> **RonLut said:**
> hmm.... how do I create extended partition with the installer?:oops:

Choose 'Manual' partitioning option.  Or use Gparted (system>admin>partition editor) to make the extended beforehand

---

### Post by RonLut on 2008-06-30
> **logos34 said:**
> Choose 'Manual' partitioning option.  Or use Gparted (system>admin>partition editor) to make the extended beforehand

I'm doing it manual.... but there is no option for extended....
I guess I should do it before install as you said? and then how do I apply this into the install?

---

### Post by logos34 on 2008-06-30
> **RonLut said:**
> I'm doing it manual.... but there is no option for extended....

then choose filesystem type "ext3" and "**logical**"--it will wrap it in extended, I believe.  Or if you do it beforehand using gparted, either just choose "guided--use largest continuous free space" install option (in which case it should select the space inside the extended and make / and /swap for you), or else select 'manual' and create the logical partitions inside for root (type: 'ext3', mountpoint '/') and swap (type: 'linux-swap', mountpoint '/swap').

---

### Post by SkonesMickLoud on 2008-06-30
> **RonLut said:**
> I'm doing it manual.... but there is no option for extended....
I guess I should do it before install as you said? and then how do I apply this into the install?

It's easier to do it before hand with either a GParted LiveCD or GParted on the Ubuntu LiveCD.  Simply right click on your unallocated space, and select "new", you should have 2 choices, select "Extended" as the entire unallocated space, then create Logicals as you'd create regular partitions.

---

