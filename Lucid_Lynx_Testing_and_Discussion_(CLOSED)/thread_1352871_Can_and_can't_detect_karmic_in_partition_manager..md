---
title: "Can and can't detect karmic in partition manager."
date: 2009-12-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2009-12-12
Hi Everyone,

I haven't seen this type of problem before... The Lucid Alpha 1 installer can't detect my current installation of Karmic with the automatic partitioning option... but when I looked down below at the manual partitoning options, it shows I do have Karmic installed. See screenshot...

Also, it wants to automatically partition my storage (slave) drive, and not the primary (master) one. That could be why it shows no operating system in the automatic partitioner option.

Also, if it matters, I booted in low graphics mode because Lucid couldn't configure my graphics card. I am working from the Lucid live cd now. 

On a plus note: Lucid Alpha1 runs great on my pc in virtualbox in Karmic. I think I will try dual booting Karmic + Lucid in virtualbox later, to see if I can reproduce this installation glitch.

James

---

### Post by jocko on 2009-12-12
The only problem in that picture is that it says "This ***computer*** has no operating system on it" when it should say "This ***disc*** has no operating system on it".
As you can see in the picture it automatically chooses to install on your /dev/sdb disc (which doesn't have any operating system on it) instead of /dev/sda. If you want to install on the other drive, just use the option "Specify partitions manually".

And this is nothing new. This is how it has always been. I don't know how the automatic option chooses which disc to use, but I guess it looks for partitions with lots of free space that are safe and easy to resize.

---

### Post by ranch hand on 2009-12-12
Are your partitions mounted?  If so they should show up on your desktop on the LiveCD.  They must be unmounted.

If you do not see them there check using gparted System> Administration>Gparted (or it could be Partition Editor).  You can right click on the partitions and get a menu that will give you an "unmount" option if they are mounted.

For that matter you could do your partitioning ahead of time right there in gparted.  that is what I always do.

---

### Post by ankspo71 on 2009-12-12
Hi jocko and janchhand,

No hard drives were mounted. I double checked in gparted and I also had no icons on my desktop. I have also rebooted and checked again.

I put in my karmic live cd and the installer shows the same as the image in the screenshot. Karmic also wants to install to sdb, says there is no operating system, but it shows it is there in the manual partioner option too.

I was dual booting crunchbang 9.04 plus Karmic, but since my cd burning issues have been fixed (thanks ubuntu devs), I no longer need crunchbang. unfortunately I don't remember what the installer showed me, but I don't remember seeing the image that I provided.

However, I remember dual booting between windows xp and Jaunty, and Jaunty autmatically wanted to install to hda, and let me move a slider back and fourth so I could tell how much space I wanted Jaunty borrow from XP. Unless maybe Ubiquity(?) has changed this much since Jaunty?  I'm sure I can easily install Lucid along side Karmic using manual partitioning, but I felt there was something suspicious with the automated part of it and needed to find out.

James

---

### Post by ankspo71 on 2009-12-12
Maybe I am thinking of another distro that defaults to automatic partitioning with resizing slider options on hda? I need to stop distro hopping!;)


So the question of the day is... has Ubuntu always automatically chosen the second hard drive when someone attempts to dual boot install? I don't remember it doing it that way. :(

For the record, I have 26gb freespace available on hda, and probably 90gb available on hdb (no OS, just storage).

Thanks,
James

---

### Post by ankspo71 on 2009-12-12
Hi Again Jocko,

I just caught your edit. I must have been thinking of the time period before I added a second hard drive. I don't know why it has just suddenly caught my attention now though. 
Thanks for the help.... You too Ranch Hand. :-)
James

---

### Post by ranch hand on 2009-12-12
I have not tried a daily build since the release of A1 but if you are using the A1 CD you are not going to format anything with the installer partitioner.  Ubiquity crashes when you do this.

You need to pre-format your drive with gparted which works fine from the CD.

Then see if the installer partitioner sees your new partitions.  If so just designate the mount point for them (or it if you only use one partition) and do not set it to format the partition(s) and it should install fine.

Your problem with seeing the drives right may be part of the ubiquity problem.

I always format ahead of time anyway because I multi-boot and like to have things set up right (test platform currently running 8 OS').

---

### Post by ankspo71 on 2009-12-12
Thanks again Ranch Hand,

I tried (almost) everything I could to try to share hda with Karmic, but in the end I chose to allow Lucid to use the entire hdb drive. So now each drive has it's own Ubuntu. I wish I had seen your post about not using the format checkbox a few hours ago. I guess you could say I assumed it would crash even if I didn't use the format option so I went for the other option.

At first I used gparted to create a 10gb ext4 partition on hda for Lucid, but whenever I tried to get Lucid to use it... it crashed. I think it crashed each time I toggled the format checkbox (like you said in your reply). So I just used the second partitioning option in Ubiquity(?), which was the erase and use entire drive option. (I decided to use that option because I had already took the time move my stored files somewhere else on hda, but didn't want to move them back again.)

All is installed though, my stored files are in a safe place, Karmic runs on hda, Lucid runs on hdb, and I'm ready to hunt some bugs.:)

Now I know if I wanted to... I can simply reinstall Lucid to the 10gb partition I created and have my storage drive back but only if I choose not to format. I'll do that in Alpha 2, unless I get anxious. :-)

James

---

### Post by ranch hand on 2009-12-12
If you have the space I would make it at least 15Gb.  I admit that the install that I have that is over 10Gb does receive the "source" stuff.  But other than some background .jpg and .png files and of coarse music there is nothing really on there.  One install that does not get the source stuff is at about 7Gb.

All of mine are installed on / and /home.

---

### Post by ankspo71 on 2009-12-12
> **ranch hand said:**
> If you have the space I would make it at least 15Gb.  I admit that the install that I have that is over 10Gb does receive the "source" stuff.  But other than some background .jpg and .png files and of coarse music there is nothing really on there.  One install that does not get the source stuff is at about 7Gb.

All of mine are installed on / and /home.

Hi, yes 10gb doesn't leave much room to work with, but I thought it would be enough for general testing. As soon as I burn a few backup cds for my files, I'll go ahead and split the hda hard drive equally for Lucid and Karmic and try again without using the format option. I wonder if my wife will trade hard drives with me (lol), this 40gb doesn't amount to much. (she probably will because she wants me to reinstall her XP soon anyways)
James

---

