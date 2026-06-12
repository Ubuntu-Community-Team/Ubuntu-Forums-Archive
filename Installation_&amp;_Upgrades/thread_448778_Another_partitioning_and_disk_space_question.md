---
title: "Another partitioning and disk space question"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by mousejunkie on 2007-05-19
Hi,

I've been us MS OS's for about 20 years and played a bit with Linux instalattions. So basically all I know is how to spell it. Ubuntu Studio is something I have been waiting for since the mid 90's.

I have a 100GB drive in my Laptop. partiotioned for windows as follows:

c: system
d: placeholder (minimum size partition that I had to keep so my drive letters would not get messed up after making some major changes)
e: temp and scratch disk (has to stay as well)
f: and g: data partitions

I would ike to resize my f: and g: partitions (using partiition magic) and create free space for Ubuntu Studio at the end of the disk.

Questions: 

Not taking into regard the amount of space I need for audio, video and temporary files/folders for those (I'll use as much as I can free up from my current windows data partitions), how much Space do I need for a full installation of Ubuntu Studio?

What should I format the space at the end of the drive as before installing and can I just tell the installer "use all that space in the new partition and create all the necessary linux partitions there"

Can I resize/move the linux partitions later like I can with partition magic under windows?

Can I just leave all the data on my f: and g: partitions which are ntfs so I can read/write on them from Ubuntu?

I know this is almost like asking to be spoon fed but I haven't really been able to find the answer to my questions. There is a similar question here: [http://ubuntuforums.org/showthread.php?t=439583&highlight=Another+partitioning+disk+space+question](http://ubuntuforums.org/showthread.php?t=439583&highlight=Another+partitioning+disk+space+question), but I can't really extract the information I need. Many thanks from a noob :confused:

---

### Post by rillip on 2007-05-19
You can leave them as NTFS, but one of them will have to be formated for the root partition.  Keep in mind that four physical partitions (not logical) is the limit, so you're going to have issues with this setup.

My recommendation: combine the data on F and G.  Format G and make logical partitions for root, home and swap. This isn't ideal, since they'll all be on the same actual partition, but you've got a difficult setup.  I'd leave F alone and let it be NTFS for you to work with in both.  If you have problems with getting that working (there are extra steps!), you can format as Fat32.  This "just works" for almost everyone.  ext3 is now usable in Windows too, but again, there is some work involved.

The other option would be backup F and G, delete them both.  Create a partition with logical partitions F and G for your Windows, then use the remaining space to create a partition with logical partitions for root, home and swap.  Once again, they're all on the same partion, it's only a matter of whether you have F and G or just F.

I do not know if Partition Magic can resize Linux partions; I've never used it. Gparted can resize them.  You'll have to boot from the live CD I think, but it can do it.  The Ubuntu LiveCD can also do it - just use Gparted, or go through the installation process and chose to manually edit the partitions.  Once changes are applied, you can cancel install and have no ill effects.

Gparted can also resize NTFS when booted from LiveCD (that's how I installed Kubuntu) but for some reason I can't change them when booted from the HDD. *shrug* Probably is a way, but I haven't been motivated enough to look.

---

### Post by mousejunkie on 2007-05-19
Thanks for the reply. Not what I was expecting but it has helped... I hope.

From what you have written and doing more searching afterwards,  I think the following is the best (It'll require a bit of work under windows but fortunately I know how to do it):

1. Leave my c: (primary) partition as is
2. "Create" unallocated space after the c: partition
3. Create a primary ntfs partition (extended with two logical:frequently changed data/permanent data) after the unallocated space for shared data
4. Install Ubuntu Studio in the unallocated space
5. Install NTFS-3G

One question still remains: How large should the unallocated space for a full install of Ubuntu Studio be?

---

