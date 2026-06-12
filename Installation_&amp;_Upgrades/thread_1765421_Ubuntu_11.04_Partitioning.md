---
title: "Ubuntu 11.04 Partitioning"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by mganesh30 on 2011-05-23
I will be installing Ubuntu 11.04 aa a standalone on my 500 GB SATA HDD. I plan to have the following partitions:-
 
ROOT - 20 GB
BOOT - 50 GB
SWAP - 2 GB
HOME - Remaining space
 
Will this work properly? I will be downloading many addituonal softwares. Hence BOOT partition is 50 GB.

---

### Post by coffeecat on 2011-05-23
I think you've misunderstood the function of a boot partition. It contains only the kernel and initramfs images with associated files and some of the grub code. It need be only a couple of hundred megabytes in size. Better still, don't have a separate boot partition. It is an unneeded complication for most setups and is only really necessary in certain circumstances, such as with an old BIOS that cannot read beyond 137GB. 

The downloaded packages for software and updates are stored in a cache folder in /var and the actual application files are installed into /usr (mostly) with configuration files in /etc. A very few apps go into /opt. Since /var, /usr, /etc and /opt are in the root partition (unless you have a very complex partition setup), that's where your space needs to be. However, 20GB + 50GB = 70 GB which is very big by Linux standards for a root partition. What sort of applications were you thinking of installing? I would have difficulty fillling a 20GB root partition let alone a 70GB one. I think you would only need so much space if you were thinking of installing Windows games to run under wine. They do take up a lot of space.

---

### Post by grubu on 2011-05-23
Hello coffeecat[]("http://ubuntuforums.org/member.php?u=129087"),
for some reason I like the fact of having a separate boot-partition. What would you suggest for an optimized-size? 400MB? Would there be any disadvantage when using different linux-partitions in an extended partition?

---

### Post by coffeecat on 2011-05-23
> **grubu said:**
> Hello coffeecat,
for some reason I like the fact of having a separate boot-partition.

I have to ask you: why? :) They really are more trouble than they're worth for most home users. In my opinion, of course!

> **grubu said:**
> Would there be any disadvantage when using different linux-partitions in an extended partition?

An extended partition is simply a special type of primary partition whose sole purpose is to act as a container for logical partitions. So I presume you mean different Linux logical partitions. It doesn't matter whether a Linux boot partition, or root partition for that matter, is primary or logical - unlike with Windows. It would be quite feasible - but slightly bizarre - to create one extended partition covering the whole of your hard drive and then create whichever logical partitions you needed for Linux in that. Of course, that wouldn't be an option if you wanted to dual-boot with Windows.

---

### Post by mganesh30 on 2011-05-23
Hello coffeecat,
 
Thanks for the explanation. However, I do have a slightly old BIOS. What then is your recommendation for partitions & sizes? I do not want to get into a situation where I get GRUB Error 18.

---

### Post by coffeecat on 2011-05-23
> **mganesh30 said:**
> Hello coffeecat,
 
Thanks for the explanation. However, I do have a slightly old BIOS. What then is your recommendation for partitions & sizes? I do not want to get into a situation where I get GRUB Error 18.

Slightly or moderately? :) BIOSs that can't read beyond 137GB are getting a bit old now, but I can understand your concern. As far as size is concerned, I've seen recommendations for as little as 50-60MB. I think that's too small. I've seen threads where the OP has run into problems upgrading when the boot partition has become full with old kernels. If you are meticulous about clearing out kernels, then about 60MB would be enough. On my Lucid partition  my boot folder contains 106MB of files, but I have 7 versions of the kernel in there - I've been lazy about uninstalling old ones. So 100MB should be plenty, and 200MB will be more than enough. If you have a large HD, then you're not going to miss 200MB, so 200MB gives you a wide margin of safety.

If you are worried about the 137GB BIOS limit, then make your boot partition the first one, or if you have Windows already on sda1, make it the next one making sure that the Windows partition is not too big.

As far as your root partition goes, that depends on what type of software you will be installing, as I mentioned before.

By the way, you won't get a grub error 18 now - that was an error from legacy grub. Ubuntu has been using grub2 since Karmic and you don't get numbered errors.

---

### Post by mganesh30 on 2011-05-23
Dear coffeecat,

Thanks for the most encouraging reply. The reason I was worried about GRUB Error 18 is that after I got that error, the HDD was not being recognized by CMOS making it impossible to reinstall the OS. Anyway, I will set my BIOS Access Mode to 'Large' before installing Ubuntu. Your advice on this please.

I will then make the following Partitions:-

ROOT - 200 MB
SWAP - 2 GB
HOME - Remaining space.

---

### Post by coffeecat on 2011-05-23
> **mganesh30 said:**
> 
I will then make the following Partitions:-

ROOT - 200 MB
SWAP - 2 GB
HOME - Remaining space.

I hope that was a typing error, because what you need is:

boot - ~200MB
root - Whatever
swap - 2GB
home - remaining space.

A root partition of 200MB wouldn't get you very far. :wink:

---

### Post by mganesh30 on 2011-05-23
Thanks coffeecat. But in your earlier post you mentioned that there was no need for a boot partition. So I could have just ROOT, HOME & SWAP

---

### Post by srs5694 on 2011-05-23
Let's go over this again:


[list]
[*]**root (/)** is the main Linux filesystem. Almost everything else is referenced relative to this filesystem, and is mounted on it. If you do a default Ubuntu installation, everything but swap will be stored here, and the partition must be at least 3 or 4 GB in size (I don't recall the precise value). This size requirement can be reduced if you split off other big directory trees, such as /usr. Thus, a 200 MB root (/) partition is way too small, unless you split off several other critical directories into their own partitions.
[*]**/boot** is the directory where the kernel, initial RAM disk, working GRUB 2 files, and a few other files reside. GRUB must be able to read several files in this directory, and GRUB uses the BIOS to read these files, so if the BIOS can't read all of your hard disk, the BIOS must be able to read the files in /boot. The easiest way to ensure this is to split /boot off into its own partition that you place below your BIOS's limit. This partition can be a few tens of MB in size, but I would recommend 200 MB as a good size. (Recall that kernel upgrades use this space, so if your system upgrades the kernel and you don't delete the old ones, you could end up using 100-200 MB of space in /boot.)
[/list]

---

### Post by coffeecat on 2011-05-23
> **mganesh30 said:**
> Thanks coffeecat. But in your earlier post you mentioned that there was no need for a boot partition. So I could have just ROOT, HOME & SWAP

Yes, I did, but you were the one wanting the separate boot partition. You could have just root/home/swap, but your root partition  cannot be as small as 200MB - that was the point I was picking up in my last post.

---

### Post by ratcheer on 2011-05-23
> **mganesh30 said:**
> Thanks coffeecat. But in your earlier post you mentioned that there was no need for a boot partition. So I could have just ROOT, HOME & SWAP

Yes, that will be perfectly adequate. The root partition should not need to be more than 30 GB. Keep all your user data somewhere under /home.

Tim

---

### Post by grubu on 2011-05-23
As there might be no differences I like the fact of having the possibilty of using up to 23 different partitions as logic partitions. So in my opinion there is no issue why I should not devide the complete harddisk-size into less or more
 logic devices for pointing them to some desired linux-paths. The only thing in my opinion would be the difference in the  time that is needed to create some partitions instead of creating one big partition. But splitting into several partitions also gives me a little bit more control I think.

---

### Post by mganesh30 on 2011-05-24
I now have Fedora which has the default partitions as below:-
 
ROOT: 50 GB
BOOT: 500 MB
HOME: remaining space
 
Just thought I could repeat this in Ubuntu.

---

### Post by grubu on 2011-05-24
And they no more have an extra swap by default?
By the way Fedora 15 Final will be out tomorrow but Gnome3 is working nicely at Natty.

---

### Post by mganesh30 on 2011-05-29
During the Partitioning stage it asks me where I should install the Bootloader. The first choice in the drop-down menu is the entire hard disk followed by the partitions that I have created.

Which iis the best place?

---

### Post by coffeecat on 2011-05-29
The first choice is the mbr of the first hard drive, not the entire hard disk. That would be one big bootloader that needed the whole hard drive! :wink:

That's the place for it to go. Installing the bootloader to individual partitions is when you want complicated chainloading between different OSs.

---

### Post by mganesh30 on 2011-05-29
dear coffeecat, that means I have chosen the right on?

---

