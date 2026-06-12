---
title: "Installing Kubuntu, Vista and Sabayon on same HD"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by hexwolf on 2007-12-02
I've tried unsuccessfully to be able to install Kubuntu, Sabayon and Vista on the same laptop hard drive for awhile now, so I figured it might be time to check out the community here. Ideally, I'd like to use a partition to store most all media so that both Kubuntu and Sabayon could access it, however, I don't quite know what partition type would allow me to do something like that.

I've had all three operating systems installed at once, however, the last operating system to be installed was the one I was able to boot to, I was unable to amend the bootloader to find the other Linux operating system.

So, knowing these concerns, can anyone recommend a good partitioning scheme and likewise provide some instruction in regards to the installation of both Sabayon and Kubuntu? I've posted this on the Sabayon forums as well, to compare input for ideas.

Thanks in advance!

---

### Post by Pumalite on 2007-12-02
Have your whole hard drive formatted ntfs and install Vista. From Vista allocate space for 2 partitions. Install Sabayon 2nd in one of them. Install Kubuntu last. If it doesn't pick up the other two, it can be easily fixed in your menu.lst.

---

### Post by hexwolf on 2007-12-02
I've been using gparted to make an NTFS partition of ~30 gigs for Vista and allocating two more partitions and leaving them unpartitioned. I haven't had much success duplicating Sabayon's partition paramters (it's an LVM), so I direct it to an unformatted partition and let it do it's thing. 

I've done some reading and was recommended "superGRUB." I'm looking into it right now, though my concern is still with the creation of a partition that allows me to save miscellaneous files and access it in either Sabayon or Kubuntu.

In all of my attempts thus far, I've use gparted to create an NTFS partition and Vista finds it and automatically installs to it, leaving me with the two unpartitioned spaces. From there, I usually let the live C.D.s do their thing, adding in a swap partition for each operating system.

Thanks for the input so far!

---

### Post by Pumalite on 2007-12-02
You are welcome.

---

### Post by hexwolf on 2007-12-02
Still no luck, I'm guessing creating two ~10 gig partitions for the linux distros and if I'm correct, a rather large Ext3 partition for media for both distros to access would be sufficient, though I'm still not quite sure.

Thanks in advance!

---

### Post by hexwolf on 2007-12-03
I'm now having some concerns with the partitions, I'm seeking input as I would like to know other's input in regards to situations I'm not currently foreseeing.

~35 gig NTFS for Vista
~20 gig Ext3 for Sabayon
~20 gig Ext3 for Kubuntu
~2 gig Extended Partition for Linux-Swap
~80 gig NTFS partition for read/write media between OS's

I'm also having trouble understanding mount points, as with more than one Linux OS, you can't use a "/" mount point for the second OS, so it seems I need a bit of reading material and/or help in regards to that problem.

Thanks in advance!

---

