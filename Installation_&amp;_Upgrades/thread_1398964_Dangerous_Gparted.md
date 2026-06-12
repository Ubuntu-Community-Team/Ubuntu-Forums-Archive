---
title: "Dangerous Gparted"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Oliv' on 2010-02-05
Hello, 

&#304; have different partitions for home, var, usr, tmp, swap, root and boot.

One day in a suicidal mood &#304; decided to get me more room for my home. So I used gparted to shrink, increase and move all those partit&#305;ons. All in one time. What should have happen happened...

 After some minutes of good work (half of the total workload was done) gparted told me that no, the var partition couldn't be moved. Do I want to save the details ? well yes why not. And it stopped its actions. I thought that even if something went wrong some kind of mechanism would allow my computer to recover or at least that the part that was done correctly would still be there.

&#304;ncorrect wish. Gparted was lost. I had this message '&#304;nvalid partition table on /dev/sda - wrong signature 0'. No partitions anymore. My heart sank in my feet.

&#304; started again my computer and could still boot. But only the boot,swap and root partitions were still accessible. The others had obviously their UU&#304;D wrong. 

The problem was my home partition with gigas of data that went to the heaven of datas....
&#304; have to confess that it's not the first time that &#304; use carelessly gparted and got havock on my computer. So &#304; didn't panic, went in the recovery shell and looked around. 
&#304; discovered 'parted'. &#304; suppose that parted is gparted without the g. But it has one option that saved my datas : rescue. &#304; used this option and could (miraculously it seemed at this time ) recover my home partition. And a correct partition table as a bonus side effect. (well, correct in the sens that at least parted/gparted didn't send me anymore error messages about the partition table, but only home, root , swap and boot were visible, tmp, usr and var were r.i.p)

After that &#304; could reinstall ubuntu with new partitions except for my beloved home partition that &#304; reused.

So &#304; have some question :
- why gparted crashed my partitions ??? &#304; really don't get it. Why would it work better if &#304; have done all the shrinking and moving steps one at a time ? &#304;f the user is doing something that's obviously too dangerous or out of reach of gparted maybe it shouldn't start ?
- why the 'rescue' option isn't in gparted ?
- why the rescue option (&#305;ts name be praised by the Lord of Careless  Computer Users) could find my home file system not the tmp, usr and var ones ?


Take care,

Oliv'

---

### Post by Herman on 2010-02-05
One idea is to use LVM if you really think it's important to divide everything up into a lot of small partitions, one for each directory. 
LVM will let you resize each partition much more easily, you should look up information about  LVM.
You can install Ubuntu in LVM if you choose the Ubuntu 'Alternate Installation CD and install with it. 

> - why gparted crashed my partitions ??? &#304; really don't get it. Why would it work better if &#304; have done all the shrinking and moving steps one at a time ? &#304;f the user is doing something that's obviously too dangerous or out of reach of gparted maybe it shouldn't start ?Were you running GParted from another operating system in a USB stick with the file systems you were working on umounted? Normally GParted can take a big list of commands, but the developers recommend to run one command at a time to be safer.
 You didn't try to resize the operating system you were running GParted in did you? I don't know if the developers would have been able to foresee somebody trying to do a thing like that.
> - why the 'rescue' option isn't in gparted ? I don't know and that is a good question.
You can use TestDisk, which is included in the GParted Live CD and the Parted Magic Live CD. TestDisk is installable in Ubuntu as well. TestDisk can scan your hard disk for lost or deleted partitions and offer you the chance to write them to a new partition table so you may have access to your files again. It could be complicated for you though because you made so many partitions.
> - why the rescue option (&#305;ts name be praised by the Lord of Careless Computer Users) could find my home file system not the tmp, usr and var ones ?I don't know.

Basically I think it's not a very good idea to divide up an installation into a lot of small partitions because unless you are using LVM you will always have some partition that will get full and need to be resized. Resizing Linux partitions is not so easy because the start points of Linux partitions are not easy to move. I would probably use the dd command instead of GParted if I had to move the start point of a Linux partition.
Or install with LVM.
Or even better, just install in one big partition. :)

---

### Post by Oliv' on 2010-02-05
&#304; like the LVM idea, thanks, &#304;'ll check it.

&#304; was using gparted from gparted live on an USB disk, and unmounted HDD.

O'

---

### Post by Herman on 2010-02-05
:) If you re-install and use LVM this time you should also look in 'Applications'-->'Ubuntu Software Center' for a program called 'Logical Volume Manager', which is a nice GUI for the lvm tools and other associated programs. You can easily resize your logical volumes with that. I think you'll like it. 
LVM is really cool, especially if you're into having lots of partitions.  :)

EDIT: Here's a link I was looking for to help you, [Hard Drive Encryption in My Ubuntu Installation]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html") - Martti Kuparinen

The title of this thread has the words 'Ubuntu Netbook Remix' in front of it, so I presume you're in a netbook.
Most netbooks don't have any CD-ROM drive and the last time I tried, the 'Alternate Installation' disc wasn't able to be installed by running the .iso files in a USB. 
You might need to install into a USB from an ordinary desktop computer and dd the installation into the netbook using a Ubuntu installation running in a second USB drive.

I have no idea why anyone would want to make a netbook installation divided into so many partitions though, but you are encouraged to have fun and do what you like. :)

---

