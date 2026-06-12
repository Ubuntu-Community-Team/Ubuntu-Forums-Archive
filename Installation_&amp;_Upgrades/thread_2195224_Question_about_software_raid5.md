---
title: "Question about software raid5"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by feardotcom on 2013-12-23
So i have a home server and i have ubuntu 13.10 server installed and everything works. But i'm considering planning a software raid 5 setup. I've read that i can have the OS installed on the raid 5, and I've also read that i CAN'T have the os installed on the raid 5. That it has to be on either a separate partition or a separate hard drive. Which one of these is correct? If i CAN'T have the OS installed on the raid 5 and i have to install on another hard drive then what happens to the raid 5 if my os hdd has to be replaced or reinstalled? My case will only hold 7 hard drives, and i'm trying to maximize my hard drive capacity.

This raid stuff is new to me.

---

### Post by TheFu on 2013-12-23
The answer to "should" and "can" are often different.  Just because something "can" be done, that doesn't mean it "should" be done.

I suppose a RAID and Linux expert "can" have the OS installed on a RAID5 partition, but for the rest of us, we "should NOT" do that.  The main reason is that when something bad happens, without the needed skill level, the machine can be left in a situation that we don't have the skill to recover.   It could be bad, very bad.

If you like, you can boot off a USB drive, have the OS and Apps on that and use SATA ports for the RAID.  10G for the OS and Apps should be plenty.  My daily use desktop the last 6 yrs only has 14G total and that includes my HOME.  Many of the servers I run are completely contained within 4G of storage (including all the data), so 10G should be plenty if there aren't any GUI programs.

I use RAID10 for data storage, but previously used RAID5 (when HDDs were much smaller). A few times when there were issues, I was happy that my OS was NOT on the RAID devices. Fixing issues on an actively used RAID set would ahve been ... difficult.

Just keep the data else where and make really, really good daily backups of the OS, settings and apps. Be religious about it.  Mirror the USB flash drive to have a 100% swappable OS/Apps boot disk too. There is your redundancy.

I've read that Ubuntu has issues with RAID for the OS partition, but that CentOS handles it easily. I don't know if that is true or not - haven't done any RAID with CentOS ever.  At this level, the specific distro does matter.

Can and should - there is a difference.

These are my opinions. Someone else will almost certainly chime in with a different opinion.  I am conservative when it comes to my data.  I still use JFS a few places and only switched to using EXT4 in the last year or so. Never used ext2 or ext3 since JFS was a better all-around solution for my needs. Data is more important than speed to me.  I am religious about backups and test the restores from time to time.  

2 yrs after BTRFS becomes standard on Ubuntu is when I'll start to consider using it on test system. It will take another year before the first prod box gets that file system. I'm conservative.

I'd also point out that 13.10 is too new for me to use. The support on it is just 6 months, so it isn't something I can really consider - especially for any "server."  By running that, you've demonstrated a greater ability to accept risk than I. Part of your consideration of my comments, I'd wager.

Only you can decide what makes the most sense for your systems.

Happy Festivus!

---

### Post by feardotcom on 2013-12-23
Thank you for your answer. So if i could find some old server hard drives for cheap that are still in working condition (highly likely) i guess i could set up the os hard drive in raid 1 on a raid card, pull out the cd rom and use that slot for the 8th hard drive then. some old 80gb sata1 drives laying around but i wouldn't trust it to run in a 24/7 environment. 

Is it possible to run ssd's in raid1? I can get 8gb ssd's for cheap. I have a question about the small hdd's is that it recommended to have atleast the same amount swap as you do ram, which would put me at about 16-20GB instead of 8, By what your saying with the same hdd that i dont need such a big swap space? or did i misunderstand? All the sever is used for is file sharing. I'm getting ready to start ripping my entire dvd/br collection in hd which will exceed my current 1tb drive.

---

