---
title: "Unable to create a 17th partition"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Resilldoux on 2010-06-23
Hi there,

So I was just partitioning my hard disk to get it ready for installation of multiple Linux distributions and that's where it happened. I booted up my notebook using an Ubuntu 10.04 Lucid Live CD and used GParted to partition my hard disk.

First, I created an extended partition that would cover my whole hard disk (don't worry, I backed-up everything twice and stored it on my server). Then, I decided to skip the first GiB of my hard disk and started creating multiple ext4 partitions (10 GiB each) and labelled them so I'll be able to tell which partition contains which distribution later on. When I was satisfied with the result, I created multiple 100 MiB ext4 partitions at the very beginning of my hard disk (the first GiB of unallocated space, remember?) which I'm planning to mount as boot partitions for each distribution. But, when I successfully created 16 logical partitions in total, GParted refused to create a 17th partition, let alone an 18th and so on...

Now my question is: is GParted unable to create more than 16 partitions on a single hard disk, or is it a known fact that an extended partition cannot contain more than 16 partitions (so that it would be wrong to blame GParted for this). So, is it possible for me to create more than 16 partitions using a work-around or manually partition my hard disk using the terminal, or should I not create as much partitions on my hard disk?

---

### Post by dabl on 2010-06-23
Standard/default hard drive setup, with MS-DOS partition table type, will limit you to a max of 4 primary partitions.  One (and only one) of the primary partitions can be designated "extended" type and subdivided into a max of (15 for SCSI/63 for IDE) logical partitions.  If the formerly primary, now "extended" partition is used to contain logical partitions, then it will not be available as a primary partition for other use, so effectively it is lost.  As a result, for a SCSI or SATA drive you should be able to pack in 18 partitions, by using 4 primary partitions, and using one of them as an extended partition to hold 15 logical partitions (losing its ID as a primary in the process).

[http://tldp.org/HOWTO/html_single/Partition/](http://tldp.org/HOWTO/html_single/Partition/)
 

Note that there are other partition table types (GUID) with different rules.

Depending on what you are trying to do with all those OSs, you might want to consider installing them on virtual hard drives, under VMware or VirtualBox.

---

### Post by darkod on 2010-06-23
On top of the reply from dabl, why the 100MB /boot partition for each distribution? It doesn't really help and you'll need lot less partitions for your distros without creating /boot for each distro.

It will work just fine with the boot files in /.

---

### Post by Resilldoux on 2010-06-23
Now that I'm reading the reply from dabl, I'm actually considering doing exactly that. The reason was that booting from dedicated boot partitions at the beginning of the hard disk is in fact faster, but I see now that I'm actually forced to boot from / as we're all limited to 15 logical partitions within SCSI/SATA drives (as I understand).

---

### Post by dino99 on 2010-06-23
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

