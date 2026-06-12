---
title: "Manual partitions for Ubuntu Server 18.04 for best performance"
date: 2019-11-25
forum: Installation &amp; Upgrades
---

### Post by flaviustech on 2019-11-25
Hey there,

I managed to get a "newer" server machine, the old one running ubuntu server 16.04 since 2016.

Now, i want to upgrade also to ubuntu 18.04 to new machine. However, the machine will run with 2 ssd's. 

It will be an [COLOR=#008000][SIZE=3]**LAMP**[/SIZE][/COLOR] Server with [SIZE=2]**[COLOR=#008000]Webmin/Virtualmin[/COLOR]**[/SIZE] platform.

May i ask you, how should i use manual partition for the best performance?

When i install for first time server, should i make a new partition on separate ssd for keeping [SIZE=3][COLOR=#ff0000]**/etc**[/COLOR][/SIZE] and [SIZE=3]**[COLOR=#ff0000]/tmp[/COLOR]**[/SIZE] routes?

The point is to have mysql queries served from **second ssd**, is that a good practice to have best performances? 

Also, another question is regarding swap partition! Should i make **[COLOR=#ff0000][SIZE=3]swap[/SIZE][/COLOR]** memory from second/slave ssd?

Can you lead me to the best way to use partitions to have a faster server?

Thank you!

---

### Post by TheFu on 2019-11-26
SSD storage management is all virtual, so there's no need to think they work like spinning disks. They do not. Wear levelling is hidden - actually, all the real storage management is hidden from the OS.

Enterprise SSDs?  Consumer? NVMe or just SATA?

If quality Enterprise SSDs, then RAID0 for best performance. I wouldn't risk it with consumer SSDs.
Leave 20% unallocated on both SSDs to drastically increase durability.

For a server, I'd add enough RAM so that swap is never used.

As for partitioning, it doesn't matter for performance, just for storage management and backups.  Some people will micromanage storage for /etc, /usr, /root, /var, /opt .... I only micromanage storage when it is really odd.  I might have a special mount for /var/lib/libvirt or /var/www if those areas will get huge.

 There are lots of posts here showing the different layouts.  Most of the professionals will be using LVM for storage management, but not always. What works best is a professional decision and driven by the specific requirements.

Clear as mud?

---

### Post by flaviustech on 2019-11-26
Thanks, 

I am moving from an intel s3000ah socket 775 with intel e4500 dual core and 2.2gb ram.

I am jumping to 1150 socket with g4400 procesor. Most of my components are non-server professional related components. No ECC ram, but at least are 4gb ddr4 this time.
The SSD are normal SATA3 SSD's.

The webserver will hold only 5-6 websites with low traffic, but i want to have a fast response queries for that traffic. Also i will install Minidlna server for sharing photo/videos and storage.

Yeah, i know, i should go for redundancy, but the components are too expansive! I mean, i wish i get a new motherboard supermicro and 16gb ecc rams with quad xeon. But, in the end, for such a low requirements from my low traffic websites, i think i am ok!
I just want to serve a fast loading websites. I have a pretty good ISP static ip, with 150-250Mb/sec Upload and  300Mb/sec Download.

The reason i asked about partitions is because it will have different response time, solving each ssd with it's own controller the files. I know there are faster the HDD, and not mechanical parts. But still they, 2 controllers are better then 1 from 1 ssd.

I donno how much it will improve if i put mysql server on the second ssd.

Btw, no RAID SSD! One is 60GB and one is 120GB, i will keep redundancy from old server, i keep backup files on it and working as second server with dns. Plus, i have the 3'rd server from my own PC, which is much more faster, i have 2 OS's (Windows + Ubuntu), in case something goes bad, i can restore pretty quick my websites.

So, i kept 20% as you said from each ssd, i installed ubuntu on the 120gb ssd, and the second ssd i installed /tmp partition, i will keep cron backup in that ssd, also i save files on my personal computer + laptop.

Hopefully i get an Supermicro motherboard, i saw some offers for $200 or i go for second hand one :). I need one with 1cpu.

---

### Post by SeijiSensei on 2019-11-26
I haven't run a physical server for web and mail services in a decade. Now I just use virtual machines at [Linode](https://www.linode.com/). No more worries about stable power or Internet connectivity or whether some disk is going to die far away in a hosting facility.

---

### Post by TheFu on 2019-11-26
> **SeijiSensei said:**
> I haven't run a physical server for web and mail services in a decade. Now I just use virtual machines at [Linode](https://www.linode.com/). No more worries about stable power or Internet connectivity or whether some disk is going to die far away in a hosting facility.

For 1 or 2 domains, this is the most cost effective and best performing solution - using a VPS.
If you will have 20+ domains for different clients that need to be separate, then the costs become prohibitive.  Many tiny websites can be run from a $30 raspberry pi, just fine.

With consumer SATA SSDs, don't use RAID0. RAID0 isn't redundant and for low volume websites, splitting things up really isn't going to matter regardless.  It isn't worth doing anything too special outside storage management considerations, IMHO.

I wouldn't bother keeping any backups on the disks connected to the machine. 

I wouldn't use mysql. I'd use mariaDB, if you can't use Postgresql instead. MariaDB is for political reasons. Postgres is for data reliability reasons. Pick your poison.

---

