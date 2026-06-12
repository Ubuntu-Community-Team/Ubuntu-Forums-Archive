---
title: "Getting Ubuntu to use only the free unpartitoned space"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by Oxwivi on 2010-12-07
When I install Ubuntu, after doing Windows, it always seems to hog some space away from Windows. How can I get Ubuntu to use only the unpartitioned space I left? I don't know how to use the advanced partitioning tool. Any pointers?

---

### Post by Swagman on 2010-12-07
Sounds like your installing via Wubi ?

---

### Post by Frogs Hair on 2010-12-07
For traditional dual boot use the disk utility in Windows prior to installing ubuntu shrink the free space to create to the desired partition size . When you get to the partition portion of the Ubuntu install use the manual  settings and locate and format the space you have set aside . There are a number of tutorials on You Tube  some better than others.

---

### Post by oldfred on 2010-12-07
If you have an available primary partition to convert to the extended partition you can install Ubuntu by creating the partitions yourself. You then have total control over the sizes. You specify size, mount point (/ (root) & /home), and format.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.

More info on partitioning:
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Oxwivi on 2010-12-07
Okay, to answer all your responses, I'm using the standard installer form the Ubuntu CD. And I already installed Windows to the the size I want it to be and left space for Ubuntu, unpartitioned. Yet, still it takes some space from the Windows's partition for reasons I can't figure out. CHKDISK is automatically run at the next boot of Windows.

And finally, I am having the folders in my /home/user/ partition bound by fstab to yet another partition, so I'd skip making a separate partition for it. And do I really need swap at all? All I do is browse and chat and occasionally chat and listen to music. Gaming will be left to Windows, if any.

How do I set the root directory in the advanced partitioning tool at Ubuntu installation from the CD? Any pointers?

---

### Post by oldfred on 2010-12-07
More links if you need them, then:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

They show examples with different versions of the installer. Choose the one more like what you want to do and just follow it.

---

### Post by Oxwivi on 2010-12-08
I got what I was looking for in a link in one of your links, thanks.

---

