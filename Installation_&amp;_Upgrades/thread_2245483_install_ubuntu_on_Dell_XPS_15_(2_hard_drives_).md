---
title: "install ubuntu on Dell XPS 15 (2 hard drives )"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by moda2 on 2014-09-23
hi
i loved Ubuntu 14.04 so I'm switching as a primary system for my work ^_^

i have Dell XPS 15 Ultrabook (core i5 version)
this ultrabook comes with 2 hard drives , 32GB mSATA + 500GB and 8GB Ram , intel core i5, intel graphics

now my problem is in partitions how,
i have installed the ubuntu on the 32GB mSATA on / and 500GB for /home, and i created 8GB for swap on mSATA drive
and it's worked
but when i wanted to check the swap the system says there's no swap created,


please tell me what is the correct partition format should i do and after that please tell me how to encrypt the home folder and swap space

thanks very much

---

### Post by oldfred on 2014-09-24
If you encrypted your /home, your swap is also encrypted. And almost all partition tools cannot see encrypted partitions and do not show swap or show it correctly.

If you have 8GB of RAM, you probably do not need swap or could install 2 or 3GB of swap on hard drive just to have some. 

But if your / is 24GB with a separate /home then you should not have any size issues in / unless you accidentally copy something to the wrong place and it ends up defaulting into / (root). I forgot to mount /backup on my other drive and it copied the backup into /. Fortunately my / was large  (25GB) enough & backup small enough that I could recover & delete the new /backup folder.

The only thing I do differently is keep /home inside / (root), but still have all data folders and some of the hidden folders in /home that have lots of data on hard drive in a data partition on rotating drive. The slight advantage is user settings in /home then also are on faster SSD. But that is less the 500MB and once loaded would probably stay in RAM as cached data anyway.

Your configuration should be fine.

what does this show?

free -m

It should show a lot of RAM used, if you have run for a while as it does cache recent activity and only releases unused data when required for newer data. And swap (I think even with encrypted?) should show but be 0 use.

---

### Post by moda2 on 2014-09-24
thank you so much for replay

i have formatted the 2 hdd to install fresh install so please tell me what i should do

install the system on the 500GB instead of installation on 32GB mSATA ?

thanks

---

### Post by oldfred on 2014-09-24
Thought the way you originally installed was fine?

I have a 64GB SSD and created two / (root) partitions one is 12.04 and now the othe ris 14.04. I allowed for and efi and bios_grub partition. Current system only boots BIOS, but I was planning on moving SSD to a new UEFI system.
I then have multiple data partitions and several installs for testing in 25GB / partitions on my 640GB drive. Swap is on hard drive but never used.

---

### Post by moda2 on 2014-09-25
> **oldfred said:**
> Thought the way you originally installed was fine?

I have a 64GB SSD and created two / (root) partitions one is 12.04 and now the othe ris 14.04. I allowed for and efi and bios_grub partition. Current system only boots BIOS, but I was planning on moving SSD to a new UEFI system.
I then have multiple data partitions and several installs for testing in 25GB / partitions on my 640GB drive. Swap is on hard drive but never used.

Thanks for the replay

I've  set my bios boot option to [COLOR=Navy]UEFI [/COLOR]
and now I'm on the Installation screen "Installation type" ( partitions screen )

I've created these partitions:
- Swap 4 GB on mSata (32GB drive)
- 250MB EFI partition on mSata (32GB drive )
- the rest of space about 25GB to / on (32GB mSATA Drive)

- 500GB (the second drive) to /home

note: someone told me to give the /usr about 10GB , i'm just confused a little bit


please let me know if this is the right settings or needs some modifications ?

---

### Post by moda2 on 2014-09-25
please help me

---

### Post by oldfred on 2014-09-25
I am not one that likes to also separate additional system partitions. Standard Ubuntu install is just / (root) and swap and that probably still is ok, but it was good back when hard drives were a lot smaller when Ubuntu first started about 10 years ago.

I prefer either adding just a /home or keeping /home inside / (root) and having large data partition(s) for your data. If a newer user the /home is easy to set up & use. The data partitions require a bit more knowledge of partitions, mounting and stetting permissions and ownership.

Part of the reason for various suggestions on moving some partitions to hard drive was with older SSD where life may have been a concern. But newer SSD have lives comparable to hard drives (not really all that long with hard drive or SSD) but some tests show that many drives would last very long times.

So life should not be a major concern now, but backups are important as any drive can fail at any time. And power failures, if a laptop bumps and other hard use can shorten the life. And a lightning strike nearby can destroy a system. Probably the main reason for backups is us. We make mistakes and erase something we should not and then really need the backup.

       SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

---

### Post by moda2 on 2014-09-25
Thanks for replay,
the system will be installed on 32GB mSATA HD
now the question is if i kept the /usr and the / on the same disk , will i have a problem in the future if i installed more software
because the software are usually installed under /usr or /opt

so my plan is mount /usr and /opt on a separate hdd 
is that will be fine ?

---

### Post by oldfred on 2014-09-25
While having added partitions on the hard drive will work. But why? You want the parts of the system you use the most on the SSD.

My 14.04 install is using about 9GB and my 12.04 Precise install was up to 12GB even with some housecleaning after 2 years. That includes about 2GB in /home for my .wine and Picasa install. Everything else with lots of data gets moved into my data partitions.

```
fred@trusty-DT:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd4        28G  9.4G   17G  37% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.4M  394M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   96K  2.0G   1% /run/shm
none            100M   64K  100M   1% /run/user
/dev/sdc2       100G   43G   57G  44% /mnt/shared
/dev/sdc6        96G   47G   45G  52% /mnt/data
/dev/sdd3        28G   12G   15G  45% /media/fred/Precise


```

---

