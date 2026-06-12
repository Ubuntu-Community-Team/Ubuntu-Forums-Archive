---
title: "[SOLVED] Resizing Partition Failed"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by ilych on 2008-02-24
Hello,

I am trying to setup a dual boot for Ubuntu, but when I use GParted (not with the Ubuntu LiveCD) to try and resize the partition which WinXP is installed on, I receive "An error occured while applying the operations".

Please view my error log [here](http://www.thelittlerock.com/ubuntu/gparted_details.htm).

Before attempting to resize my partition, I defragmented my hard drive and also performed a chkdsk /f.

I could not find similar posts on this forum that could help my problem.

Thanks for any help!

---

### Post by logos34 on 2008-02-24
> Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

That's from the last part of your error message.  Did you do that?

---

### Post by Charcoal1981 on 2008-02-24
From the looks of your error log, you did not shut windows down properly before loading the Gparted Live CD. Assuming that Gparted has not nuked you system (which it doesn't look like it did) you just need to boot into windows, shut down properly (not hibernate) and then run the Gparted Live CD again.

Make sure you have backups of critical data before you start!

---

### Post by ilych on 2008-02-24
Thanks for the replies. I shut down my computer completely then booted from the GParted live CD.

However...it's been resizing my partition for 2 hours already (it shows "real resize" below the progress bar). Does it normally take this long? If not, what might be the problem, and should I cancel it or wait a bit longer?

Thanks again.

---

### Post by forestpixie on 2008-02-24
it can take a while - don't cancel it

---

### Post by ilych on 2008-02-24
Thanks, it finally finished. I am currently setting up my partitions in this manner:
[http://img379.imageshack.us/my.php?image=partitioning4mz5.png](http://img379.imageshack.us/my.php?image=partitioning4mz5.png)

But what does that really mean?
1. After I finish partitioning, do I select to install in the Ubuntu /ext3 partition?
2. In Ubuntu, how do I access/write in the shared partition (FAT32)? Does it appear as a drive on my desktop? A folder?
3. Lastly, how do I make my settings all go into the /home ext3 partition?

Thanks for helping a novice out!

---

### Post by forestpixie on 2008-02-24
not sure what sizes you've got the partitions at - but I for instance have 9GB for / and 50Gb for /home 

when you install - go manual then pick the partitions and choose the mountpoint - / for / and /home for /home swap sorts itself

ubuntu should find the fat32 partition and put it in your fstab which will mount it 

> Lastly, how do I make my settings all go into the /home ext3 partition not usre what you mean - but /home is used to store configurations and data for you 

does that help

---

### Post by ilych on 2008-02-24
I'm only allocating a little more than 1 GB for /home. Why do you have 50 GB for it? Isn't it just for "configurations and data"?

This setup is supposedly helpful for reinstalling future versions of Ubuntu (per this [tutorial]("http://www.psychocats.net/ubuntu/partitioning")). How is that accomplished? In other words, when I reinstall, how do I preserve the "configurations and data" in /home?

> not usre what you mean - but /home is used to store configurations and data for you 

My question is: Do I need to do anything so that configurations and data are stored in /home, or does Ubuntu automatically configure that?

Thanks again, I can't wait to install Ubuntu after all this partitioning is done!

---

### Post by forestpixie on 2008-02-24
yea - I've got docs and music and on and on and on in /home and a couple of other partitions if you get my drift - you have that monstrous shared partition :)

as far as configs etc - that's where they get put as standard - bit like My Documents in the other well known OS

When you reinstall - choose manual method for partitioning as you'll do this time, but just don't let the install format /home

I wish you well - see you on the other side of the install

as an aside - if the install appears to hang at about 82% when it's scanning mirrors - it'll get there eventually :D

---

