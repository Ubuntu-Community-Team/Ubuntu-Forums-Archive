---
title: "Unable to reinstall Ubuntu"
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by sumithar on 2015-04-14
In a different thread I had posted about issues I was having with logging in but since I am not getting any responses there, I thought I'd try to reinstall my Ubuntu overlaying the one I have.  But when I try this it gives me a message that "No operating system is detected on this computer"[ATTACH=CONFIG]261307[/ATTACH]  But I have both Windows and (a semi working) Ubuntu installed on this.

I chose the "Something Else Option" in the hope I could pick the partition I wanted to install it in.  Now I get a screen showing that no partitions exist. 

When I click on the New Partition Table option it shows that I have no partitions currently
[ATTACH=CONFIG]261309[/ATTACH]

Which makes no sense as you can see from the gparted display, I have no shortage of partitions![ATTACH=CONFIG]261308[/ATTACH]

I absolutely don't want to wipe my disk to reinstally Ubuntu- it will be a lot of work to back everything up and restore them.

Any thoughts?

Thanks!

---

### Post by Bucky Ball on 2015-04-14
Everything looks fine to me. In your second screen shot it is asking where you want to store your boot loader and yes, you do want it to go to sda. It is NOT asking you where you want to install Ubuntu.

Click okay when you get to that second screen which asks where you want the bootloader. That is what that screen is supposed to look like as it is only looking at disks, not partitions, and I'm assuming you only have one disk in the machine: sda.

---

### Post by sumithar on 2015-04-15
Hi Bucky Ball, 
If only things were that easy :)  I clicked OK like you recommended and it says there is something wrong with the partitioning.
[ATTACH=CONFIG]261323[/ATTACH]

But if I go back and try to fix this by clicking on "New Partition table" it threatens to wipe out existing partitions (or at least so the message seems to me)
[ATTACH=CONFIG]261325[/ATTACH]

Thanks!

---

### Post by dino99 on 2015-04-15
you seem having miss something while partitionning the / partition: it have to be declared as / (root) and with the 'boot' flag
and it have to be a format supported by linux (mostly ext4). Note that the hdd can only support 4 primary partitions, so set at least 1 extended partition which then can support other partition into it.
note that windows wants, if im not mistaking, to be installed into the first partition.

---

### Post by Bucky Ball on 2015-04-15
As above.

Start again>choose 'Something Else'>create partitions on the drive for Ubuntu. It does look like you've missed a step or two which is why it is complaining about no root partition set (you need to create a / partition prior to this screen).

/ = root; where the OS lives - with a separate /home partition 20Gb is plenty, if no /home and not linking to existing directories in existing partitions, large as you can.
/ = /swap; similar to a Win pagefile (but a partition) - if not hibernating, 2Gb is fine. 

You can also create a /home partition for all your personal data or link later from the /home directory inside the / partition to existing folders on existing data drives/partitions. All the mount points are defaults in the partitioning section of install. Make the partitions EXT4 and choose 'swap space' for the filesystem of /swap. 

Have a look [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") and [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343370#343370") for further details.

* I did notice something in the third screenshot in your first post that may be causing an issue. You have three primary partitions and an extended partition. That is your limit (four partitions of any kind on the one physical drive) unless you're using EFI. Your unallocated spaces are both outside of the extended partition so can't be used as you need two more partitions making six all up. 

I suggest you expand the extended partition to use the unallocated space at the end of the disk (use all the disk) and install / and /swap to the unallocated space which will not be inside the partition.

---

### Post by sumithar on 2015-04-15
Thanks for your continued patience

"you need to create a / partition prior to this screen"...
Where would I create this?  I wasn't given a place to do this.

"create partitions on the drive for Ubuntu"- 
As I indicated it looks like it will wipe my existing partitions out if I try this and I'd rather not do that.

I checked out those links.  The first is for when the disk is new and empty.
The 2nd kind of corresponds to my situation in that there is already a windows partition.  But when I go thru the install procedure it doesn't show that existing partition.

"I suggest you expand the extended partition to use the unallocated space at the end of the disk (use all the disk) and install / and /swap to the unallocated space which will not be inside the partition. "
I tried to expand the extended partition by right clicking on the /dev/sda4 line but I don't get a chance to expand into the unallocated 436.46GiB space since Resize/Move is greyed out.

I do keep getting a popup dialog box "Libparted bug found- Can't have overlapping partitions"...Does this have anything to do with the problems I'm facing?

Regards

---

### Post by Bucky Ball on 2015-04-16
You need to right click the partition and unmount it prior to trying to resize.

Just a word. If you are resizing a Win OS partition, use Windows tools. If you are resizing a Ubuntu partitions (EXT*) use Ubuntu tools (gparted).

---

### Post by sumithar on 2015-04-21
Hi Sorry for the delayed reply.  If I rightclick it everything is grayed out except these two options.
[ATTACH=CONFIG]261455[/ATTACH]

FWIW, this is the error I referred to in the previous post- dont know if this is a factor in the problems I am facing
[ATTACH=CONFIG]261456[/ATTACH]

Thanks!

---

### Post by Bucky Ball on 2015-04-22
You are trying to unmount an extended partition. To unmount that, first you need to unmount all the logical drives inside it, which means unmounting sda5-sda11. Do that and then you should be able to unmount the extended partition just fine. To delete it, though, you need to delete all the logical partitions inside it, sda5-sda11.

Bottom line: You can't resize the extended partition (except to expand it if there is free space on one side or the other) while you have those logical partitions mounted inside it. You can't delete the extended partition while you have logical partitions inside it.

---

