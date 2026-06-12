---
title: "Is my /boot on correct RAID 12.04 ? Did I make a mistake"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by rcollman on 2014-04-05
I  setup a RAID5 (md1) and a RAID1 (md2) using the Ubuntu install image. During setup I said to put  /boot on the smaller RAID1.  I put "/ "on the RAID5.  My boss told to put the \boot and other low activity  folders on  the RAID1 and put /usr and /var on the RAID5. Did I  do this or  do I have duplicate boot directories on each RAID?  Don't do this all the time and do not understand what if any file I need to edit.  This is an older server with 10 150g HDs :)   

A couple of years ago I figured out how to load 3 instances of Ubuntu on 3 different servers.  The third one was easy. Thus I am not a complete newbie but.....  Not afraid to read and learn.  We are early in the setup process so,  reinstalling could be an option.   Thx in advance.

---

### Post by Double.J on 2014-04-05
Hi there!

Short answer: yes!
If you have told the installer to mount a volume on the raid 1 array at /boot and a volume on the raid 5 array at / then all directories for ubuntu will be on the raid 5 array volume EXCEPT for the /boot directory which will be on the raid 1 array. The installer will automatically configure the bootloader so it knows where to load the system, and the /etc/fstab file so that the /boot volume is automatically mounted at /boot when the system starts.

one thing - your boss said to put /var and /usr on the other raid array? Have you checked if he wanted seperate partitions for these directories as well? It is common to create extra partitions for these directories as well as /home and /tmp as they will grow the most over time (depending on usage and maintenance). The thinking is that if the partitions these directories sit on become full, the root system will not suffer Impeded performance. 

Not sure which other 'low activity' directories they wanted on the raid 1 array, [this]("https://help.ubuntu.com/lts/installation-guide/i386/directory-tree.html") may help?

Jj

---

### Post by rcollman on 2014-04-06
Many thanks, at least the Ubuntu installer is sort of logical for the old C/PM DOS guy, who was dragged kicking and screaming into the GUI world!   Appreciate the advice on partitions.  He didn't mention but  he probably expects me to figure out what I think it best and make a recommendation.   

The link looks very educational, just looked at the first couple of pages.   It looks like I should put /etc, /bin, /sbin, /lib and /dev on RAID1 along with /boot.   Anyway, I need to do some more reading and refreshing concerning the basics once again.  

In two days I will be back at work, with my wax ear plugs working on the server in my spare time.  Figure I better get this straight before loading up programs  under /www :)  Thx again.

---

### Post by rcollman on 2014-04-08
Decided I needed practice.  Used the CD and deleted the RAID5, then made it again.   RAID1 is now mda and a UUID ####1 and I set it to mount / with ext4.  The RAID5  is now mdb and a UUID###2 .  Ubnuntu boots up just fine.     

Assume I could put some other mount points on UUIDXXX2. I want /usr and a /data  to be located there.  Assume that since I did not say to mount /usr this directory would remain on UUDI XXX1, the RAID1.     So how to  I move it?

I think of UUIDs as drives.  I am tempted to go to FSTAB and copy the UUIDXXX2 line and change it to /usr to see what happens.   Feel stupid :)

---

