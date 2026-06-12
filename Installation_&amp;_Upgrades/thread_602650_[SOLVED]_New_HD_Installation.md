---
title: "[SOLVED] New HD Installation"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by CanonKen on 2007-11-04
Hi,
Hope you can give me some good advise here.
I'm making the switch to Ubuntu, been using it for about 6 month dual booting on a PC with XP on, my hard drive is now on its last legs (everything is saved) just a matter of time.
I'm going to get a new HD and just install Ubuntu, got my eye on these 2 drives,in your opinion which is the best to go for
[One]("http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=483463") or [Two]("http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=258254")
Heard good reports about both of these, but should I look at something else ie Maxtors that I have always used and had no trouble with (says as he touches the wood table :) )
And whats the best way to partition it - just leave Ubuntu to it? no need to worry about backups or anything, i have an external drive for that and would like to keep using it.

Look forward to yourr reply's and suggestions

---

### Post by Pumalite on 2007-11-04
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
A good scheme is:
10 GB for'/'
2x RAM up to 1 GB for /swap
The rest for /home
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
(I'd go for the Western Digital)

---

### Post by CanonKen on 2007-11-04
Cheers pumalite,
As a relative newby am I right in saying install Ubuntu 1st then resize the partitions after??

---

### Post by Pumalite on 2007-11-04
Install Ubuntu last.

---

### Post by CanonKen on 2007-11-04
Cheers, never used Gparted before, I'll look into it - thanks

---

### Post by CanonKen on 2007-11-04
Forgot to mention you forgot the G at the end of partitionin but i found my way there :)

---

### Post by Pumalite on 2007-11-04
Thanks. I corrected it.

---

### Post by CanonKen on 2007-11-05
No problem,
been thinking about the new install today and having 400gb I think I might install Windows XP on a small partition just for chance I may need it, prob put it on 20gb or something like that.
How would this affect the partitioning we spoke about earlier?
Still run Gparted then install windows then Linux?
Or install windows then Gparted.
Have also heard about Windows and Linux sharing documents but I'll have a look through the forums and see whats involved
Might never come about as I'm looking more to using Linux full time

---

### Post by Pumalite on 2007-11-05
You first run Gparted Live CD; you make one large partition of your whole drive formatted ntfs. Install XP. Run Gparted again and resize the Widows partition.
Or, run Gparted and divide your hard drive in two partitions: one at the beginning of the drive formated ntfs. The other formated ext3. Install XP in the first partition of the first or only hard drive. Then install Ubuntu in the other partition.

---

### Post by CanonKen on 2007-11-05
Thanks Pumalite, your a star.
Was wondering which way to do it, seems I can do it both ways.
Picking the hard drive up tomorrw, will have time to do the install Thu I think unless work gets really busy.
I'll re-post and let you know how it goes, thanks for your help/advice.
Better burn that Gparted iso file while I remember

---

### Post by Pumalite on 2007-11-05
Good luck.

---

### Post by CanonKen on 2007-11-07
Right I have decided to go with this
1. 20 GB for XP
2. 10 GB for Ubuntu
3. 269 GB for /home
4. 1 GB for /swap
5. 100 GB Fat 32 for sharing

Are they in the right order?
And would they be
XP Primary
Ubuntu primary
/home Logical
/swap Logical
Fat 32 Logical

---

### Post by bulldog on 2007-11-07
One little thing :),if you plan on installing Gutsy you can skip the FAT32 partition.
Gutsy is perfectly enable to read and write to ntfs files system so sharing is not an issue.
You can install  a driver in XP which is capable to read ext3 file systems so......

When you come to install choose when the partitioner gives you the options MANUAL partitioning,you've allready done that part.
Mount the 10GB as /   [root] set the bootflag and format  ext3
Mount swap as swap and format as swap
Mount the last partition as /home and format ext3
Proceed with the install

---

### Post by CanonKen on 2007-11-07
So far so good, XP is on, just in the middle of installing Ubuntu as I type this

---

### Post by bulldog on 2007-11-07
Fingers crossed :)

---

### Post by Pumalite on 2007-11-07
Don't forget your toes.

---

### Post by CanonKen on 2007-11-07
Well everything went smoothly, everything seems to work OK, just got a slight graphics problem but I'll look into that tomorrow, when i boot to XP I have to adjust my monitor to the right to get it centred, when I boot to Ubuntu I have to move it the other way, i can't find an happy medium - YET :)

---

### Post by bulldog on 2007-11-07
Throw that monitor out the window and get a nice LCD monitor with a DVI connection and that problem is solved :)

Glad to hear the install was smooth

---

### Post by CanonKen on 2007-11-07
It is a nice LCD monitor :)
No DVI Though :(
Might be sorted now, changed the graphic driver and its central now in Ubuntu, I'll boot to XP sometime over the next month and see what happens there :lolflag:

Thanks for your help, both of you, much appreciated

---

