---
title: "Vista &quot;Data' Partition, Can I resize?"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by bobnutfield on 2008-03-31
Hello Everyone,

After a lot of hair pulling and grief, I have finally found that Ubuntu 8.04 (Beta) will recognize my sound card and enable me to actually HEAR IT!  About a dozen other distros would not, even though they loaded the correct drivers.  Embedded wireless still doesn't work but a cheap USB Belkin does.

So, I am ready to install Hardy as a dual boot with Vista.  I have two questions if someone would  be so kind as to share your knowledge.  I have studied long and hard on the dual boot issue with Vista, and these are my questions:

1.  This is a new Toshiba laptop and came with Vista pre-installed.  It is an 80GB hardrive with three current partitions:

         sda1    Vista Recovery      5GB
         sda2    Vista Program        35GB        16GB free
         sda3     Data   (Vista)         35GB           85MB   used       34.5GB free

The "Data" partition is where I would like to install Hardy.  For some reason, Vista decided to locate the Recycle Bin on this partition, along with a couple of other folders called desktop.ini and and one with .tag file extension.  If I resize this partion to about 5GB to make about 29GB available for Hardy, what affect will this have on Vista?  This require the creation of a fourth partition sda4 which will also be a primary.

2.  Has anyone experienced any problems dual booting with Vista after resizing these types of partitions?  

Even though Hardy is still in Beta, I have been running it from the live CD for a while now and it looks stable enough to install.  I am assuming when the final stable release comes out in April that the Hardy repos will upgrad my system accordingly.

Any replies are greatly appreciated.

Regards

Bob

---

### Post by aashay on 2008-03-31
Windows includes a folder $RECYCLE.BIN on all the partitions. So i doubt the data partition exclusively contains the recycle bin. As far as resizing the partition goes, that wouldnt cause any problem at all. ALthough the vista recovery partition on sda1 might cause problems when you get to installing grub. And also, usually a single partition is kept primary. all others marked as logical.

---

### Post by bobnutfield on 2008-03-31
Thank you for your response.  I had not thought of the recovery parttion also including the MBR.  Surly, with the number of people dual booting with Vista there is a way to do it.

Any thoughts?

Bob

---

### Post by bobnutfield on 2008-03-31
I just ran Gparted and noticed there is 1.00mb of unallocated space on the very front of the drive.  Is it possible this is the MBR?

Bob

---

### Post by logos34 on 2008-03-31
you can't see the MBR--it's a tiny bit of the first sector of the hdd, only 512 bytes to be exact, which includes boot record and partition table. 

Another potential grub problem besides the one referred to by aashtray is discussed [here]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo#head-e746e1f17e0fc71f1c95142f2558412cd6b3afe2"). 
(there's lot's of other helpful info on that page).  There's a small chance you'll have to use easybcd to dualboot.  

But the immediate problem, looking at your list of partitions, is that you already have three, and when you install ubuntu you need a minimum of / and /swap.  So you're going to have to convert that data part. into an extended and stick linux inside.

---

### Post by NightwishFan on 2008-03-31
You can resize partitions using Vistas built in disk management. Right click on my computer and hit manage.

---

### Post by bobnutfield on 2008-03-31
Thanks for the replies.  I had no idea that Vista would make it so hard to dual boot.  I have done it with XP dozens of times with no issue.  But, then, this is a new laptop and Vista pre-installed.  

If given the chioce during installation, I would elect NOT to have a swap partition as I have 2GB memory which has always  been sufficient in the past.  Surly someone has had the same issues with a new laptop before, and if anyone reads this post, please advise me how you handled a dual boot.  I did not receive an installation cd with this laptop (just the typical recovery cd), so I would rather not bork my Vista installation just yet.  

I have read in a number of places that Vista will only let you use its partitioner and I have resized the data partition to allocated 18GB of unused space.  I cannot see any option in the Vista repartitioner to create logical partitions.

Anyone have any advice?

Bob

---

### Post by aashay on 2008-03-31
afaik you would have to delete your data partition and make a extended one in its place. yu can then add logical partitions to the extended one

---

### Post by logos34 on 2008-03-31
> **bobnutfield said:**
> I have read in a number of places that Vista will only let you use its partitioner and I have resized the data partition to allocated 18GB of unused space.  I cannot see any option in the Vista repartitioner to create logical partitions.

You can always use **Gparted** on the ubuntu live cd to create an extended partition out of the freed space, then make an ext3 logical partition inside for /.  And a /swap if want (which, contrary to the confusing impression left by my previously remarks, does not have to be a primary partition).  Or if you still don't want a swap, that's ok too (but you just won't be able to hibernate).

---

### Post by stchman on 2008-03-31
> **bobnutfield said:**
> Hello Everyone,

After a lot of hair pulling and grief, I have finally found that Ubuntu 8.04 (Beta) will recognize my sound card and enable me to actually HEAR IT!  About a dozen other distros would not, even though they loaded the correct drivers.  Embedded wireless still doesn't work but a cheap USB Belkin does.

So, I am ready to install Hardy as a dual boot with Vista.  I have two questions if someone would  be so kind as to share your knowledge.  I have studied long and hard on the dual boot issue with Vista, and these are my questions:

1.  This is a new Toshiba laptop and came with Vista pre-installed.  It is an 80GB hardrive with three current partitions:

         sda1    Vista Recovery      5GB
         sda2    Vista Program        35GB        16GB free
         sda3     Data   (Vista)         35GB           85MB   used       34.5GB free

The "Data" partition is where I would like to install Hardy.  For some reason, Vista decided to locate the Recycle Bin on this partition, along with a couple of other folders called desktop.ini and and one with .tag file extension.  If I resize this partion to about 5GB to make about 29GB available for Hardy, what affect will this have on Vista?  This require the creation of a fourth partition sda4 which will also be a primary.

2.  Has anyone experienced any problems dual booting with Vista after resizing these types of partitions?  

Even though Hardy is still in Beta, I have been running it from the live CD for a while now and it looks stable enough to install.  I am assuming when the final stable release comes out in April that the Hardy repos will upgrad my system accordingly.

Any replies are greatly appreciated.

Regards

Bob

Vista has it's own partition shrinker.  Try it first.

---

### Post by Pumalite on 2008-03-31
Check this guide:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
These are also useful:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

