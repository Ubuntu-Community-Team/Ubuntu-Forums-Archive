---
title: "Setting up partition and swap space."
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by iSylence on 2011-03-11
Hi all,

I'm still fairly new to using Ubuntu, I have been using it for a wee while now using the installer from within Windows, but I have recently decided to shrink off a part of my drive and dedicate it to Ubuntu.

My problem now is I am not sure about how to go about setting up the partitions. I shrunk off 40GB from my drive so I have plently of space, the problem is when I create a partition to install Ubuntu in it tells me I need a swap space which is fine. But then when I create a partition leaving a little left for the swap space (or vice versa making a swap partition first and leaving the rest for Ubuntu) the rest of the free space becomes "unusable".

What do I need to do here? Also how much swap space is recommended?

Cheers for any advice in this matter.

---

### Post by Hakunka-Matata on 2011-03-11
[COLOR="Red"]Swap size should be about 2 X RAM size.  Does the Thumbnail help?[/COLOR]  **Retracted - usually not true** - Brought to my attention by forum member 'Dutch70', thanks!

[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")
Excerpt:

How much swap do I need?

As a base minimum, it's highly recommended that the swap space should be equal to the amount of physical memory (RAM). Also, it's recommended that the swap space is twice the amount of physical memory (RAM) depending upon the amount of hard disk space available for the system (although this "recommendation" dates back from a time when physical RAM was very expensive and most Unix systems ran with many processes in swap space - a situation that hardly applies in most situations these days, but ancient Unix/Linux myths like this "recommendation" tend to survive well past their "use by" dates). In reality, if you use hibernation you need what was outlined the relevant paragraph above, otherwise you need as much swap space as your system will use - which may be actually be very little in a modern hardware setup. The only downside to having more swap space than you will actually use is the disk space you will be reserving for it.

---

### Post by CrooKxD on 2011-03-11
> **iSylence said:**
> Hi all,

I'm still fairly new to using Ubuntu, I have been using it for a wee while now using the installer from within Windows, but I have recently decided to shrink off a part of my drive and dedicate it to Ubuntu.

My problem now is I am not sure about how to go about setting up the partitions. I shrunk off 40GB from my drive so I have plently of space, the problem is when I create a partition to install Ubuntu in it tells me I need a swap space which is fine. But then when I create a partition leaving a little left for the swap space (or vice versa making a swap partition first and leaving the rest for Ubuntu) the rest of the free space becomes "unusable".

What do I need to do here? Also how much swap space is recommended?

Cheers for any advice in this matter.

I had the same problem the other night and what I did was I booted into Window and used the disk manager to turn all the unallocated space into a new volume without formatting it and that worked for me, the trick is not to format it, the install will do that for you

---

### Post by iSylence on 2011-03-11
> **CrooKxD said:**
> I had the same problem the other night and what I did was I booted into Window and used the disk manager to turn all the unallocated space into a new volume without formatting it and that worked for me, the trick is not to format it, the install will do that for you

Thanks, I do already have it unformatted though :S It's just set up as unallocated space at the moment but I can't create a partition without making the rest of it become unusable, when I still need to use the rest of it for a swap space. I have 3 existing partitions on top of this, could this be part of the problem?

---

### Post by Dutch70 on 2011-03-11
> **iSylence said:**
> Hi all,

I'm still fairly new to using Ubuntu, I have been using it for a wee while now using the installer from within Windows, but I have recently decided to shrink off a part of my drive and dedicate it to Ubuntu.

My problem now is I am not sure about how to go about setting up the partitions. I shrunk off 40GB from my drive so I have plently of space, the problem is when I create a partition to install Ubuntu in it tells me I need a swap space which is fine. But then when I create a partition leaving a little left for the swap space (or vice versa making a swap partition first and leaving the rest for Ubuntu) the rest of the free space becomes "unusable".

What do I need to do here? Also how much swap space is recommended?

Cheers for any advice in this matter.

Welcome to UF iSylence, 
 
 It sounds like your already using your maximum of 4 primary partitions and you'll have to make an extended partition. Then you can create more logical partitions inside the extended. So, for your next partition, use the entire unallocated space & make it an "extended" partition. Then shrink it & create your others.

Your Swap partition **does not** need to be 2x your physical RAM, unless you only have 256-512 MB of RAM. A good rule of thumb is Swap equal to your RAM.
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

Edit: If you've already shrunk your hdd from inside windows, do everything from gparted now.

---

### Post by CrooKxD on 2011-03-11
> **iSylence said:**
> Thanks, I do already have it unformatted though :S It's just set up as unallocated space at the moment but I can't create a partition without making the rest of it become unusable, when I still need to use the rest of it for a swap space. I have 3 existing partitions on top of this, could this be part of the problem?

I had the same exact problem the other night. I was setting up my HP laptop for a dual boot and at first I got the error too may primary partitions. Apparently the recover partition was a primary partition and I had 100GB unallocated and seemingly not gonna be worth a damn, thats when I stopped and booted back into Windows and took all the unallocated space in the GUI I right clicked and selected "New Volume" wanna say it asked if I wanted to format it and I said no. I rebooted back to the liveCD install and was able to create all my partitions as logical partitions after that...The install at that point went off without a hitch.

---

### Post by CrooKxD on 2011-03-11
> **Dutch70 said:**
> Welcome to UF iSylence, 
 
 It sounds like your already using your maximum of 4 primary partitions and you'll have to make an extended partition. Then you can create more logical partitions inside the extended. So, for your next partition, use the entire unallocated space & make it an "extended" partition. Then shrink it & create your others.

Your Swap partition does not need to be 2x your physical RAM, unless you only have 256-512 MB of RAM. 
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

Edit: If you've already shrunk your hdd from inside windows, do everything from gparted now.

I was wondering about the SWAP...I did 2GB based on something I saw in one forum and felt real dumb when I started seein people talking about double the RAM.

---

### Post by Dutch70 on 2011-03-11
> **CrooKxD said:**
> I had the same exact problem the other night. I was setting up my HP laptop for a dual boot and at first I got the error too may primary partitions. Apparently the recover partition was a primary partition and I had 100GB unallocated and seemingly not gonna be worth a damn, thats when I stopped and booted back into Windows and took all the unallocated space in the GUI I right clicked and selected "New Volume" wanna say it asked if I wanted to format it and I said no. I rebooted back to the liveCD install and was able to create all my partitions as logical partitions after that...The install at that point went off without a hitch.

Guess that's one way to do it, but all you had to do, was select "extended" for the entire partition from the little drop down box on the right of Gparted. Then continue creating your logical partitions.

---

### Post by CrooKxD on 2011-03-11
> **Dutch70 said:**
> Guess that's one way to do it, but all you had to do, was select "extended" for the entire partition from the little drop down box on the right. Then continue creating your logical partitions.

Good to know. I am probably gonna do a reinstall tonight. I mucked up and made my root 5GB which was 1GB more than recommended on another forum. Im at 89% used on my root and Ive had Ubuntu running for 2 days...Im afraid of how it will be in 2 more :s

---

### Post by iSylence on 2011-03-11
Okay new question, should I delete the OEM drive and the recovery drive from my disk?
I just recently picked up this laptop from Dell (and I'm actually a little disappointed with them, but that's another story) and of course it has this recovery stuff on it. I am in legal possession of multiple versions of OSs through the courses that I study at University so reinstalling Windows would be no problem for me, and I have access to all the important drivers from their site.

I'm no noob when it comes to setting up Windows and I'm keen to get rid of these two stupid partitions, but I'm keen for insight from you guys who might have some important points to share.

---

### Post by Dutch70 on 2011-03-11
> **iSylence said:**
> Okay new question, should I delete the OEM drive and the recovery drive from my disk?
I just recently picked up this laptop from Dell (and I'm actually a little disappointed with them, but that's another story) and of course it has this recovery stuff on it. I am in legal possession of multiple versions of OSs through the courses that I study at University so reinstalling Windows would be no problem for me, and I have access to all the important drivers from their site.

I'm no noob when it comes to setting up Windows and I'm keen to get rid of these two stupid partitions, but I'm keen for insight from you guys who might have some important points to share.

Other than needing the extra space they occupy, there is no other reason to.

---

### Post by CrooKxD on 2011-03-11
A clean install will 9 times out of 10 result in better performance in the long run. Now if you only have the recovery CDs u are more or less going to put the same bloat back on the disk then I would just resize the partition

---

### Post by Hakunka-Matata on 2011-03-11
> **Dutch70 said:**
> Welcome to UF iSylence, 
 
Your Swap partition **does not** need to be 2x your physical RAM, unless you only have 256-512 MB of RAM. A good rule of thumb is Swap equal to your RAM.
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")


Thanks for the SwapFAQ's link, good information.  I always figured I could afford 4 or 8 or 16GB of disk space, especially these days, but I see your point also.  There is one caveat to small swap partitions however, in the same SwapFAQ's link:  Quote "Hibernation (suspend-to-disk) The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system. "

---

### Post by Dutch70 on 2011-03-11
> **Hakunka-Matata said:**
> Thanks for the SwapFAQ's link, good information.  I always figured I could afford 4 or 8 or 16GB of disk space, especially these days, but I see your point also.  There is one caveat to small swap partitions however, in the same SwapFAQ's link:  Quote "Hibernation (suspend-to-disk) The hibernation feature (suspend-to-disk) writes out the contents of RAM to the swap partition before turning off the machine. Therefore, your swap partition should be at least as big as your RAM size. The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system. "

Which is why I said "Swap, equal to your RAM" If you want to hibernate. A little extra is not a bad thing, but 2X your RAM is overkill & wasted space unless you have very little RAM.

---

### Post by Hakunka-Matata on 2011-03-11
> **Dutch70 said:**
> Which is why I said "Swap, equal to your RAM" If you want to hibernate. A little extra is not a bad thing, but 2X your RAM is overkill & wasted space unless you have very little RAM.

@ Dutch70 - I stand corrected, you are right.  OK, now, let the learning continue.......  
Thanks :-)

---

