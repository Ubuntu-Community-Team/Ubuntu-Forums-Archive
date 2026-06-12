---
title: "I broke my file systems when I installed Win"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by fonggiding on 2007-11-21
After being clean for many years now, I decided to install Windows on my first partition(which I kept empty).

When I got the install menu after booting with the Win install CD I got to the partition screen.
Due to lack of sleep, I accidentally pressed "d" for delete partition, and for both my data partition and usb drive.
Now Windows didn't really delete it, I think it only marked it to be deleted. So now I can't recognize the partitions I messed up!

In gnome partitioner it shows the partitions as ready to have a fs written to it.
I know(probably) it didn't delete the data, did it change the headers(the data which shows the partiton's FS)?

I don't know what to do... Please help me...

---

### Post by rmemm on 2007-11-21
Yes your data is there as long as you've not booted an OS or installed additional software so your chances of recovery are quite good with enough work.

Your options:

[LIST]
[*]Hire someone to do it -- maybe costs $2500.
[*]If you have a backup -- just use this if its OK because repairing is complex.
[*]If you have a backup of your partician table elsewhere -- either as paper copy or an actule copy of the boot blocks, then restore is simple.
[*]Otherwise -- you basically have to search for the lost particians and rebuild the partician table.
[/LIST]

Another thing I would say -- you may want to image your entire drive to another drive before making any changes to it -- because it's easy to be in worse shape than you started when your doing low level disk work.

If you do have to rebuild the partician table, it's quite easy if you know the locations of the particians -- you can do so with fdisk.  But the real trick is to know the locations because any error means you'll fail, and maybe even furthur corrupt your disk.

Rob

---

### Post by meierfra on 2007-11-21
Give testdisk a try: [Hermanzone info on testdisk]("http://www.users.bigpond.net.au/hermanzone/p21.html")

---

### Post by fonggiding on 2008-01-23
:KS Thank you so much! testdisk worked very well! Well, not on my usb drive. Thanks for the posts. I think I actually found out abount testdisk(great program) through googling around.
Anyway I wanted to thank rmemm and meierfra for their posts and to got the good news out to other potential sufferers who are still feeling the symptoms of Micrsoftitus. There is a cure, there is a way... :KS

---

### Post by rosegarden78 on 2008-01-23
Testdisk?  I always thought formatting meant forever.  Who knew?  The Feds used a simple script that copies a dummy file onto itself, doubling it's size, over and over until the disk was full -- at which point the script deleted the dummy file.  Very easy with do loop for next if else and shell statements.

---

### Post by rmemm on 2008-02-02
Formatting and partitioning are two different things.

I think the orginal poster had just re-partitioned, which just changes the partition tables, not the content.  One good reason to always keep a copy of the partition table.

Formatting - it still would not actually erase all data.  Usually formatting just writes format information -- meaning it will overlay some things -- but it won't usually zero this disk first.  You can see this from formatting a large hard drive -- it takes hours to zero such a drive, but to just partition and format, you can do this quickly.

Also when zeroing a drive -- you still don't really erase it.  There's potentially some stuff left.  High security erasure requires overwritting multiple times with well selected erasure patterns -- 7 I think(?).

Rob

---

