---
title: "just tested the feisty livecd; some questions for config."
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by nanotube on 2007-05-14
hey all
first, just want to share some enthusiasm here. and ask some questions while we are at it. :)
i just tested the feisty livecd on my dell 5150 laptop. checked to see if all hw works, installed and confed beryl, and... everything worked like a charm! i didn't even have to change the default xorg.conf! just added the beryl repo to the sources.list, update, install the beryl and emerald packages, start beryl, and voila, there it is.
mind you, this is on an ati radeon 9000, and it just flew, without any problems! 
and i love the extra usability features (and eyecandy, of course) of beryl. 

so, next weekend, i'm thinking i will definitely install it to my hd (it is currently a dapper/winxp dual boot, plus a fat32 partition for shared data). 

i'm thinking i will start fresh, with the following changes:
* no more winxp partition - winxp can live in a vmware image.
* no more fat32 data partition - waste of perfectly good space. :)
* /home on a separate partition, so that fresh installs can go easier in the future, if needed.
* beryl, of course! :)

questions: 
* does anyone see any problems with this? are there things you can't do in vmware winxp that you can do in regular xp (ignore the 3d games issue, as i don't play any)? 
* i have a 40g hd, and 1.5g ram. so, 1-1.5g goes to a swap partition, then... how big should i make /home, and what to leave for / ?

thanks! ;)

---

### Post by hartz on 2007-05-14
You will get a million different opinions - here is mine:
/ - 10 GB (Includes all installed software, the OS, and /tmp)
swap - 2 GB (near the start of the disk)
/var - 5 GB (not far from swap as you access this file system all the time for logging, etc)

How to split the rest of the space between /home and anything else depends on your usage.  If you download lots of files and are happy to leave these in your home, put the entire rest of the disk into /home.  This is the strategy I tend to go for mostly these days.  This way I need only 4 partitions.  The fewer, the better as you have "wasted space" that you allocate/reserve to each file system just to prevent it from filling up to easily, too soon.

If you did want to have a separate fat32 file system for porting stuff between operating systems, then make that as small as possible, and still put as much as possible into /home.  An external USB disk works well enough for moving things between OS instances.

If you have another disk drive, even an old 40 GB drive, then rather put the swap partition on that disk and connect it via a separate disk controller.  You will feel the performance difference immediately if any paging/swapping occurs.  This way you also reduce the number of partitions on the disk.

If you want a special mount point for some data base or other special application, then create that first before you make /home and/or any FAT32 partitions.  You want it to physically reside directly after swap and /var on the disk.  A large database running all the time should actually have its own dedicated disk(s) if performance is of the ultimate importance, but we all cheat on this when it comes to performance/budget trade-offs.

---

### Post by nanotube on 2007-05-14
thanks for the tips :)

a question: any particular reason to keep /var a separate partition? 

good idea about sticking in a second disk - but as i said in my original post, this is a laptop, so if i stick in a second disk, i'll have to take out the first! :)

i'll also mention that it is a system for personal/work/school use, so it's not going to be a server or have any databases etc. running on it.

---

### Post by hartz on 2007-05-14
My bad, I read incompletely.

My habbit of putting /var on a separate file system stem from a very formal Unix production server background.

/var is where things tend to "grow" un-checked.  So having it in a separate file system prevents you from ending up with an unbootable file system.

For example, if root fills up and you need to reset the root password on login, then you are buggered, because you need free blocks in order to change the root password (the /etc/shadow file gets copied temporarily in the process)

Ubuntu and other apt-based distros leave much downloaded data/files in /var, particularly updates/install files.

You would probably be OK leaving it as a single file system merged with root - there are millions of opinions about the topic of how to best partition your file systems.

---

### Post by nanotube on 2007-05-14
hey, thanks for your reply. :)
about root filling up, one could always just boot from a livecd, mount the hd, and delete some files from like, /var/cache/apt, and be right back up and running, right? (though this is probably not what you'd want to do on a production server ...)
and while you are here, do you have any comments about windows in vmware? ;)

---

### Post by hartz on 2007-05-15
I have never run vmware.  Ever.

It is nr 109999407 on my to-do list 888AZ.5

You should search for other people's posts on vmware on this forum, try it out, and if necessary, start a new thread with any questions that you have :-)

---

### Post by nanotube on 2007-05-15
> **hartz3 said:**
> I have never run vmware.  Ever.

It is nr 109999407 on my to-do list 888AZ.5

You should search for other people's posts on vmware on this forum, try it out, and if necessary, start a new thread with any questions that you have :-)

hehe ok ;)

---

