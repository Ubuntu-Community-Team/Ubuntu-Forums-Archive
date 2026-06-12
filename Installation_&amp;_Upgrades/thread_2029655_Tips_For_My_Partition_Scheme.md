---
title: "Tips For My Partition Scheme?"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by naathyn on 2012-07-20
Hello everyone.  I am sorry if I posted this in the wrong forum.  I am still getting used to this.  In addition, I am not sure all this information is necessary, but I will provide as much as I can in-case it is.

**Computer:**  HP Pavilion Elite m9510f
**Operating System:**  Dual Boot Windows 7 Home Premium 64-bit + Ubuntu 12.0.1 64-bit
**Processor:**  Intel Core 2 Quad Q8200 (Yorkfield-4M) 2.3 MHz
**Memory:**  LGA 775 (Socket T) 8.2 GB 
**Hard Drive:**  Samsung HD753LJ 700.00 GB
**Video Card:** NVIDIA GeForce 9500 GS 512 MB
**Monitor:** Toshiba TV HDMI 1920x1080+60i

I will start off by saying that, unless I am missing a useful partition, I am not really willing to allocate any more space to  Ubuntu.  I am still very new to this and just trying to learn the  ropes.  Perhaps once I become more knowledgeable, I will be comfortable with allocating more space to a Linux OS.  (Or just buy another hard drive.)

Currently the partition scheme is looking like this:

**ntfs**: 650G (**primary partition**)
--- *extended partition*: 50GB ---
**ext4**: 5GB (**logical partition**)
**ext3 | /root**: 15GB (**logical partition**)
**ext4 | /home**: 18GB (**logical partition**)
**swap**: 12GB (**logical partition**)

Now I have a few questions:  

In what scenario would I need to make swap a primary partition?  I am asking this because Ubuntu's internet browsing is **slow**.  Not the slow like:  "Disable all the extensions, get faster internet, more RAM, etc".  It's the slow as in it takes **forever** to simply connect to a site... but it seems once it connects, it loads right up.  In Windows, I am not having this problem.  Have I given myself too much/little swap?  Is the order wrong?  Should I make *another* swap?

I know the primary partition should come before the logical, but do the order of these partitions make a difference?  In addition, if I *did* make swap a primary partition and stuck it above ext3 (right below the first ext4), does that mean that it is shared between the 4 partitions?  If so, in what scenario would I want to do this.

Also, I have seen some partition schemes using a 200MB (or something along those lines) partition for /boot.  Even though I have read about it (as well as all the mount points and dozens of file systems) I don't quite get how this works and if it could benefit me.

As far as the file systems go, I am shooting for the most effective Partition Scheme as well as the most organized (I have read about Reifier and some of its benefits, but I do not quite understand why *I* would want to use it over ext3, ext4).  

I would be down for allocating more space to Ubuntu if I knew (in words I understand) how a more advanced partition scheme might benefit me. 

Thanks in advance,
Nathan

---

### Post by darkod on 2012-07-20
With 8GB of ram you won't even use swap. The only reason that I know of to have a big swap, is if you plan to hibernate the ubuntu OS. In that case swap needs to be around 1.5 x RAM so that it can save the memory content when it hibernates. Otherwise, swap of 2GB is enough and you can save yourself the other 10GB and use it better.

I don't think the swap is a reason for websites loading slow. In any case, you can check if swap is used at all, and how much memory is used in terminal with:
```
free -m
```

The primary/logical has no meaning to my knowledge. Linux works efficiently with logical partitions.

As for their positioning, I think the "start" of the disk is considered the part of the plate with the smaller circle. So in theory, the partitions towards the start of the disk should be slightly faster. But since you have the first 650GB taken by win7, there will be very little difference in speed between the linux partitions, so reordering them won't make much sense.

About the separate /boot, you don't really need it. It would make a sense if your BIOS can't read boot files beyond the 137GB mark, but in that case the /boot needs to be in the first 137GB and your win7 is there.

For filesystem I use ext4 but I haven't actually looked too much into other options. I think for regular desktop use ext4 is most suitable. If we were talking about server or storage, there might be other options, better.

One thing you could try about the slow browsing is using another DNS. If you get your IP by dhcp from your router, probably the router is the dns too. You can try using the ISP dns servers (you can probably find them on the internet about your ISP), the google dns 8.8.8.8 and 8.8.4.4, OpenDNS, etc. If you do want to change that, you need to open Network Manager, select Edit Connections, the connection, Edit button, then the IPv4 tab, and select the option Automatic (address only). That will receive only the IP by dhcp but not the dns. Below that field there is DNS field where you enter your own manual dns servers.

---

### Post by mastablasta on 2012-07-20
you only "need" 
 
/
/home (optional as partition, home is kind of like My documents folder in windows).
/swap (if you are going to hibernate. and it's size was already explained well).
 
i have only 
/
/swap
 
as i have data on another much larger disk. if i dint' have a second disk i would create a data partition. that way i can easilly "backup" home directory with all user settings to /data partition and do a fresh install and then move the  /home directory back from data partition.
 
i am not sure why you have this in the start:
**ext4**: 5GB (**logical partition**)

 
i hope you didn't create partition called
/root
 
because of it's name.
 
as  / is the so called root partition.

---

### Post by naathyn on 2012-07-20
Thank you two for the help, it is much appreciated.  

Thanks for clearing things up for me Darko, well done.  

And Masta, that ext3 with no mount point was going to be used if I was going to install another Linux OS inside Ubuntu.  I quickly found out thatI am not really interested in doing that as of now.

And I didn't name it /root, I just named it /  Sorry for the confusion.

Thanks guys!

---

