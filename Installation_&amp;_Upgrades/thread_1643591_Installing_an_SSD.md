---
title: "Installing an SSD"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by reablom on 2010-12-12
I've been looking around on the forum for some help on this, but even though it seems to me that more people probably have the same questions as me I haven't been able to find a thread about this.

I want to do the following: currently I've got Ubuntu Maverick installed on a 500GB HDD. I'm thinking about installing an SSD for two reasons: 

- Reduce boottime
- Reduce startup time of applications (e.g. FireFox and OpenOffice)

Currently I've got three partitions on my Samsung HD
- one for the OS (chosen a bit too large at 50GB) 
- one for the home 440GB
- swap 10GB

Some advise how to go about would be nice. For example: 
- Can I keep all the data in my home folder or is it best to make a back-up and do a "clean" install and put it back?
- How about all other programs I installed (Picasa, Krusader, Spyder, Grisbi,...)? All lost? All personal stuff of these programs should be in my home folder right? Will those programs pick that up once I copy the backed-up data to the home folder?
- Where to put the swap space? For speed in the SSD I guess, but repetitive read/writes are thought to be bad for SSD lifetime. Or is that outdated?

Any help is appreciated.

---

### Post by dixonstalbert on 2010-12-12
hello

i recently upgraded my system with a 60 gig SSD as my boot drive.


I am running 50 gig for ubuntu 10.04 including home directory and 10 gig swap space.

I have a 14 gig virtualbox of Windows 7  and a 12 gig  windows 2000 in my home directory and have about 3 gig free space left over.


You can try booting from a LiveCD set up the drive partitions then use rsync to transfer data from your harddrive to your ssd. 

I did a clean install because I needed to do some housecleaning. I then copied over my .virtualbox my .thunderbird and .mozilla directories and my Desktop directories from my old install into my new harddrive.

Before the ssd I had upgraded from an Athlon XP 1.9 gig /DDR400 to a Athlon 975 quadcore with DDR12800. The cpu upgrade probably sped things up about 40% ,while the ssd seems to have sped things up by over 200%. 

Also, I was running into system stability problems with hibernate because my previous 2TB so-called 6GB/sec HD took so long to start-up/shutdown and I spent weeks tweaking things to try and get reliable hibernate. After I went with SSD, hibernate consistently works.

As to your question about putting swap on ssd, check the ssd specs, I seem to remember my is rated at lifespan of many millions of read/writes.  I have not done the calculations, but I believe that should meet my needs of 3-5 years before I will want to upgrade again.

---

### Post by oldfred on 2010-12-13
I do not have SSD.

This was for Karmic but shows a SSD install.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
Edit: I left out link, Herman has it below now, with additional comments:
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

You can export a list of all your installed apps. I do this regularly and include it in my backups. If you have made any system wide settings those will be in /etc. I try to save anything that I edit in /etc to another file in /home so I automatically have backups.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

If you have a lot of RAM you should not be using swap anyway. Herman in the link above on SSD, I believe only creates a swap file in root. He says you should have some swap as it checks somewhere for it and without it, certain activities were slower.

If you mount your current /home as part of a new install (and not format it) all your settings will be found when you reinstall your apps.  I keep several Ubuntu installs of 20-25GB but have all my data in /data partition. My /home is only about 1GB as all the data is elsewhere.

---

### Post by reablom on 2010-12-13
> **oldfred said:**
> I do not have SSD.

This was for Karmic but shows a SSD install.



Was there supposed to be a hyperlink here?

---

### Post by dabl on 2010-12-13
> **reablom said:**
> 

I want to do the following: currently I've got Ubuntu Maverick installed on a 500GB HDD. I'm thinking about installing an SSD for two reasons: 

- Reduce boottime
- Reduce startup time of applications (e.g. FireFox and OpenOffice)

Currently I've got three partitions on my Samsung HD
- one for the OS (chosen a bit too large at 50GB) 
- one for the home 440GB
- swap 10GB

Some advise how to go about would be nice. For example: 
- Can I keep all the data in my home folder or is it best to make a back-up and do a "clean" install and put it back?



At this point, and considering the following question, it's probably better to just leave it as-is.  If it's bothering you that the OS has way more space than needed, you could use GParted and shrink the "/" partition, and then enlarge the "/home" partition to use the free-up space.  Leave the OS plenty of headroom -- maybe take it down to 15GB.

> 
- How about all other programs I installed (Picasa, Krusader, Spyder, Grisbi,...)? All lost? All personal stuff of these programs should be in my home folder right? Will those programs pick that up once I copy the backed-up data to the home folder?



The good news is -- yes, your custom settings will all remain.  The bad news is -- all wrong and unneeded settings will stay too.  ;)

> 
- Where to put the swap space? For speed in the SSD I guess, but repetitive read/writes are thought to be bad for SSD lifetime. Or is that outdated?



Does your system need to swap to run (i.e. small memory), or is it just for hibernate (suspend to disk)?  If it is just for S2Disk, then there's no excessive writing -- it's just one write per hibernate.  If your system is routinely using swap, then you need more memory worse than you need an SSD.

I have recently installed on two different SSDs, so I will share a few pointers.

1. For _your_ make and model, learn what it takes to perform a correct alignment of the first (and any additional) partitions. For example, OCZ forums threads are [[COLOR="Green"]**here**[/COLOR]](http://www.ocztechnologyforum.com/forum/showthread.php?48309-Partition-alignment-importance-under-Windows-XP-(32-bit-and-64-bit)..why-it-helps-with-stuttering-and-increases-drive-working-life.&p=335049#post335049) and [[COLOR="green"]**here**[/COLOR]](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226).

2. Use ext4 filesystem, but use the "commit=nnn" mount option to change the frequency of the journalling to longer than the default 5 seconds. For example, commit=300 is every 5 minutes and commit=600 is every 10 minutes.  Of course you're trading off data security in the event of power loss.

3. Use the "vm" options available for /etc/sysctl.conf to slow down some of the filesystem syncing.  Here's the end of mine:

```
.
.
# Log Martian Packets                                                                                                                              
#net.ipv4.conf.all.log_martians = 1                                                                                                                
#
vm.swappiness=1
#
vm.vfs_cache_pressure=25
#
vm.dirty_writeback_centisecs = 30000
vm.dirty_expire_centisecs = 30000
vm.dirty_ratio = 50
vm.dirty_background_ratio = 2
#
```

4. Mount the /tmp directory and the /var/log logs on a tmpfs. (If you need to preserve the /var/log files after a reboot, you'll have to grab them manually, or write a script to save them somewhere).  So, your /etc/fstab might end up looking like this:


```
UUID=31c31df6-b090-43e9-8826-8513fd876370     /                    ext4       defaults,noatime,errors=remount-ro,barrier=0,discard,commit=300 0 1
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306     none                 swap       sw 0 0
UUID=ec21f5b3-7fd4-4f4b-af8d-cf787b147ae8     /mnt/REVODATA        ext4       auto,users,rw,exec,noatime,barrier=0,discard,commit=300 0 2
UUID=97ff1207-32a4-4856-b1a4-fc4eb87b7b97     /boot                ext4       defaults,noatime,errors=remount-ro,barrier=0,commit=300 0 0
UUID=9f1a991c-6ad6-40af-ba59-c10638a211c5     /mnt/WHATEVER        ext4       auto,users,rw,exec,noatime,commit=300 0 2
UUID=8206cc53-cf7d-4fa1-a62f-b358aedc8658     /mnt/DATA            btrfs      defaults 0 2
none                                          /tmp                 tmpfs      defaults,noatime,mode=1777 0 0
none                                          /var/tmp             tmpfs      defaults,noatime 0 0
none                                          /var/log             tmpfs      defaults,noatime 0 0
none                                          /var/spool           tmpfs      defaults,noatime 0 0
```

Hope this gives you some ideas to work with!

---

### Post by Herman on 2010-12-13
> This was for Karmic but shows a SSD install.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation:D Thanks for providing links to my web pages, oldfred, it's nice to think somebody will benefit and I'mnot just wasting my time making them. 

It's now called "[Ubuntu Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html")", (not specific to Karmic).

I just ran through the installation in that page yesterday, and it works just as well for Maverick Meerkat as it did for Karmic, the only small change I noticed was in the screen where Ubuntu guesses your time zone and you have the option of over-riding it manually if it's incorrect. Other than that the procedure remains identical as far as I can see.

I added a note close to the top of the page to explain that the goal of that particular type of installation was for making a portable Ubuntu installation in a drive that's more durable than a HDD and is secure, (in case you lose it). That kind of installation is okay for speed, but it doesn't result in the fastest SSD possible performance. 

I wonder if I should make a page about how to install in an internal SSD (without file system encryption), with the emphasis on creating a Ubuntu installation in an SSD for maximum speed and performance?  

I agree with dabl, in so far as SSD optimization depends on the exact make and model of SSD, so you really should go to your SSD drive manufacturer's website and follow instructions there if you want to obtain best performance.
> 1. For _your_ make and model, learn what it takes to perform a  correct alignment of the first (and any additional) partitions. For  example, OCZ forums threads are [[COLOR=Green]**here**[/COLOR]]("http://www.ocztechnologyforum.com/forum/showthread.php?48309-Partition-alignment-importance-under-Windows-XP-%2832-bit-and-64-bit%29..why-it-helps-with-stuttering-and-increases-drive-working-life.&p=335049#post335049") and [[COLOR=green]**here**[/COLOR]]("http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226").  :smile:

---

### Post by reablom on 2010-12-14
> **Herman said:**
>  
I wonder if I should make a page about how to install in an internal SSD (without file system encryption), with the emphasis on creating a Ubuntu installation in an SSD for maximum speed and performance?  



That would be great! For the migration part: I think I'll just back up all data from my home folder to a USB HDD, format the HDD, use it to mount home and copy all data back to the HDD. I'll leave the swap on the SSD I think. I've got 4GB of RAM and swap does not seem to used at all.

> **Herman said:**
>  
I agree with dabl, in so far as SSD optimization depends on the exact  make and model of SSD, so you really should go to your SSD drive  manufacturer's website and follow instructions there if you want to  obtain best performance.
  :smile:

I read these posts, but I don't understand completely. Also they give different advice one post says align to 56 sectors/track while the other one says align to 32 heads and 32 sectors/track... 

Besides that: I normally let the ubuntu installation create the various partitions by itself. If I understand correctly, now I have to first create the partitions using fdisk (and maybe a live cd) and than install to these partitions. I guess I should choose the manual partitioning method during ubuntu install?

---

### Post by Herman on 2010-12-15
You only need to create the MBR with fdisk, once your number of heads and your number of sectors per track are set in the MBR you can go ahead and create partitions in the normal way with GParted.
I recommend Maverick Meerkat's GParted version 0.6.2 or better.

I haven't tried out the Ubuntu installer's inbuilt partitioner used in Maverick, but the stand-alone GParted in Maverick defaults to creating partitions that are aligned, (they start at sector 2048 ).

I'm using 32 heads and 32 sectors per track for mine and it seems to be working very well. Mine's a OZC Vertex and that's what is recommended at the OCZ forums for it.

Make sure TRIM is working, (I installed an updated version of hdparm and installed wiper.sh and DiskTrim to get that working. I had to flash my SSDs firmware first but probably you won't need to do that, times have changed over the past year or so and things have advanced a lot. Yours will probably come with TRIM enabled already. There are some other tweaks and settings we can use too. Using kernel boot option 'elevator=noop', or 'elevator=deadline' is one, setting 'noatime' in /etc/fstab is another and tuning swappiness and a few other things..., oh yeah, setting the file system alignment is another.  :)

---

### Post by reablom on 2010-12-21
Ok guys, thanks, great help. To finish up this post, this is what I did:

1. Install SSD in my PC and boot normally using the HDD. Use tip from oldfred to save marked packages.
2. I followed this [http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk ]("http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk") thread. I made two partitions: one of 45GB for installing the OS and one with the remaining 10 GB, which I partitioned as swap space. 45 GB is more than enough for the OS, during normal use swap isn't used, but I figured maybe I want to use hibernating, then that is faster on the SSD.
3. Reboot and install Maverick Meerkat from a CD. I assigned the partitions manually and mounted my old home folder at /home.
4. Reboot and set the SSD as primary boot device (in the BIOS)
5. Set discard option in /etc/fstab and reboot
6. Check TRIM is working: [http://andyduffell.com/techblog/?p=852](http://andyduffell.com/techblog/?p=852)
7. Reduce swappiness to prevent using the swap space during normal use (I have 4GB RAM) [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
8. Set noatime option ([http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)) and commit=300 as suggested in previous posts.

Result of the Disk Utility benchmark:
Minimum read rate 183 MB/s
Maximum read rate: 267MB/s
Avg read rate: 255MB/s
Average access time: 0.2ms

Seems fast enough to me, my Samsung HDD is around 50MB/s. The system sure is faster (booting, firefox, OpenOffice)

(Oh yeah, I've got an OCZ Vertex II)

---

