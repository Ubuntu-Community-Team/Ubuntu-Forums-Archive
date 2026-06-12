---
title: "Allocated old windows partition without formatting"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by apocalypse207 on 2009-12-09
Hi everyone. I recently attempted to remove my Windows partition entirely and allocate that free space to my Ubuntu partition.

I used Gparted and deleted the Windows partition. I did not format the new unallocated space before expanding my Ubuntu partition. I also expanded the filesystem to take up the entire single partition.

My current problem is that this was intended to add free space to my Ubuntu partition. Because I did not format the old Windows partition first, I *believe* that all of that information is still there taking up space on my hard drive. I currently only have 4.5GB free of a 200GB drive. The original Ubuntu partition was ~30GB with only 25 or 26GB used.

Is there a way to fix this problem without re-installing Ubuntu? I just want to get down to one partition for Ubuntu and remove all of the old data from Windows.

Thanks for the help.

---

### Post by darkod on 2009-12-09
According to your explanation you did correct. You should not format it because formatting means you would need to create a partition of that space in which case it wouldn't be available for existing partition to be expanded into it.
It's best to open Gparted from your ubuntu and see what it says. Post a screenshot here if you need advice.
One thing that might have happened is that if your root (and swap) are in extended partition, expanding the extended partition is only half of the job. The logical partition inside (root, swap, etc) will remain the same until you also expand the root partition itself.
Gparted image would show you this right away. Just open Gparted and take a look what your drive looks like right now.

---

### Post by apocalypse207 on 2009-12-09
According to Gparted, I have my Toshiba partition for system things, and a second extended partition which contains both swap and the filesystem. The problem is that the filesystem takes up almost all of my partition. The original ubuntu filesystem did not take up that much space. It's saying that I only have 5GB of free space remaining on the drive. I intended to get all 160GB of free space from my Windows partition and add that to my Ubuntu partition, but it seems that that data is still occupying 160GB of my disk space.

I can post a screen shot in a little over an hour.

Thanks for the help.

**I did expand the root filesystem after expanding the extended partition.

---

### Post by darkod on 2009-12-09
OK, waiting for the screenshot because I got a bit lost in the explanation. :) Probably too tired.

---

### Post by apocalypse207 on 2009-12-09
[IMG]http://i.imgur.com/fc1k3.png[/IMG]

Ok, so originally I had a Toshiba System volume which is still intact. I also had a Windows partition that was ~150GB and an Ubuntu partition (which includes the swap) that was ~30GB.

I deleted the 150GB Windows partition and then expanded the /dev/sda3 partition to occupy the new free space. As you can see, I also expanded the /dev/sda5 (filesystem) to occupy all of the new 185GB partition.

So I wanted to end up with Ubuntu on one partition, with the swap AND all the extra space obtained by getting rid of Windows.

From what I can see, all of the Windows data is still occupying space on the drive, but I don't have a way to get to it and get rid of it so I can use the space.

---

### Post by darkod on 2009-12-09
Honestly, I thought this is the way to do it myself. I understand what you're saying, you still have only 6GB free. It can't be the windows data because the filesystem is stated as ext3 but it really seems like it has kept the used % from before.

---

### Post by darkod on 2009-12-09
Our answer seems to be here:
[http://ubuntuforums.org/showthread.php?t=232925](http://ubuntuforums.org/showthread.php?t=232925)

---

### Post by apocalypse207 on 2009-12-09
Trying now, I'll get back to you on the results, thanks again for the help.

---

### Post by apocalypse207 on 2009-12-09
Haha! It worked! Thanks for the help, Darko.

---

### Post by darkod on 2009-12-09
No problem. Enjoy it now, you deserved it. :)

---

