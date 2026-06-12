---
title: "New Hard Drive Help"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by FeelsLikeANood on 2013-06-26
Hey

My old 2.5" hard drive is failing. Tomorrow I plan to buy an external hard drive and open up the case and replace the failing drive with the new one. I need to know if there is anything I need to do to prepaid the drive before installing Linux 12.04 and restoring from my backup.

---

### Post by varunendra on 2013-06-26
> **FeelsLikeANood said:**
> Hey

My old 2.5" hard drive is failing. Tomorrow I plan to **buy an external hard drive and open up the case and replace the failing drive with the new one**. I need to know if there is anything I need to do to prepaid the drive before installing Linux 12.04 and restoring from my backup.

Why would you do so?

You will be paying extra for the casing, and will be voiding the warranty immediately?

Why don't you just buy an internal 2.5" drive that will be cheaper and sustained warranty?

---

### Post by FeelsLikeANood on 2013-06-26
The only reason is that I don't know any local stores that sell internal drives and I can't wait another week for shipping. I use to laptop for work.
I didn't think of the warranty though. I'll drop by some local stores again and hope i get lucky and find an internal drive somewhere tomorrow. 

My question still stands though. Is there anything I need to do to prepare a new drive or can I just install Ubuntu?

---

### Post by FeelsLikeANood on 2013-06-26
The only reason is that I don't know any local stores that sell internal drives and I can't wait another week for shipping. I use to laptop for work.
I didn't think of the warranty though. I'll drop by some local stores again and hope i get lucky and find an internal drive somewhere tomorrow. 


My question still stands though. Is there anything I need to do to prepare a new drive or can I just install Ubuntu?

---

### Post by dino99 on 2013-06-26
all you need to do is to pay attention at the available format to plug it : sata3 / sata6 / ....  then format it to ext4 for example

---

### Post by TNFrank on 2013-06-26
Tiger Direct is currently having a sale on SSD's and they could probably get you one in 3 or 4 days depending on how far you are from their store. 
I agree, get an internal, don't mess with an external since, like was said, you'll void the warranty the instant you open the case. 
You could always back up to a USB stick(not sure how large your files are but you can get a 32GB USB for around $20 bucks nowdays) and keep your fingers crossed that your hard dive doesn't crap out before you get the replacement. Even if it does you'll still have the back up on USB to install after you get the need internal hard drive. 
Anyway, good luck on keeping things running until you can figure this out.

---

### Post by varunendra on 2013-06-26
> **FeelsLikeANood said:**
> My question still stands though. Is there anything I need to do to prepare a new drive or can I just install Ubuntu?

In case of an internal drive, it would most probably be unpartitioned, unformatted. Just let the Ubuntu installer do what it wants.

In case of an external drive, it would have a single partition formatted NTFS or FAT32 with some backup/sync tools on it (meant for windows only). In this case also, you can just let the Ubuntu installer do what it wants.

If you are planning to keep the drive Ubuntu only, keep the partition format EXT4 or something that suits you more and is internally supported by Linux (Like JFS, XFS, BTRFS etc.).

In any case, you don't really have to worry about preparing the drive in advance.

If you can wait for new drive, for sake of warranty if nothing else, you can make a persistent live USB to use Ubuntu or can install it on the USB drive like a normal installation, and run the OS from there until the new drive arrives. This will help you avoid using the failing drive unless absolutely necessary, thus avoiding any possible damage to the data on it. Of course if you have backed up all of it, you don't need to worry about that as either.

---

### Post by FeelsLikeANood on 2013-06-26
That's good to hear. And I found a small computer store nearby that has internal drives in stock with warranty thankfully. I'll buy one of the SSD most likely. ^_^ thanks for the help

---

