---
title: "How do i repartition my hard drive partition to small"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Peterfc on 2008-04-29
A total newbie to Ubuntu. Just done a clean install of Hardy 8.04. I have my partition set too small can anybody help please.

---

### Post by Six_Digits on 2008-04-29
Set to small?
You mean set **too **small?

gparted my friend.
Do some searching too:

[http://ubuntuforums.org/showthread.php?t=770495&highlight=gparted](http://ubuntuforums.org/showthread.php?t=770495&highlight=gparted)
[http://ubuntuforums.org/showthread.php?t=771028&highlight=gparted](http://ubuntuforums.org/showthread.php?t=771028&highlight=gparted)

You'll have to do it from the LiveCD if you're currently running on the partition you wish to edit.

---

### Post by Lord Landis on 2008-04-29
> **Peterfc said:**
> A total newbie to Ubuntu. Just done a clean install of Hardy 8.04. I have my partition set too small can anybody help please.

How do you have them set up?

Yes, you'll need to use the gparted liveCD to re-size them (unless you want to do a complete re-install), but it's really quite easy to use.  

Just make sure that you make a full backup of anything you've put on there that you need to keep, just in case.  I've used gparted on production servers, and it's worked without a hitch, so you should be fairly safe.

---

### Post by Shadius on 2008-04-29
> **Lord Landis said:**
> How do you have them set up?

Yes, you'll need to use the gparted liveCD to re-size them (unless you want to do a complete re-install), but it's really quite easy to use.  

Just make sure that you make a full backup of anything you've put on there that you need to keep, just in case.  I've used gparted on production servers, and it's worked without a hitch, so you should be fairly safe.
How do you do a complete reinstall of Ubuntu on Dual booting computer? Also, how do I remove the partition Ubuntu's on and give it back to Windows? How can I view the partition that Ubuntu is on?

---

### Post by Posterus on 2008-04-29
> **Shadius said:**
> How do you do a complete reinstall of Ubuntu on Dual booting computer? Also, how do I remove the partition Ubuntu's on and give it back to Windows? How can I view the partition that Ubuntu is on?

you give little info...im guessing that you have a dual boot right now with windows and ubuntu? and one of your partitions is too small? you can just run the ubuntu live cd and use the partition editor and resize the partition from there...you will see all of the partitions in there, you will most likely have to shorten the windows partition and move it, then enlarge the ubuntu partition...as for "remove the partition Ubuntu's on and give it back to Windows" there is no point at all in doing that unless you are trying to get rid of ubuntu completely...other than that there is no difference......may i suggest a defrag b4 you do this though, it'll make the change faster

---

### Post by Shadius on 2008-04-29
> **Posterus said:**
> you give little info...im guessing that you have a dual boot right now with windows and ubuntu? and one of your partitions is too small? you can just run the ubuntu live cd and use the partition editor and resize the partition from there...you will see all of the partitions in there, you will most likely have to shorten the windows partition and move it, then enlarge the ubuntu partition...as for "remove the partition Ubuntu's on and give it back to Windows" there is no point at all in doing that unless you are trying to get rid of ubuntu completely...other than that there is no difference......may i suggest a defrag b4 you do this though, it'll make the change faster
Sorry for the little info. Yes, I am trying to remove Ubuntu altogether.

---

### Post by Six_Digits on 2008-04-30
This is what I did last time I removed Linux:
1. Boot Windows - Erase Linux Partition/s
2. Create a Super [GRUB disc]("http://www.supergrubdisk.org/index.php")
3. Create back-ups if you haven't already (I backup like a maniac)
4. Restart with Grub disc
5. Restore Windows boot-loader (MBR)

Done! This is what worked for me but MAY NOT be the correct way to do it.

---

### Post by Posterus on 2008-05-11
you could use a windows cd instead of super grub to restore the mbr

---

### Post by valjour on 2008-05-12
Peterfc- 

I just did a clean install too and manually partitioned my HD.  I took the time to figure out what I needed for each partition, I have four.

I personally think that reinserting/installing your Hardy CD (after changing bios to CD read first) and use ubiquity if you have a cd and it isn't live.  In the guided section their is a slider (the line underneath the bar) to change partition size if you haven't made too many changes to Hardy yet it might work.  That would truly be easiest on you and give you more space on your first partition. Or go totally manual but be careful!  Make sure to read the box before you install it at the bottom it tells you the partitions and sizes.  I used the back button (which wipes out all the work you have previously done)  several times before I was comfortable with the sizing.

I'm just a newb too.  Gparted seemed complicated but I know this is the tool to use after the fact if you can't change the facts. 

If this doesn't help you at this stage of the game I hope it helps someone out there with install partition problems.

Another Pete :)

---

