---
title: "fresh install - partitioning for the future"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by lecterror on 2010-08-30
Hi everyone!

At the moment, I have one Ubuntu laptop, and one Windows PC. Since one of the disks is showing some signs of age, I've decided to buy a new disk (WD 1.5TB) and install Ubuntu. 

No more Windows!:popcorn:

However, since this is my primary workstation, I've decided to put some thought into it. While I can "play" with my laptop OS, I want my primary workstation to be stable and reliable. Even more importantly, I want to make sure that upgrades will be as smooth as possible.

On my laptop, I've created three partitions, root, /home and swap. Upgrades seem to be relatively smooth. Are there any other recommendations for separate partitions, for example, would it be a wise thing to separate /etc as well? ..or any other folder for that matter? Some say that /boot should also be separated...*[Citation needed]*:)

I'll be using the machine for web development mostly (LAMP), web design.. if that affects anything. Of course, that's not the only thing I'll be doing, but I thought it wouldn't hurt to mention anyway.

Additional question: Which file systems would you recommend for root, /home, etc..? ext3, 4, something else? ext4 seems to be recommended by Ubuntu folks, is it reliable?

Thanks in advance!

---

### Post by dino99 on 2010-08-30
boot with partedmagic and follow this little help if you want to install ubuntu:

prepare your hdd first, ex4 is the best stable to use nowadays:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by lecterror on 2010-08-30
Thanks for your fast response.

What are the advantages of using partedmagic instead of the "default" Ubuntu partitioner during install? Surely I should end up with the same configuration regardless of the tool used?

---

### Post by srs5694 on 2010-08-30
Note that some WD drives use the "Advanced Format" system, which requires special care when partitioning lest you run into potentially serious performance issues. I describe the details in [this article on IBM developerWorks.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) If in doubt, I recommend you pre-partition on 4096-byte boundaries using partitioning tools you understand.

As to the partitions themselves, the three-partition design you propose is probably adequate. You should *never* split /etc off of root (/). The same applies to /bin, /sbin, /lib (and/or /lib32 or /lib64, if present), and /dev (except insofar as udev creates a virtual /dev filesystem during the boot process). All of these directories contain files that are critical to the boot process, so the system won't boot if you split them off. For instance, /etc/fstab contains the list of partitions and their mount points, so putting /etc on a separate partition robs the system of the ability to determine where to mount partitions. Similar, /sbin/mount is used to mount partitions.

Splitting /boot off makes sense in some configurations. It simplifies some LVM and RAID configurations, and it was necessary on some old systems that had BIOSes that couldn't read past a certain point on the disk -- putting /boot early on the disk ensured that the kernel could be read by a boot loader that relied on the BIOS to read the disk. This last factor hasn't been an issue for years, though, except of course on old computers (roughly ten years old or so, IIRC). Arguments can be made for splitting off /usr, /usr/local, /opt, /tmp, /var, and others; however, these apply mostly to specific configurations, such as servers that write a lot of data in /var.

You might, though, want to consider using LVM. This will enable easier filesystem resize operations in the future. If you leave a bit of unallocated space in the volume group now, you could use it later to install a future version of Ubuntu (or another Linux distribution) alongside whatever you install now in order to perform parallel testing of the new system with the old one. Once you're satisfied the new system works to your satisfaction, you can delete the old one. Of course, you can do this with regular partitions, too, but with LVM you can more easily adjust the sizes of the new and old installations, add filesystems should you decide you need them, etc. I don't want to say you should definitely use LVM -- it does add complexity and it's got its learning curve. You might want to look into the possibility of using it, though.

---

### Post by lecterror on 2010-08-31
Well, that was detailed enough :)

It was only *after* I posted my question is discovered amongst the many results in my search that /etc should not be separated.. Typical! :D This will bring more pain if I ever have to make a complete reinstall, with network configuration, apache, etc..

Is there a way to check if my partitions are properly aligned? I'm not sure if I did everything right. Hardware was never my cup of ale I'm afraid, and managing it on Linux is even more difficult because of my unfamiliarity with available tools.

Speaking of disks...do you think it is worth switching on "Spin down hard disks when possible" option? I've read a couple of threads about this, and it seems like there is no consensus..some say that spinning up and down brings more wear and tear than continuous running, regardless of heat produced.:confused:

I admit I have no idea what LVM is, but once I've "settled in" I might take a look at it. It does seem like a lot more trouble than a simple VirtualBox setup :)

Thanks for your tips!

---

