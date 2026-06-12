---
title: "Need help with &quot;FakeRaid&quot;"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by RetiredInMaine on 2007-11-29
I want to use raid on my new PC. I had read  that a new install would detect the drives and ask if I wanted to install a raid array so I installed Ubuntu 7.10.  The install detected both drives but only installed on one of them   A thread in this forum said I needed to use the alternate  cd if I wanted raid, so I downloaded and burned it. But when I went to install it did not ask if I wanted to use raid.

Question, how do I install raid on 7.10? I have read the directions on the fake raid how to but I think some information is missing, or else I just do not understand what it's telling me. The dialog asked which drive to partition and I aborted at that point. Should I have continued?

Additional question, if I switch to a 64 bit install will that cause me any problems with raid?

Thanks  to anyone who answers.

---

### Post by foolsh on 2007-11-29
yes you have to use the alternate cd to do this. It's a little tricky the first time so give me a few **more/hours** minutes and I'll post a little how to.

be right back

---

### Post by foolsh on 2007-11-29
Not sure about the 64bit question I only have 32bit systems
keeping in mind partitioning your hard drive is not something users do everyday and assuming you want to wipe everything and get that six hard drive +terabyte of storage running just Linux in a supper fast Raid 0 array

do the usual:
```
boot alternate cd
choose install in text mode
choose language and keyboard etc...
configure network 
enter your host name blah blah blah

```

On the Partition Disks Screen choose _manual_

Delete any partitions you see until you see FREE SPACE under each disk
Or
If your disks are UN-configured highlight each and press enter, answer yes to the prompt for each disk

-Deleting a Partition:
highlight it and press enter and choose to delete to partition  


-Boot partition //anyone have a way of booting directly from a /dev/md?//

 This was my difficult  mistake when I first stated using a raid my system just wouldn't "boot"

make a partition about 500 MB `maybe even 1 GB` at the beginning of the first drive for the /boot partition
You'll need to leave room here for all those kernel images that will be installed eventually during updates or, if you compile your own.

```
select FREE SPACE on the first drive press enter
Select Create A new partition
enter/replace the default size with 500 MB or, whatever you would feel is best, hit return
select Primary
select Beginning
change Mount point: to /boot
set the Bootable flag: to on
select Done setting up the partition

```
I would keep "Use as: Ext3" even though XFS is faster I had some problems with files not executing after a fresh install of gusty two days ago. Nothing would run for me, X would start but that was it. I couldn't run any executables. Weird XFS worked on feisty. And grub seems not to like being installed to XFS. Lilo wants to install when the ubuntu install is "Finishing up"
 

Create a swap partition

determine size of swap partition
say maybe 1GB swap
for raid 0 divide the size by the number of drives - see below
say we have 3 drives
```
 1 GB / 3 = 333 MB
```
Create partitions on each drive that size
```
Choose the FREE SPACE
Select Create A new partition
replace the default size with the desired size i.e. "333 MB" hit return
select Primary
select Beginning
Change Use as: to physical volume for raid
select Done setting up the partition
repeat for each drive creating only one new partition in each
After all the disks have 1 raid volume partition 
select Configure software RAID at the top
select yes to write changes
then select Create MD device
choose your raid style
select each /dev/* by hitting the space bar. Then press enter
select Finish

```
Raid 0 = big fast non-fault tolerant drive good for desktops gaming and swap usage
Raid 1 = fault tolerant drive. If you make this or raid 5 your swap type, then increase the size to your maximum wants from step 1. Because it does not treat the raid array as one big disk it treats them as many backups of the same info
Raid 5 = more fault tolerant than raid 1 and with more features but I forgot them
I use raid 0 it is fast! but have backups of all my stuff on my firewall/router/fileserver box

Making the root partition

same as above except the size of the partition can only be as large as the smallest amount of free space on the smallest drive
yes this wastes some space if all your disks are exactly the same from creating the /boot partition.
 I wish there was a way to boot from /dev/md0/boot.

so look at the FREE SPACE of each drive
Find the smallest one then create partitions in each drive that big
say one drive has 78 GB free and the other two have 81 GB. 
78 GB is as big as you should make the partition size

Create root partition /
basically same as above
```

select FREE SPACE in the menu 
Create Partition
Enter size
Choose Primary
select Beginning
Change Use as:  to physical volume for raid.
then select Done setting up the partition &#8220; 
repeat for all drives
after all drives have partitions choose Configure software RAID from the top
*same as before *
select yes to write changes
then select Create MD device
choose your raid style
select each /dev/* with the space bar and hit enter
select Finish

```

almost there two more things to do 
```

select the RAID device that is for your swap if you followed the steps above it should be RAID0 device #0
change Use as: to swap
select done setting up the partition
now select the big RAID device and hit return ie RAID0 device #1
change Use as: to ext3
change mount point to / - the root file system
choose Done setting up the partition

```
finally choose Finish partitioning and write changes to disk
if you get a red screen error just go back and change/add what the installer was complaining about

---

### Post by foolsh on 2007-11-29
there I'm finish ,I think , I messed with arrays all night long and some of the next day trying to figure them out
I really hope this helps
having programs open almost instantly is a real big plus when I'm switching from one app to the another
If you setup a raid 0 array with more than 3 drives you will notice a BIG difference in performance
cheers m8

---

