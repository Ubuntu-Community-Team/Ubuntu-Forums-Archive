---
title: "Dual boot on 80 gig drive"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2011-05-18
I have my computer set up with 2 40 GB drives (IDE) and 1 500 GB(SATA). One 40 GB drive for Windows XP, 1 40 for Ubuntu and the 500 GB for storage for both (formatted NTFS).

I am building a computer for my wife and want to use 1 80 GB IDE drive instead of 2 40s and a 320 GB IDE for storage (the storage drive is irrelevant to my issue). These are all parts I have laying around. I installed XP and partitioned the 80 gig into 2 40 gig partitions during the installation.

When I go to install ubuntu, it shows me all the partitions of both drives but gives me no option (other than manual) for using the 2nd half of the 80 gig for installation. 

I need to know how to set it up manually. It gives me a slider to divide the 2nd half of the 80 GB drive into 2, but I don't know what size to make them. Also when I look at my 40 GB drive from my computer it show 3 divisions: "39 GB ext4", "ext 1.7 GB" and "1.7 GB swap space".

Thanks,
Brad

---

### Post by aphatak on 2011-05-18
What you are looking at is perfectly normal.  Linux prefers swap space on a partition all by itself, and your installation has placed the swap volume in a logical partition as opposed to a primary partition.  The 'ext 1.7 GB' refers to an extended partition, which is a kind of primary partition that contains logical partitions.  If your swap space is approximately twice the size of your physical RAM, you should be fine.

Incidentally, if you have a separate data drive, 40GB (or even 39GB) is a lot more space than Linux would need.  I normally allocate 16GB for Linux, and 4GB for swap.  I have never had Linux run out of disk space in this set up (all my data is on a file-server).  What I would do in your place is allow 20GB for Linux (16GB for the root and other stuff, and 4GB of swap space), and give the remaining area all to Windows.  XP can (and probably will) use the extra space.  You will have to partition the disk manually if you want to do it.

The set up as you have described it will run Linux comfortably, though.  So if you want, you can bash on regardless!

---

### Post by brad1138 on 2011-05-18
> **aphatak said:**
> What you are looking at is perfectly normal.  Linux prefers swap space on a partition all by itself, and your installation has placed the swap volume in a logical partition as opposed to a primary partition.  The 'ext 1.7 GB' refers to an extended partition, which is a kind of primary partition that contains logical partitions.  If your swap space is approximately twice the size of your physical RAM, you should be fine.

Incidentally, if you have a separate data drive, 40GB (or even 39GB) is a lot more space than Linux would need.  I normally allocate 16GB for Linux, and 4GB for swap.  I have never had Linux run out of disk space in this set up (all my data is on a file-server).  What I would do in your place is allow 20GB for Linux (16GB for the root and other stuff, and 4GB of swap space), and give the remaining area all to Windows.  XP can (and probably will) use the extra space.  You will have to partition the disk manually if you want to do it.

The set up as you have described it will run Linux comfortably, though.  So if you want, you can bash on regardless!

Thanks, I am not worried about my computer it has run fine for a long time. Although I have 2 GB memory, from what you said my swap should be 4 GB?  I actually I did give a little more space to the XP partition, about 43/37 or so. The comp I am building will have 1 GB memory, so I will make the swap 2-3 GB. With the extra storage drive, I am not worried about running out of room on the XP partition.

---

### Post by Dutch70 on 2011-05-18
I agree with aphatak on the space you need for "/" aka "root". 15-20GB is what I always recommend & I go with 20GB myself. If Ubuntu uses more than 75% of the system, it will begin to slow down. However I've never actually used more than 8-10 of my 20GB. 

Having extra swap space won't hurt anything, but your swap partition only needs to be equal to your physical RAM, plus about 10% for overflow if you like, and you really only need that if you want to hibernate. 
With 2GB of RAM, I'd go with 2.25GB of swap & that **is** a little extra.

Double your RAM is an old rule & it's for people that have 512MB of RAM or less. Now days, 1GB of RAM is the recommended minimum for Ubuntu, so the double your RAM rule is not really necessary anymore, except for people that run it on 512MB & some do and say it runs fine.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

---

### Post by brad1138 on 2011-05-18
> **Dutch70 said:**
> I agree with aphatak on the space you need for "/" aka "root". 15-20GB is what I always recommend & I go with 20GB myself. If Ubuntu uses more than 75% of the system, it will begin to slow down. However I've never actually used more than 8-10 of my 20GB. 

Having extra swap space won't hurt anything, but your swap partition only needs to be equal to your physical RAM, plus about 10% for overflow if you like, and you really only need that if you want to hibernate. 
With 2GB of RAM, I'd go with 2.25GB of swap & that **is** a little extra.

Double your RAM is an old rule & it's for people that have 512MB of RAM or less. Now days, 1GB of RAM is the recommended minimum for Ubuntu, so the double your RAM rule is not really necessary anymore, except for people that run it on 512MB & some do and say it runs fine.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

OK, So I will have about 35 GB for Ubuntu and 2 for the swap, that should be fine right? You may only need 20, but more can't hurt anything can it?

BTW I did a clean install of 11.04 on my comp in April and it say 23 GB free now, less than 1 month later, so that is about 15 GB used and I haven't really installed that much.

---

### Post by Dutch70 on 2011-05-18
Hahaa, no it certainly won't hurt anything, but it's probably a bigger waste of space there than it is if you use it for swap. In such a case, I'd go ahead & make the swap a little bigger even though it doesn't need to be. You may add RAM one day.

Edit: nevermind this, I forgot about your 500GB hdd.
You can also create another partition and format it to NTFS. Then you'll be able to share files on that partition with windows, or if you format to ext3 you can install fs-driver into windows and it will be able to read ext3 file systems. Not sure if either of those are useful with your situation.

If you're using 15GB and haven't installed much, you may want to install bleachbit and clean your system.
```
sudo apt-get install bleachbit
```
You can also install it from Software Center.

Or run these commands to clean your system.
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
```
sudo apt-get clean
```

I run those 3 commands & then use bleachbit (not running as root) for everything else.

---

