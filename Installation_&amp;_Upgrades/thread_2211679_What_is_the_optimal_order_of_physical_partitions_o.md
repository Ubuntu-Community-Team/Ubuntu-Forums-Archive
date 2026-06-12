---
title: "What is the optimal order of physical partitions on a hard disk?"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by rewyllys on 2014-03-17
As a result of major hardware failures in my desktop system, I'm in the position of having to consider how best to organize a new 2TB hard drive for my system.   

 I want to have three partitions for Operating Systems (Current and 2 Alternatives), one partition for Swap, and one partition for Home.  I plan on allocating 40GB to each of COS, AOS1, and AOS2; 20GB to Swap; and the remainder of the 2TB to Home.  Thus I'll need three primary partitions, plus 2 logical partitions within an extended partition.  

 Having read various recommendations for what should be placed at the beginning of a hard drive and what should be placed at its end, in order to minimize the time required for moving the writing head(s) and reading head(s) in typical usage, I am wondering: What is the best physical layout of the various partitions I'll need?  
 
 For example, is the optimal order this: Swap, AOS1, AOS2, COS, Home (e.g., as in sda1, sda2, sda3, sda6, and sda7, respectively)?

Or is the optimal order something else?  Your advice will be much appreciated.

---

### Post by TheFu on 2014-03-17
Great that you have a plan.  

In theory, the fastest part of the HDD is the outside according to my google-fu. 
* [http://wiki.answers.com/Q/Which_part_of_a_hard_disk_moves_the_fastest_past_the_read_and_write_heads_and_therefore_is_the_most_desirable_location_for_commonly_used_files](http://wiki.answers.com/Q/Which_part_of_a_hard_disk_moves_the_fastest_past_the_read_and_write_heads_and_therefore_is_the_most_desirable_location_for_commonly_used_files)
* [https://superuser.com/questions/159890/does-the-order-of-partitions-matter](https://superuser.com/questions/159890/does-the-order-of-partitions-matter)
That means putting swap there.

Honestly, caching is so much more important that I do not worry about any partition order on my HDDs.  If I need something faster, using an SSD is a simple fix.
20G of swap is HUGE - more than almost anyone not running HUGE servers needs, IMHO.  2G is fine unless you sleep/hibernate. Then the swap size should match the RAM amount. This ain't Windows.

Having 3 OSes that you can change booting between is smart too. I do it on my XBMC/plex machine. There is a small risk if the HOME is shared with the same userid should each OS have a different DE. Corrupted DE environments aren't any fun to solved. Good backups are invaluable or just use a different userid for each boot.

I would also suggest that you add another partition for large data.  This will make backups easier.  OS, apps, settings and documents need a daily, versioned backup, but large media files do not.  A simple mirror is fine for media files, use parity tools like par2 if you want to ensure any corruption is recoverable or something like SnapRAID. Keeping those two sorts of data separate makes backups much easier.

I consider 20G for an OS overkill.  My primary desktop has 15G total for OS, apps, settings, documents and programming files. I do RoR and Perl along with lots of presentations. If you do Java, more would be mandatory.

If you plan to have any virtualization - and it would be a shame not to on any system with 12G or RAM or more - then /var will need to be larger, much larger, to hold the virtual machine vHDDs.  Just sayin'.  Or you could put the VMs elsewhere.

Also, if you are unsure what to do with all that storage, use LVM and delay allocation until needed. LVM will let the disk additions be added ad needed.

So ... the order of partitions isn't what matters, it is the placement on the HDD.  gparted and parted will let you control that.

Hopefully, others will provide different recommendations too so you can pick which you like best.

---

### Post by rewyllys on 2014-03-17
[SIZE=3]TheFu, thanks very much for your comments.  [/SIZE] 
 
 [SIZE=3]As I understand them, you're saying: (a) that the Swap partition should be on the outside of the hard drive, and, hence, should be the first partition created; and (b) that the order of the other partitions does not matter too much, compared with such speed-affecting factors as the total amount of RAM.[/SIZE]
 
 [SIZE=3]I appreciate your suggestion of using a separate partition for media files. It makes good sense, and I'll incorporate that into my system plan.  I assume that doing so will require my using Gparted to assign say, sda8, to be used as “/home/<username>/media”. Is that correct?[/SIZE]
 
 [SIZE=3]With respect to virtualization, I've been using Windows 7 within a VirtualBox virtual machine on the system that just died.  And I assigned this virtual machine 100GB of space, which I thought was part of my /home/<username> partition, rather than being part of /var within root's partition, i.e., the partition that I called COS in my initial post.  [/SIZE] 
 
 [SIZE=3]Have I misunderstood where a virtual machine's Virtual Hard Drive is located?  And if so, how can I do what you had in mind when you wrote, “Or you could put the VMs elsewhere”?[/SIZE]
 
 [SIZE=3]Again, many thanks for your help.[/SIZE]

---

### Post by mansonfan78 on 2014-03-17
Personally, I would have a separate partition for your data.  This way you can have three different user accounts in /home (one for each OS) and have them share documents, etc on the data partition without causing any configuration conflicts.

---

### Post by rewyllys on 2014-03-17
> **mansonfan78 said:**
> Personally, I would have a separate partition for your data.  This way you can have three different user aeaccounts in /home (one for each OS) and have them share documents, etc on the data partition without causing any configuration conflicts.
Thanks for your interesting suggestion.

Please help me further by telling how to implement your suggestion, i.e.,  in terms of how to use Gparted to set up such a data partition/

---

### Post by mansonfan78 on 2014-03-17
You can create a new partition as ext4 and there should be a mount point option of /data (if I remember correctly).  Personally I'm dual booting with Windows so my shared data partition is ntfs, never done it with ext4.  By the way, if you do it this way your /home wouldn't need to be very large at all (10 gig would be more than enough, even for three user accounts).

---

### Post by TheFu on 2014-03-17
[http://hddscan.com/doc/HDD_Tracks_and_Zones.html](http://hddscan.com/doc/HDD_Tracks_and_Zones.html) is interesting.
I'd always assumed that sector 0 was on the inside, thus slowest. I don't honestly know which ring of the platters it is.

Oh ... virtualbox?  Then the VMs are probably stored inside your HOME. I've never used that on a Linux host after it crashed on a new box here.  Been running  KVM for a few years now. Ran vbox on Windows for years - even gave presentations about vbox optimization in a few countries. KVM VMs, when using virt-manager, normally go into /var/lib/libvirt/ .... somewhere. I don't recall where Xen or qemu put theirs by default. I used to fight against that default, then just decided to mount extra storage there for the VMs.

I would NOT mount the extra media partition under HOME.  It would defeat the ability to easily handle backups in the 2 different methods. I place data like media on /D, That way recursive backups don't get mixed up between the simple mirror and the 60-90 day versioned backups of HOME.  There is nothing special about a mount location - just that it already exists and it is a directory.  You can create a mount point ANYWHERE with locally connected storage.  ```
sudo mkdir /D
``` - for example.

With all that storage, using LVM makes sense and removes the problem about guessing where storage will be needed at the beginning. Add more to whatever partition needs it later, as needed.  Just don't pre-allocate it all.

---

### Post by rewyllys on 2014-03-17
Thanks again, TheFu.  Your comments have helped my understanding of these partitioning matters.

A few minutes ago, I came across a post, #7, by OldFred in [this thread]("http://ubuntuforums.org/showthread.php?t=2199504&highlight=data+partitions%2C+link").  It appears to offer a wealth of information on partitioning. I'll be avidly studying some of the links in OldFred's post, for which I herewith thank him.

---

