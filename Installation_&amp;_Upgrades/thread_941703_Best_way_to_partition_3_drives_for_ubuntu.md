---
title: "Best way to partition 3 drives for ubuntu"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Oziyak on 2008-10-08
I'm looking for some opinion and knowledge on how I should setup my drives for ubuntu.

I have 2 160 Gb SATA drives and 1 30 GB IDE drive installed on my system.

Processor is AMD64 3000+ so I was going to go with the 64-bit version.

Motherboard is DFI NF4 Ultra and has 3 GB of Dual channel ram installed

Video card is a 1GB Nvidia Geforce 8600 GT with HDMI, DVI, and VGA outputs.

I was also going to use 8.10 beta :)

thanks for any info you can provide.... I"m not very familiar with setting up partitions for a linux install but want a fast and stable machine and dont' mind setting them up manually in the ubuntu install cd settings.

thanks again

---

### Post by timcredible on 2008-10-08
i would go with:

swap - 1gb of the 30gb drive
/ - the rest of the 30gb drive
/home - one of the 160gb drives
/data - the other 160gb drive

all of them ext3

---

### Post by Idefix82 on 2008-10-08
It depends on how you are going to use the system. In any case I would recommend a separate /boot partition of about 200 MB and a separate /var partition of 2 GB or more (at most 5 I would say) and a separate /home partition. Its size depends on how you want to use it. If you are only going to store text documents and not install any icon themes etc then a couple of GB will suffice. If on the other hand you want to store music, pictures, videos etc on it then you could easily use one of your two large hard drives as the /home partition.
[Here are a couple of thoughts]("http://ubuntuforums.org/showthread.php?t=928600&page=2") of mine on why to create a separate /var and possibly a separate /tmp partition. Have a look at my second post on that page.
I have also a separate /usr partition. That should be fairly large since all the installed programs will go there.
And of course you need a SWAP partition. One recommendation is to make it about the size of your RAM because the RAM is written to SWAP when you hibernate.

---

### Post by Oziyak on 2008-10-08
thanks very much for the response :)

I'm really a little more dense then I might let on though... can you explain to me what the / is for the rest of the 30 gb drive? is that the system files? making the 30gb the boot drive? also not sure what home and data are.... well... I know what home is...

so I should setup one swap and 3 ext3 partitions?

---

### Post by Idefix82 on 2008-10-08
Everything that is not on a dedicated partition will go into the main partition which is mounted as /. With the setup timcredible is suggesting for example all the programs that you install will go there. Personally, I think that 30 GB for software and 320 GB for data is slightly skewed for many users, unless you are only going to use the browser but have huge databases of music and videos which you want to store on your computer (rather than an external HD). But as I said, you are best in the position to decide what you need.

---

### Post by Oziyak on 2008-10-08
thanks man.... that was exactly what I wanted to hear.... I like the explaination on fragmentation and what not...

Now I"m not sure what to do though with the 30 gb drive? and if it can be used to make things better yet.
If I setup a boot, usr, var, home, data, and swap all off one drive then that leaves me the other drives as backups etc...

also... is there an order that those folders should be organized on the disk as far as location? or will linux take care of that for me?

---

### Post by WWSmith36 on 2008-10-08
There really is no ¨best¨ way for partitioning.  It all depends on what you will be using the system for and what your personal preferences are.  That being said, I´ll give you some general suggestions.

Swap file typically 1.5 x ramsize

Install linux on a single partition.  I do not find it necessary to have separate partitions for individual linux folders like (/boot /home /etc /var).  

Definitely create a large data partition for music, video, pictures, etc.  If you planning to dual boot windows I would make this a ntfs partition so that windows could access these files as well.  In linux you can just create links in your /home folder to music, video, pictures, etc.  This will keep the size of you home folder smaller.

I would also create a backup partition on a separate drive and sync it with you data partition.  That way if that drive dies, you will have a backup of your critical data files, music, etc.

I would also suggest a separate drive partition for backups images of the your OS´s.  This comes in hardy if you ever want to restore a corrupted OS.

---

### Post by Oziyak on 2008-10-08
thanks for that information as well.
I'm relatively new to linux (ubuntu) and am not aware of the syncing programs and/or image backup programs that come with it (or can be downloaded).  Could you name them for me?  Also... is this image backup similar to microsofts "system restore"?

---

### Post by jerome1232 on 2008-10-08
You can also use LVM to create a volume group that spreads over more than one drive, You can then create multiple volumes inside the volume group. The draw back to this is obviously if a partition is spread out over 2 drives you have 2 points of failure and etc...

So you could have a single volume that spreads out over all three drives.

---

### Post by Idefix82 on 2008-10-08
There is another very good reason for at least having a separate /home partition: when you upgrade to the next version of Ubuntu and you decide to do it with a clean install of the next version, you can still keep all your settings by just reusing the /home partition.

As for the placement: Ideally, the /boot partition should be the first partition on the HD. Other than that, I am not aware of any restrictions.

It's up to you to decide whether you want to back up everything regularly. If you do then leaving one of the big HDs for backup will of course make everything much safer. On the other hand, you will have much less space.

What I would do in this case is to put /home and /usr on the one large hard drive, everything else, like /boot, /var and SWAP on the 30GB hard drive and leave the second large hard drive for backup. Personally, I don't have a separate data partition and store my docs, music, pictures, ... on the /home partition, but that's up to you.

---

### Post by WWSmith36 on 2008-10-09
For a sync application, there is a grsync which is a GTK+ graphical frontend for rsync.  Here is there website
[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)
It is in the universe repository.

For drive imaging, the is partimage which is also in the universe repository.
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

For restoring a partition, especially your Ubuntu partition, you should use a System Rescue CD.  This is a nice utility CD.  You must download and burn the ISO from the website.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

A good resource for linux software is
[http://linuxappfinder.com/](http://linuxappfinder.com/)

Hope this Helps

---

