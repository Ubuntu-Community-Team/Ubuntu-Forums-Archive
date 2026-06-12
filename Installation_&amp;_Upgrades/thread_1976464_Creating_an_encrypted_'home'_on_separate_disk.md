---
title: "Creating an encrypted '/home' on separate disk"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2012-05-08
Hi

With the release of Ubuntu 12.04 i'm also upgrading my hardware to an SSD for the OS and a HDD for the home Directory. I've been practicing the install in Virtualbox but continually hit a problem.

Using the Ubuntu 12.04 Alternate ISO, i get to the 'Partition Disks' screen and select 'Guided - use entire disk and set up encrypted LVM', this happily goes off and configures a boot, SWAP and root partition for me on the SSD (great so far).

I now want to create an encrypted primary partition on my HDD for my home folder, so I:
- create an empty new partition table on the device
- create a new partition
- Primary
- Use as: 'physical volume for encryption'
- configure encrypted volumes
- Create encrypted volumes (select the volume)
- Finish

Then i get this!

[IMG]http://ubuntuone.com/7QNeMUof4uZrnmt5FMr4Xo[/IMG]

Now I'm confused!!

The SWAP space created was created automatically on the SSD, but i only get this error when im trying to set mp my home folder on my HDD, and that (i don't think) has a SWAP!?

If someone could help my with this i would be grateful, as i'm really excited to install Ubuntu 12.04.

Many Thanks

---

### Post by Slim Odds on 2012-05-08
> **Ceiber Boy said:**
> Hi

With the release of Ubuntu 12.04 i'm also upgrading my hardware to an SSD for the OS and a HDD for the home Directory. I've been practicing the install in Virtualbox but continually hit a problem.

Using the Ubuntu 12.04 Alternate ISO, i get to the 'Partition Disks' screen and select 'Guided - use entire disk and set up encrypted LVM', this happily goes off and configures a boot, SWAP and root partition for me on the SSD (great so far).

I now want to create an encrypted primary partition on my HDD for my home folder, so I:
- create an empty new partition table on the device
- create a new partition
- Primary
- Use as: 'physical volume for encryption'
- configure encrypted volumes
- Create encrypted volumes (select the volume)
- Finish

Then i get this!

[IMG]https://ubuntuone.com/7QNeMUof4uZrnmt5FMr4Xo[/IMG]

Now I'm confused!!

The SWAP space created was created automatically on the SSD, but i only get this error when im trying to set mp my home folder on my HDD, and that (i don't think) has a SWAP!?

If someone could help my with this i would be grateful, as i'm really excited to install Ubuntu 12.04.

Many Thanks

Firstly, you definitely do NOT want swap space on an SSD. Second, as it says, you need to either turn swap off or encrypt the swap partition. If you let it setup those partitions automatically, how would it know to encrypt the swap partition?

Take a look here: [http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

---

### Post by Ceiber Boy on 2012-05-09
> **Slim Odds said:**
> you definitely do NOT want swap space on an SSD.

Why do you not want SWAP on the SSD?

---

### Post by GnuSense on 2012-05-09
Supposedly SSDs have a limited number of writes before they wear out. I'm not sure how true this still is, new technology has figured out how to distribute the writes all over the drive, slowing wear, but in the early days folks were encouraged not even to use a journaling file system like ext3 on a SSD. 

For all its supposed ease of use, Ubuntu's support for custom drive partitioning with encryption sucks eggs. Sure, you can do whatever you want with an expert text install from the alternate image if you don't mind getting down and dirty and setting up LVM & LUKS from the command line, but even using the "Expert" install from the alternate ISO it wouldn't let me control how I partitioned the disk with LVM encryption. I wanted a separate /home & '/' partition and it set me up up with a 10GB '/'with no way to alter that (I wanted at least 20 GB to support a decent /tmp directory for large downloads, multiple desktops & room to load a few GB of .deb files in /var/cache/apt/archives.  I don't want to go back and repartition the LVM from the CLI after the install. If I had the patience for that I would simply use Debian (which I largely do, anyway). 

So I decided to allow one big encrypted '/' partition. It set up a 6 GB swap partition on my 60 GB SSD, I guess because I have 6 GB of RAM, what a complete waste of space, especially considering that 12.04 disables hibernation by default. I am never going to touch that swap partition for anything else with that much memory on the machine. I'll probably disable the swap partition in the fstab and reformat it to ext4 at some point, but it is a fresh install, so I'm not feeling any space constraint and I was able to re-enable hibernation.

I should file a bug report against the installer for this bone-headed behavior.

---

### Post by Slim Odds on 2012-05-09
> **Ceiber Boy said:**
> Why do you not want SWAP on the SSD?
Well, SSD's do not have unlimited write cycles...

Even if they are better these days, they will still wear out quickly if your machine swaps a lot. Since you didn't mention all your specs, I don't know. If you have a lot of RAM, you may not even need swap for "normal" operation (not talking about suspend/hibernate).

Also, SSD's writes are quite a lot slower than their reads. This can have a bad impact on the swapping itself. You always want swap on the drive with fastest write speeds (reads are generally always much faster then write for almost any storage device).

---

### Post by Ceiber Boy on 2012-05-10
> **Slim Odds said:**
> Since you didn't mention all your specs

Sorry, it was neglectful of me not to even mention even basic specifications:

Memory: 4GB
Processor: AMD Phenom II X4


To my recollection I've never used the SWAP in this current 10.04 install! so i think i'll try and live without it now in my 12.04 install, if i do hit a problem ill upgrade my memory, I don't suspend or hibernate the system.

---

### Post by Slim Odds on 2012-05-11
> **Ceiber Boy said:**
> Sorry, it was neglectful of me not to even mention even basic specifications:

Memory: 4GB
Processor: AMD Phenom II X4


To my recollection I've never used the SWAP in this current 10.04 install! so i think i'll try and live without it now in my 12.04 install, if i do hit a problem ill upgrade my memory, I don't suspend or hibernate the system.

Perfect solution! ;)

---

