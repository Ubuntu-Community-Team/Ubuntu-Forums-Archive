---
title: "Installing on partition"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by GEOvanne on 2011-05-07
Sorry if this question has been asked already, but all the articles I've read is filled with technical jargon that I don't understand.

I have 2 hard drives, I want to install ubuntu on the slave, but I also want to save some of my files from the primary (which is windows) unto the slave.
My friend suggested that since I'm going to do this I should install in partition.

So I'm creating a new partition and I'm stuck here.
I have the new partition type set to primary and gave it 20 gigs.
I have the location for the partition at the beginning (does it matter where I set it?)
I have it set to use Ext4
And I'm not sure what the mount point is or what should go there.

So right now I'm stuck here until my friend answers his phone :(


Also, after I have these things set, what else is there that I should know about during the installation process?

---

### Post by mikewhatever on 2011-05-07
The mount point should be the forward slash (/), which designates the Ubuntu system partition, also known as the root partition.

---

### Post by deltacomp on 2011-05-07
No it doesn't really matter where on the hard drive you put the partition. As MikeWhatever said, the / is main partition and will be the area with the OS, so select / as the mount point. I would recommend you install Ubuntu on the 20 gig partition and give yourself a small swap area, maybe a couple gigs or less. Ubuntu should find your other HD and give you the option of either booting into Windows or Ubuntu.

---

### Post by oldfred on 2011-05-07
Herman has lots of detail, not as complex as it may seem since he explains so much.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If your BIOS lets you choose which drive to boot, you want to install grub2's boot loader to sdb or whatever drive the external is. It will probably show it by drive brand name/type.

---

### Post by GEOvanne on 2011-05-08
Ok guys, I installed it, thanks for the help.

---

