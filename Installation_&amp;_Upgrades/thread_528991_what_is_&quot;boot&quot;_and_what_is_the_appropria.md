---
title: "what is &quot;/boot&quot; and what is the appropriate size for it"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by jokefake on 2007-08-18
is there a way to install ubuntu in such a way that, the grub will stay intact even after reinstalling win xp, if the system is dual boot.
also
when u decide to edit your partition manually during installation, you can create a mount pt "/boot".  what exactly does is mount pt do, and what is the appropriate size for it.

thanks

---

### Post by Pumalite on 2007-08-18
'/' mounts your system.
A good scheme is: 10 GB minimum for '/', 500 MB to 1 GB swap and the rest for /home.

---

### Post by logos34 on 2007-08-18
> **jokefake said:**
> is there a way to install ubuntu in such a way that, the grub will stay intact even after reinstalling win xp, if the system is dual boot.
also
when u decide to edit your partition manually during installation, you can create a mount pt "/boot".  what exactly does is mount pt do, and what is the appropriate size for it.

thanks

windows will overwrite grub on the mbr no matter what you do, you can easily restore grub afterward using the ubuntu live or alternate install cd.

You really don't need a separate /boot unless you're constrained by the 1024 cylinder Bios limit or you're booting a number of different linux distros.  ~50-100 MB is average size from what I've seen

---

### Post by ruibernardo on 2007-08-18
This is just to tell that there is a certain advantage in using a separate "/boot" partition (*for advanced users?*).

JFS or XFS are better for disk performance. They have less problems and checks times (and time spent on checks) than ext3. So, If you use XFS for "/" (root) and "/home" you MUST have a "/boot" partition. This is necessary because Ubuntu/Linux can't boot directly to XFS/JFS partitions. So, you have to create an ext3 "/boot" partition.

But using a "/boot" partition implies a more "complicated" partition mapping, because if you (still) have a Windoze partition, you have to create ALL other partitions (other than windowz) in an extended partition to avoid problems: windows+boot+root+home+swap=5 partitions; maximum primary partitions on a disk=4, so an extended partition is needed.

500 MB is more than enough on /boot. It allows you to have many kernel images (the files needed by linux to boot and installed on each kernel updates) without any problem.

If you do a fresh install, you can set all this on manual partitioning. It's easy. Create an extend partition in the free space on disk, and inside it create a /boot partition in ext3 format; create all the others ("/" and "/home") partitions as XFS. Done. All the rest is done as usually.

My 2 cents.:popcorn:

---

### Post by logos34 on 2007-08-18
> **epimeteo said:**
> JFS or XFS are better for disk performance. They have less problems and checks times (and time spent on checks) than ext3. So, If you use XFS for "/" (root) and "/home" you MUST have a "/boot" partition. This is necessary because Ubuntu/Linux can't boot directly to XFS/JFS partitions. So, you have to create an ext3 "/boot" partition.

Interesting.  Didn't know that linux can't boot directly to XFS and needs separate /boot (wonder why?).  From what little I've heard about XFS it does perform better but only if you work with very large files.  How does it compare to the new ext4?

---

### Post by ruibernardo on 2007-08-19
I should have said "GRUB" instead of "Ubuntu/Linux". GRUB doesn't like XFS on boot. At least until now. Feisty was shipped with GRUB 0.97 ([http://oss.sgi.com/projects/xfs/faq.html#grubwork](http://oss.sgi.com/projects/xfs/faq.html#grubwork)).

In the "Desktop CD" you can't install LILO and Ubiquity don't allow you to install with a /boot with XFS, so you have to use the "Alternate CD" to install a XFS on /boot partition and LILO.

You can avoid all this trouble of using LILO or the "Alternate CD" by creating /boot as a etx3 filesystem. This also ensures that even if you change from LILO your system will always be bootable.

IMHO, I do notice a _great_ improvement on disk speed, and not only with little files. Also, booting is quicker than with ext3 or ReiserFS and all disk operations are faster.

Ext4 is a mystery to me, I've never used it.

NOTE: apart of the ext3 /boot partition *thing* there is another difficulty about XFS. For those who like to expand and shrink partitions frequently, XFS don't allow to shrink, only expand.

---

### Post by logos34 on 2007-08-19
> **epimeteo said:**
> I should have said "GRUB" instead of "Ubuntu/Linux". GRUB doesn't like XFS on boot. At least until now. Feisty was shipped with GRUB 0.97 ([http://oss.sgi.com/projects/xfs/faq.html#grubwork](http://oss.sgi.com/projects/xfs/faq.html#grubwork)).

In the "Desktop CD" you can't install LILO and Ubiquity don't allow you to install with a /boot with XFS, so you have to use the "Alternate CD" to install a XFS on /boot partition and LILO.

You can avoid all this trouble of using LILO or the "Alternate CD" by creating /boot as a etx3 filesystem. This also ensures that even if you change from LILO your system will always be bootable.

IMHO, I do notice a _great_ improvement on disk speed, and not only with little files. Also, booting is quicker than with ext3 or ReiserFS and all disk operations are faster.

Ext4 is a mystery to me, I've never used it.

NOTE: apart of the ext3 /boot partition *thing* there is another difficulty about XFS. For those who like to expand and shrink partitions frequently, XFS don't allow to shrink, only expand.

Well, you've definitely piqued my interest...I'm putting this in my todo list.  I read over the project FAQS and I will be doing a little more research on this.

Too bad you can't shrink partitions online, and it appears you can only expand to the *right*. (I do a lot of partition tinkering/resizing).  But no matter.

So let me get this straight: if I want to use grub (I have 0.97), then I must make a separate /boot?  Do I format it as ext3 or XFS?

---

### Post by ruibernardo on 2007-08-19
> **logos34 said:**
> 
So let me get this straight: if I want to use grub (I have 0.97), then I must make a separate /boot?  Do I format it as ext3 or XFS?

Yes logos,

you make a separate /boot partition and format it as ext3, then format (all) the other(s) as XFS.

About the size of /boot partition. I've said that 500MB is more than enough. It's really too much. You are right about it: ~100MB is enough. My 500MB /boot partition has only 49MB ocupied, with 2 kernels images installed. I will reduce its size on my next install.

---

