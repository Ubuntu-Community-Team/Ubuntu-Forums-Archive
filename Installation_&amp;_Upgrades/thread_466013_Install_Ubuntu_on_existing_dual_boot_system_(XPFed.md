---
title: "Install Ubuntu on existing dual boot system (XP/Fedora)"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by DNAphil on 2007-06-06
I have seen a few posts on this, and I really don't see the exact answers I am looking for so I am hoping that a new post, may get me the answers I need.

I have a dual booting laptop that is running XP and Fedora Core 6.  It uses GRUB for the dual booting, that was installed by Fedora during its install.  What I would like to do, is to replace Fedora with Ubuntu and keep this laptop as a dual booting laptop, with XP and Ubuntu.  

Here are the partitions on the drive:

sda1-- fat16 (Dell Media Utility- used for system recovery)
sda2-- ntfs (XP partition)
sda3-- ext3 (marked as /boot, and contains GRUB)
sda4-- unknown (labeled as LVM, and I am sure it is Fedora's LVM)

Now if I used the Live CD, and do a manual partitioning, do I remove sda4, and re-format it for Ubuntu, and leave sda3 alone?  If so, will Ubuntu detect sda3 and upgrade grub with either its own boot manager, or just update grub so that i can dual boot into XP and Ubuntu?

Or do I have to do something completely different?

Your help would be greatly appreciated, as I am dying to get this laptop up and running with Ubuntu.

Thanks.

---

### Post by reiki on 2007-06-06
I only use the Alternate CDs, not live, but as long as you leave sda1 and sda2 alone, you should be fine.
My only concern is that I do not know what sda4 is. It says LVM... fine... *probably* Fedora, but I don't know that from here. What is the size of sda3 and sda4?

My thoughts right now are that if you simply leave sda1 and sda2 alone you should be able to do whatever you want to sda3 and sda4. I would manually partition and I would probably delete both partitions and create new ones.

---

### Post by DNAphil on 2007-06-06
sda3 is 100 Mb, and when I mounted it and looked in it, it was the /grub directory as well as some other files that had fc6 in their name, which made me believe that they are also fedora files or config files for grub.

sda4- is about 10Gb in size, exactly what I partitioned when I set up the Fedora system last year.  I am very confident that sda4 is Fedora in LVM format, and that the Gnome partitioning program just does not recognize it.

---

### Post by dabl on 2007-06-06
100 MB is too small to install a Linux OS in -- I'd say delete both sda3 and sda4, and make it one 10.1 GB partition.  That's still kind of a minimalistic size, but Ubuntu will fit and run in it.  You won't have much spare room for user data -- maybe 4 or 5 GB, depending on how many packages you install.

---

### Post by DNAphil on 2007-06-06
I am not too worried about space for user data, my laptop mainly stays at home, and shares all of its files across the network.  Very little actual user data stays on my laptop.

So it sounds like I should take out sda3 and sda4.  

On the live CD will Ubuntu prompt me to install a boot loader?

---

### Post by DNAphil on 2007-06-07
Time for the Epilogue to this story....

So , from the Live CD,  I went ahead and used the GNOME Partition tool to remove sda3 and sda4.  I left the space unused and started the Install program.  The Install program saw the unused space and had an option for Guided partitioning using the largest contigious unused space.  I let the Installer do its thing, and when it was done (the second time, the installer crashed once, but doing the same steps above on more time got it working), it put in a new version of GRUB, configured it to dual boot, installed some swap space, and did the full install.

So now I have a dual boot, Ubuntu/XP laptop.  

Thanks for the help and advice.

---

### Post by bmach on 2007-06-16
Hi DNAphil,

I'm in the exact same situation as you were but with an earlier version of Fedora. I also have the two partitions that Fedora is installed on (one is 100MB and the other is 10GB). 

I'm a little bit worried about using the GNOME partitioning tool that comes with Ubuntu live CD simply because i'm not familiar with it and worried I will do something wrong and not be able to boot my machine at all. 

Does anyone know if I delete the two Fedora partitions in windows using PartitionMagic will i still be able to boot my PC in windows or will this corrupt the GRUB multiboot? Similarly, if i choose to use the GNOME partitioning tool as part of the Ubuntu live CD and something goes wrong here (i.e. crashes like it did for you DNAphil) could this potentially corrupt the GRUB multi boot? What partition does the Grub multiboot run from?

Many thanks in advance.

---

