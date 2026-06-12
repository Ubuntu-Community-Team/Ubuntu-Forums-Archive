---
title: "Trying to software raid 1 with 2 sata disks on Ubuntu 7.10"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by TimRDuffy on 2007-11-08
Hi, I am new to Linux (though solaris trained) and new to software raid.
I am trying to put together an amd64 based home web server that has just two 750 gb SATA II disks on which the OS and the /home data (photos) to be software raid 1'd. I have read much on this forum to suggest that is the way I should go. 
My disks are recognised by Ubuntu server (or desktop or alternate, have tried 606, 704 and now 710) as being sata disks (calls them SCSI1 and SCSI2) when I set the bios (new amd64 motherboard) to AHCI (but not to the alternative setting of legacy) - which I have read is likely to be a good way to make linux recognise sata disks. 
I follow the how_to set up software raid guidelines (those from ubuntu or even suse linux say the same thing - which is encouraging) and ALWAYS fail at the same place.
I set up the partitions I want: /boot, swap, /, /home and a spare partition for future possible dual booting with ubuntu desktop
on the first disk fine - the partitions are of type RAID.
WheneverI move to the second disk  it would partition it identically as needs to be done before one can choose 'configure software raid' menu option  BUT  the type option menu suddenly does NOT have the RAID type option - it has all the other ones it had with the first disk but not RAID nor LVM.
I have done this so many times with so many variants I feel that either a) I am missing some important undocumented step and am missing some crucuial point somehwere 
or b) actually the system is trying to tell me that it can't actually use raid here with these disks that it calls scsi1 and scsi2. 
Can somebody PLEASE advise me , I have to admit that there is far less good written support for using sata disks with linux and software rainding them than I thought there would be - perhaps I really shouldn't have started with this ideal trying to use Ubuntu?
My sata II disks have red sata cables coming from the 4 sata ports on the motherboard to each hard disk - so I assumed that meant they are on different 'sata' channels and hence good for software raid.
Many thanks,
Tim

---

### Post by evilpenguin on 2007-11-08
I would not claim to be an expert on this subject. I have only used software RAID to assemble arrays of USB flash drives (!) for faster writing. But you do not mention using "mdadm" which is an essential for software raid.

As I recall I did not have to label partitions in any particular way. I just used the /dev entries for the partitions.

Here's a command line I used to make an array of USB drives:

mdadm --create /dev/md5 --auto=md --level=0 --chunk=32 --raid-devices=$NUMDRIVES $DRIVES

Where $NUMDRIVES is the count of USB sticks and $DRIVES is a concatenation of their device names. I have set up an array of SATA drives (using striping with redundancy, I always have to look up the RAID number), but I used the whole drive (/dev/sda, /dev/sdb, etc.) without assembling partitions.

I believe that linux software raid creates its own "private" superblock and that the partition label you set with "fdisk" is tweaked automatically by mdadm.

Anyways, don't put too much store in what I say. Like I said, I played with it and it worked. I haven't had to go back to it in months. I'm no expert. But I do remember that a lot of the documentation out there is OLD, and that "mdadm" is the *current* tool for doing software raid.

I hope this is of some help, if not much...

---

### Post by TimRDuffy on 2007-11-08
Thank you Evilpenguin but this doesn't quite address what I need an answer to so I request that someone try and answer  my query from knowledge/experience of trying to do similar/the same. Recall that the documentation implies when I move to the second disk the menu should allow me to choose raid. Why does it not? Continuing bugs in Ubuntu versions? - or I suspect something far more subtle - like the hardware can't hack it or I am trying to do something completely non-relevant (but this is not implied in how I read  the how-to).
I too have seen mdadm working - but have never managed to get the correct partitons in the pairs from a ubuntu server installation menu so that I can end up with what I currently understand one should do for a such and os +data disk software raid1 i.e. you raid partitions not entire hard disks (as you have done with your usb 'disks') .
Kind regards
Tim

---

### Post by TimRDuffy on 2007-11-15
I hope this will bump this item and maybe give something straightforward for a ubuntu (mdadm tool)  technical supporter to answer:

If I were to simply install my ubuntu server 7.10 lamps installation on one of my empty disks - and then study mdadm command - can I simply once the system is installed create the raid1 mirror of that first disk on the second disk?
Have I been misled by the installation menus into thinking mdadm will only work on partitions that are marked RAID and not on actual working partitions? (still can't usually get the menus to allow setting the second disk as raid whilst using even alternate disk cd - now suspect this is not software error but somehow hardware/bios related - my very new but cheap ATI sb600 based motherboard with 2 sata II 750 Gb disks is is called msi k9agms-fih- I am deliberately not trying to use fakeraid?
Should I simply try that and forget about setting up the raid as I try to install ubuntu?
Many thanks for an answer from somone who knows about using mdadm within ubuntu.
Tim

---

### Post by sickpuppet on 2008-02-08
Hi Tim - 

I'm in the process of setting up RAID 0 using the Gutsy Gibbon 7.10 alternate install CD on a Dell XPS 420 box (with integrated Intel SATA controller fakeraid which I'm planning to bypass) and two 320Gb SATA disks. I came across your post in my research.

You didn't mention which howto you followed - so far, I've found this one to be the most useful:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=408461](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=408461)

You're right in your observation that there's very little clear, up-to-date documentation on how to set up software RAID in Ubuntu.

It seems there are two main hurdles to setting up RAID (doesn't matter whether it's 0, 1 or 5 for the purposes of this discussion):

[LIST=1]
[*]GRUB can't boot from a software RAID partition
[*]Software RAID partitions reside inside existing partitions
[/LIST]

To overcome the first point, you'll need to create a straight ext3 /boot partition, and to overcome the second point, you need to create two partitions of the same size on each of your two disks. These can then be configured as elements to be combined into a single logical RAID partition.

As I understand it, satisfying these two requirements will leave you with a little unused chunk on your second SATA disk of the same size of the /boot partition on your first SATA disk.

I'll let you know how I get on.

(As an aside, I previously set up software RAID5 (using Ubuntu 5.10 Breezy Badger) as a proof-of-concept on a clunky old box with five 9.6Gb SCSI disks. This was much simpler to do once I added a PATA hard drive for the OS to boot from.)

regards
Ben

---

