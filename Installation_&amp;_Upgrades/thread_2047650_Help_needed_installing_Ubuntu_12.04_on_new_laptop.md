---
title: "Help needed installing Ubuntu 12.04 on new laptop"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by tomsax on 2012-08-25
I'm trying to install ubuntu 12.04 by creating a partition for it.

I get to the option where I choose "Something else" and then get the list of partitions.  I have:

dev/sda1 ntfs
dev/sda2 ntfs
dev/sda3 ntfs
dev/sda4 fat32

sda2 is the big one.

I tried to change the size of sda2 but before I could install the change it says I should create "swap space" which I don't know how to do.  So I abandoned that and tried to shutdown.

Then when I tried to start the laptop as usual with Windows 7 it told me that the system needed to be repaired and it took about 2hrs to do so.

Its a new laptop with loads of space and I would like Ubuntu and Windows 7 on the machine but it is proving very hard to acheive this.

Any help out there?

---

### Post by Bucky Ball on 2012-08-25
Hold everything!

You can only have four primary partitions on one physical drive else it gets tricky. Avoid.

Basically, you want something like three primary  partitions and one extended partition. Inside the extended partition you  can create as many logical drives/partitions as your hardware can  handle. Ubuntu will happily live in there (Win should be drive 1/primary partition 1 to keep it happy).

What is on the NTFS drives? I see no free space so where are you going to install Ubuntu? It uses EXT* partitions, not NTFS. Start with free space or delete the NTFS partitions to create free space after you choose 'Something Else'. 



If you have an existing big NTFS data partition, Ubuntu will be able to use that (you can set up some symlinks to it when Ubuntu installed.

Are you dual-booting with Windows?

---

### Post by Finnicella on 2012-08-25
Do you have an HP?
If it' so 
dev/sda1 ntfs  is the partition for windows boot
dev/sda2 ntfs  is the partition with windows 7
dev/sda3 ntfs  is the partition Recovery
dev/sda4 fat32 is the partition HP TOOLS
I've also an HP and I deleted sda4, resize windows with windows tool and whit the unallocated space I make an extended partition for Ubuntu.
If you have questions I'll try to answer.
Bye
Finny

---

### Post by tomsax on 2012-08-25
> **Bucky Ball said:**
> Hold everything!

You can only have four primary partitions on one physical drive else it gets tricky. Avoid.

Basically, you want something like three primary  partitions and one extended partition. Inside the extended partition you  can create as many logical drives/partitions as your hardware can  handle. Ubuntu will happily live in there (Win should be drive 1/primary partition 1 to keep it happy).

What is on the NTFS drives? I see no free space so where are you going to install Ubuntu? It uses EXT* partitions, not NTFS. Start with free space or delete the NTFS partitions to create free space after you choose 'Something Else'. 



If you have an existing big NTFS data partition, Ubuntu will be able to use that (you can set up some symlinks to it when Ubuntu installed.

Are you dual-booting with Windows?

There is no free space.

---

### Post by tomsax on 2012-08-25
> **Finnicella said:**
> Do you have an HP?
If it' so 
dev/sda1 ntfs  is the partition for windows boot
dev/sda2 ntfs  is the partition with windows 7
dev/sda3 ntfs  is the partition Recovery
dev/sda4 fat32 is the partition HP TOOLS
I've also an HP and I deleted sda4, resize windows with windows tool and whit the unallocated space I make an extended partition for Ubuntu.
If you have questions I'll try to answer.
Bye
Finny

Yes its a HP laptop.  I could try that though it seems a pity to lose the HP tools, especially as I think I've just used them to restore my computer.

---

### Post by arunes007 on 2012-08-25
> **tomsax said:**
> There is no free space.
Format the drive which is least usable to you through the linux live disk.
in ext2 mode coz ubuntu cant be installed on ntfs partitions.
Declare the root file as "/".
And if u have some space which is unpartitioned...make them swap space.
U can also continue without creating swap space...

---

### Post by Finnicella on 2012-08-25
To restore your computer you need the recovery partition.
Naturally, make a backup of the files inside the HP TOOLS partition and I suggest you to make the dvd of the recovery partition and a back up of all your important data too.
Bye
Finny

---

### Post by sandyd on 2012-08-25
HP Laptops have a tool to create restore discs.

Those things are equivilent to your recovery partition, and most people delete their recovery partition after creating them.

Just create a few sets of discs, delete the recovery partition, and you should be on your way.

---

### Post by Bucky Ball on 2012-08-25
+1 to what Finni and Sandyd have been saying, but crucial point that was  mentioned earlier but is worth repeating; once you've made the recovery  disks of the recovery partition and deleted it, [I]resize the existing partitions with the tools in Win.
  
[/I]Once you have plenty of free space you're good to go with creating the extended partition with it.

After that: Make a plan before you launch off, though, of how you are going to set up the Ubuntu partitions. Good luck. ;)

---

### Post by tomsax on 2012-08-26
I've backed up HP recovery on DVDs as suggested (as well as also creating a windows recovery disk and copying the drives contencts to an external hard drive.

I've deleted the HP tool drive from using the ubuntu DVD (windows didn't allow me to do it or warned me not to).

So, I have free space (over 100 GB) and only three partitions remaining.  

Still when I try to install "within windows" for a dual boot (first option) it fails.  I get some text and then it asked me to remove media and press enter, then it restarts in windows...

I am thinking of using something else but will this give me a dual boot on start up, the type I can choose windows or ubuntu when I start up?  Also concerned that the first option above doens't work implying a problem.

---

### Post by tomsax on 2012-08-26
BTW, thanks for all the previous input and help.  Much appreciated.

---

### Post by tomsax on 2012-08-26
Now realised I hadn't deleted as I hadn't clicked install (as in install delete?).  But if I do click install it says no root system is defined and asked me to correct this from the partitioning menu.

---

### Post by mansonfan78 on 2012-08-26
Reboot with the live cd in the drive.  Select "install ubuntu" then go to "something else".  You'll need to specify partitions manually and set up your unallocated space as three separate extended partitions:  15-20 gb as ext4 mounted as /, a partition equal to or larger than your physical ram mounted as swap, and the rest as ext4 mounted as /home.  Make sure you select the box next to "format" on the / and /home partitions.

---

### Post by tomsax on 2012-08-26
I've now deleted the HP tools drive in windows.  Now the 1st option of installation in windows seems to work and is chugging away as I write on this other laptop.

Should that work or might it all end in tears?

---

### Post by mansonfan78 on 2012-08-26
That should work then, although installing within Windows isn't the best option if you're planning on using Ubuntu long-term.  The procedure I mentioned earlier would be better and in case you're wondering, it would install the grub boot menu which allows you to dual boot with Windows (grub actually allows several operating systems on one computer, not just two).

---

### Post by linuxguy049 on 2012-08-26
Just for education sake: Is this booting into windows because the bootloader is stored somewhere other than C: ? So it goes to boot that drive, but nothing is there?

---

### Post by Bucky Ball on 2012-08-26
*Moved to** Installation & Upgrades.***

---

### Post by Mark Phelps on 2012-08-27
> **linuxguy049 said:**
> Just for education sake: Is this booting into windows because the bootloader is stored somewhere other than C: ? So it goes to boot that drive, but nothing is there?

Presuming that you installed Ubuntu from INSIDE Windows -- if your PC first boots into Windows, then it is behaving properly.

When you install from INSIDE Windows, it does not use GRUB, nor does it create a GRUB menu; instead, it modifies the Windows boot to add an entry for Ubuntu.

Instead of a partition, you get a file (root.disk) created INSIDE the NTFS partition and Ubuntu will run from there.

---

### Post by linuxguy049 on 2012-08-27
> **Mark Phelps said:**
> Presuming that you installed Ubuntu from INSIDE Windows -- if your PC first boots into Windows, then it is behaving properly.

When you install from INSIDE Windows, it does not use GRUB, nor does it create a GRUB menu; instead, it modifies the Windows boot to add an entry for Ubuntu.

Instead of a partition, you get a file (root.disk) created INSIDE the NTFS partition and Ubuntu will run from there.

Oh. I guess I misread.

I thought he had installed from a CD or something, onto C. I know that with HP lt's, windows is everywhere, and so I figured his bootloader for windows was still floatin around.

Thanks for clarification!

---

