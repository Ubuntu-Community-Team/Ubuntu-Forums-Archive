---
title: "Need more room on /"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2011-08-08
I need more room on my / partition. For some unknown reason, I only made it about 7.5 GB when I first installed 9.04. I need to upgrade to 10.04 (at least) and it states I need more room on /.

I have plenty of room available on my /home and swap partition (they are under the same extended partition). Attached is a pic of Gparted.
Is there a way to grab space from the sbd2 partition and give it to sbd1? I tried earlier, but couldn't figure out a way to do it.

---

### Post by Basher101 on 2011-08-08
There is no pic o.O also it is possible. Depending on how big your partitions are this could take hours though, because you have to "move" the partition (depending on your partition setup). Do you have experience with partitioning?

---

### Post by lsutiger on 2011-08-08
Hey Basher101! Thank you for the quick reply. Yeah I notice right after I clicked submit :-/

I have limited experience with partitioning, as in I do not do it on a daily basis, but understand how to set the partitions. I am just not sure about the question at hand.

This machine is in a business environment and it is critical that it is up and running. We haven't really implemented cloud computing yet :)

I do have daily backups on the server, so if everything gets wasted, I can get it back up and running, but I really do want to go through that again!!

---

### Post by Basher101 on 2011-08-08
please post a screenshot of Gparted and how your partitions are set up. Then i could suggest the best method how to proceed (im a SO new to ubuntu, i repartitioned my laptop like 12 times, so i got the experience in 1 day :lolflag:) I set up my partitions like this: i got total 640gb hdd (597,sth in binary calculation) i gave windows 7 26gb, then made an extended partition containing: 15gb for ubuntu, 4gb swap, and the the rest as a giant shared partiton for all the files (docs, movies, downloads, games, music ect.) and i only got my OS and basic programs on the OS partitions.

edit: did you add the file later on? i think there was no screen when i first read it

---

### Post by lsutiger on 2011-08-08
Done (on first post)! How do you like 11.04? I loaded it on a test laptop....I am not feeling the love for it. The GUI just seems a bit 'dumbed down'...Just my opinion!

---

### Post by Basher101 on 2011-08-08
I love it, i cant complain about it. I love gnome 3 even more (from what i see on youtube), but my onboard graphics cant handle it....so back to helping you, i see you have many files on your big ext4 partition..thats the problem. You will have to either shrink the extended partition and move it (that will take hours for sure looking at how big it is) or completeley repartition it, making a fresh install and copying back all the files. Doing the reinstallation will work alot faster, trust me. I moved a partition around 200 gigs big in my "learning" phase, it said it needed more then 3 hours to complete. Done the repartitioning and reinstall in 30 minutes.

edit: a note about 11.04, you can always use the old interface. Unity is not the only one you can select, gnome 2.3 is also there
edit edit: i just now looked at your username...do you speak german by coincidence?

---

### Post by lsutiger on 2011-08-08
:-/ Didn't want to hear that! Oh, well, it may have to be a weekend project! Thanx for your input!

---

### Post by Basher101 on 2011-08-08
Well, thats the bad thing about partitioning. When you have to move a big partition. The fast way is always a pain if you do not have any way to back up your files...glad i could answer your questions. Makes me happy as a noob to help others :KS

---

### Post by lsutiger on 2011-08-11
OK, I cloned my disk so I could play with a spare :) I repartitioned so I have 2GB at the beginning of sdg2.
Attached is a new screen shot. How do I merge the unallocated at the beginning of sdg2 into sdg1?

---

### Post by dino99 on 2011-08-11
as your main partitions are inside the extended one: 
- you might give more room to "swap", its easy as there is 2.95 GiB unused, that will extand swap ~ 5 GiB
- if you dont need sdg1 now, remove it, then sdg2 can be extand to the left.

That done, inside sdg2, you can move "swap" on the very left, and finally sdg6 can be extand too (doing these changes will modify the partitions number)

After validating these changes and closed gparted, you need to update grub:

sudo grub-mkconfig
sudo update-grub

note: VERY IMPORTANT
always use gparted on unmounted partitions: that mean to boot with a livecd (not with the hdd as usual)

---

### Post by lsutiger on 2011-08-11
sdg1 is my boot partition.

---

### Post by Blasphemist on 2011-08-11
> **lsutiger said:**
> OK, I cloned my disk so I could play with a spare :) I repartitioned so I have 2GB at the beginning of sdg2.
Attached is a new screen shot. How do I merge the unallocated at the beginning of sdg2 into sdg1?

You can shrink the extended partition by moving it's left boundary to the right. That will create new unused space outside of the extended partition that you can use to extend your existing primary partition into.

---

### Post by lsutiger on 2011-08-11
OK, attached is what I have now. I booted off of that disk fine. Now I want to claim the 158GB at the end of the drive and use it in sdc6.
Is that possible?
Whatever I try, I can not get it like that.

---

### Post by Blasphemist on 2011-08-11
You just need to expand the extended partition, sdc2, to include all of that unallocated space. Then you can create more logical partitions in that space.

---

### Post by lsutiger on 2011-08-11
Thanks!

---

