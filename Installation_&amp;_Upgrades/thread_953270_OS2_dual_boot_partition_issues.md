---
title: "OS/2 dual boot: partition issues"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2008-10-20
When I installed eComStation (aka OS/2), I left space on the hard drive for a later Ubuntu installation, to be a dual-boot set-up.  I have read that in such cases, it is much better to do the disk set-up using OS/2's software, and to then let Ubuntu use the remaining space.  A special issue is making sure the Ubuntu install puts GRUB in the Ubuntu **/boot** partition, not in the MBR, but that is a separate issue.

My problem is this: using OS/2's LVM, I see empty space equalling 81,811 MB (using 1024, that's 79.9 GB, which is about right).  But when I boot up the Ubuntu 8.04 install dvd and get to the disk-partitioning part, it shows me  104.88 GB as free.

Obviously, I am in terror of telling it to start partitioning that "free space", which is larger than the block not partitioned as OS/2 (or the MBR) for fear of destroying my OS/2 installation, which would be--to put it mildly--catastrophic.  (In principle, I could restore, but it would be a nightmare.)

Moreover, using OS/2's LVM, I had already created--within the free space--volumes and partitions of the sizes wanted for the Ubuntu install.

Can anyone give me any idea what's going on here?  Why is Ubuntu reporting 131% of the space OS/2 is?

---

### Post by mdebusk on 2008-10-20
> **owlcroft said:**
> When I installed eComStation (aka OS/2), I left space on the hard drive for a later Ubuntu installation, to be a dual-boot set-up.

Felix Miata's [Disk Partitions, OS/2, & Multiboot FAQ]("http://mrmazda.no-ip.com/partitioningindex.html") helped me tremendously with that.

I feel compelled to add that I multibooted Windows 98 (DOS prompt, not GUI), Windows XP, eComStation, and Ubuntu, and the more I learned Ubuntu the less I booted anything else. The Win98 and eCs partitions are now gone, and I haven't booted XP in months.

---

### Post by owlcroft on 2008-10-20
> **mdebusk said:**
> Felix Miata's [Disk Partitions, OS/2, & Multiboot FAQ]("http://mrmazda.no-ip.com/partitioningindex.html") helped me tremendously with that. . . .

I have seen it, but it doesn't seem to address the problem I am having, which is that LVM and gParted are reporting very different sizes for "free space" (meaning not already used by eCs or the MBR).

---

### Post by guitsy on 2008-10-20
run the ubuntu cd.when partition section comes select manual partiton.then u will be displayed with the partiton table.right click on the empty space format it.come back to previous page.select the option to install in the free space.after the installation grep will show both os.:guitar:

---

### Post by mdebusk on 2008-10-20
> **owlcroft said:**
> I have seen it, but it doesn't seem to address the problem I am having, which is that LVM and gParted are reporting very different sizes for "free space" (meaning not already used by eCs or the MBR).

I do remember this being a problem, and seem to recall it's the fault of the OS/2 LVM. The recommendation is to back up your OS/2 partition, repartition and format with DFSee, restore OS/2, and install Ubuntu. That bypasses the whole mess.

---

### Post by owlcroft on 2008-10-23
> **mdebusk said:**
> I do remember this being a problem, and seem to recall it's the fault of the OS/2 LVM. The recommendation is to back up your OS/2 partition, repartition and format with DFSee, restore OS/2, and install Ubuntu. That bypasses the whole mess.

Not so easy a thing to do.  I have all my data backed up at a remote location (though to restore it all by download would take a monstrous amount of time), and it includes what data I need to re-create the OS/2 install, but that is always a dicey thing.  I am thus hesitant to try that route.

I also wonder why it should be necessary.  As best I recall, though I can't locate the source any more, the consensus seemed to be that unlike the case with Windoze, the best approach was to use OS/2 to set up the disk space, then just format as required at the time of Ubuntu install.

Now for the *really* odd part: a little while ago, I again rebooted the Ubuntu Install CD, but as "try it" not install it, and when it came up, I tried **sudo gparted** and lo! I saw something looking much like the correct information.  (Again: I had already made partitions of the right sizes and types--primary vs. logical--using OS/2); regrettably, thinking that all was somehow now well, I then shut down and booted back into OS/2.  On again booting the CD into Ubuntu, however, gparted was back to showing that strange 104.88 GB figure, which seems to correspond to no existing partition or combination of existing partitions.

Curiouser and curiouser . . . .

Any other ideas?

---

### Post by owlcroft on 2008-10-23
Well, well.  I tried a somewhat different Google search, and look what I found:

[http://ubuntuforums.org/showthread.php?p=5998057#post5998057](http://ubuntuforums.org/showthread.php?p=5998057#post5998057)

While this may not be exactly my problem, it might.  As one comment there reads, *I have a similar problem. I can still change partitions using windows vista and fdisk but gparted does not recognize my partitions.*

There are other related notes to be found on other pages: [I][gparted] has wrecked the partition table on my OS/2
boxes more than once. While I can repair the damage, I really don't want to have to do so...  What is provided now works just fine so far as I'm concerned. I'd much rather have a working text-mode interface than something which is going to damage my partitions, thank you very much![/I]

***If*** it turns out that it is gparted that is the problem, however would I do an install since that is the partition editor the install uses--is there an option to use some other?

---

### Post by mdebusk on 2008-10-23
> **owlcroft said:**
> I have a similar problem. I can still change partitions using windows vista and fdisk but gparted does not recognize my partitions.

Does parted/gparted recognize HPFS? It didn't when I last had a HPFS partition. I didn't use LVM at all. Maybe IBM's LVM is a stranger to parted/gparted too.

---

### Post by mdebusk on 2008-10-23
> **owlcroft said:**
> Now for the *really* odd part: a little while ago, I again rebooted the Ubuntu Install CD, but as "try it" not install it, and when it came up, I tried **sudo gparted** and lo! I saw something looking much like the correct information.

What I would do is go ahead and install Ubuntu. It's likely to work, and if it doesn't, you have to start over... which is the only other option I see anyway.

---

### Post by owlcroft on 2008-10-23
> **mdebusk said:**
> Does parted/gparted recognize HPFS? It didn't when I last had a HPFS partition. I didn't use LVM at all. Maybe IBM's LVM is a stranger to parted/gparted too.

But that's not the issue.  If gparted doesn't know what the HPFS partitions are (which I doubt--it should at least see that *something* is occupying the space), it should hosw me, I would think, either the entire disk as available (c. 235 GB) or else the area not occupied by the OS/2 partitions (c. 80 GB).  Instead, it shows me 104.88 GB unpartitioned, unused, un-everything'ed, and that's all she wrote.  

If I started to install on that wildly incorrectly sized area, who knows what disasters would befall?  Hence my reluctance to rely on gparted.

---

### Post by mdebusk on 2008-10-24
> **owlcroft said:**
> Instead, it shows me 104.88 GB unpartitioned, unused, un-everything'ed, and that's all she wrote.

Now I understand, and that's a horse of a wildly different color. And I know nothing of how parted determines what is on a disk, so if you don't want to start from scratch, I have no solution.

Well, maybe one. Have you considered installing a second hard disk just for Linux? You could give that 80 gig back to OS/2 and have plenty of space to stretch out on Linux as well.

---

