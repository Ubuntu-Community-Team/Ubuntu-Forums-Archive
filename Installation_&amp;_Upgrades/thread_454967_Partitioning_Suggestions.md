---
title: "Partitioning Suggestions"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by toppy on 2007-05-26
I just purchased a new machine to use solely for Linux which I mainly use for PHP and MySQL developing.  But now that I finally have a decent machine to run Linux on I'm planning to try a few more things and wanted some advice on partitioning.

I have a 320 gig SATA drive and a 60 gig ATA.  I'm considering having multiple Linux distro's such as:

1) My main/developing/stable install of Kubuntu
2) An install I can play around on, tweaking, compiling a new kernel, trying to break stuff
3) A boot for testing various cluster distros/programs (and hopefully settling with one)
4) Most likely another partition for trying new distros, maybe a lean tweaked install for trying linux games.

I'm even considering more just so I don't have to mess around with partitioning if I end up using the above for things I like.  But that may be a bit of an overkill.

The remaining drive space would just be general network storage, a place to put download content, music, etc.  I was expecting the 60 gig would be part of that storage space.

So any suggestions on how much to allocate to each partition, file systems, etc?  Would swap space for each distro be needed?  Would doing all this be an overkill?

---

### Post by blueturtl on 2007-05-26
Since you do have two hard-disks has it occured to you to separate the operating systems and applications on the 60 GB disk and the data to the 320 GB disk? The benefit is that if you play around with your installations you won't be messing with the partitions or partition table of the disk that contains everything dear and valuable to you. Just a thought. It could be something like this:

60 GB ATA

7 gigs for distro x + 3 gigs for home x (your main developing / stable)
7 gigs for distro y + 3 gigs for home y (experimental)
7 gigs for distro z + 3 gigs for home z (cluster distro)
7 gigs for distro v + 3 gigs for home v (experimental2/gaming system)
some 0.5 gigs of SWAP (I think this can be shared as only a single system will be running at each time)
rest of the remaining space for game data, something like /mnt/games (games can take a lot of space)

320 GB SATA
all space dedicated to your precious files, music, pics, movies, backups, what ever
/mnt/storage

The reason there'd be a separate home for each system is that you'd have separate users / profiles for all systems (your settings under experimental wouldn't effect your settings under the stable distro and vice versa). Evaluate the space required by each system. It's just a draft and I have no idea how much space you usually require for example in your home folders.

---

### Post by rillip on 2007-05-26
Remember that there is a 4 partition limit per drive, so you would have to either make one of those have a logical partition (i.e. one distro has it's space and the swap space in the same real partition) or put the swap on the data drive.

I would recommend putting the swap on the data drive so that you have seperate IO.  It provides a nice bit of parallel IO that will probably be noticible if you are paging frequently.  This lets you move up to more swap space if you need it, also (.5 is a bit skimpy, depending on your ram).

Otherwise, I agree with blueturtl, that seems like a very sensible paritioning scheme.  You can also probably make it a little bit more slanted toward your space, if you need to.  My install is under 4gb at the moment, so you can probably shift depending on what your current install looks like.

---

### Post by toppy on 2007-05-26
Thank you kindly for your answers, they are very helpful!  I was really unsure about the swap and if it kept data stored after a shutdown.  I'm only running 512 megs of memory right now, not sure how long that will last, specially if I'm compiling kernels.

I hadn't consider using the 60 gig for the boot and operating systems.  Reason being is I figured the 60 gig ATA 133 being slower would be just a storage drive.  Wouldn't it be a big performance hit having all the loading access on the  ATA?  

Having the swap on a separate drive for the parallel IO is a good idea, I hadn't thought of that.  If all the downloads, big file copies and music playing was running of the SATA drive the performance hit may be less critical?

---

### Post by blueturtl on 2007-05-26
Considering your questions about the performance:

You are right, the newer driver probably is a little faster. However the difference comes mostly from seek speed rather than the defined maximum bandwidth for the drives (SATA has a higher bandwidth, but that doesn't mean the drive can automatically reach those transfer rates).  If you installed your operating systems on the 320 GB disk you would have to force data on the same disk which would hurt performance somewhat anyway as well as increase the risk of data loss just that bit while modifying partitions and system installs.

The easiest thing would be to have the home or homes on a separate disk. That way starting up OpenOffice or something else will not impact your cd-burning or music listening or something else that is probably mostly tasking the drive with your personal files on it. The "problem" that you have is that your second hard-disk is pretty sizeable to contain just four operating system root directories... after all Ubuntu in all it's glory can take up to about 3-4 gigs. Even with multiple separate installs that leaves a lot of unused space on the 60GB drive.

One thing that might also help performance is separating home and long term storage volumes. This is because your home dir will contain all the settings and thumbnails and caches and what-not. These files are frequently read and modified. I think home folder is more prone to fragmentation.

You only have so many actual drives so this is pretty much up to you.

My setup goes something like this:

40 GB primary:

20 GB /windows (a partition that is actually dedicated to my windows virtual disk image)
20 GB system root

120 GB secondary:

0.5 GB swap area
20 GB home
99.5 GB storage

---

### Post by rillip on 2007-05-27
In regards to performance, it's a balancing act.

Consider the IO we're going to be doing:

1. Loading system files, i.e. the OS
2. reading system files, for progs
3. reading data files for progs
4. writing data files for progs
4. reading from the swap to load a background prog
5. writing to the swap to store a backgroung prog

1. encourages OS on the SATA.  But, this is only an issue during boot.  Once booted, it becomes largely irellevant. So OS on SATA gives slightly faster boot time, and inconsequential speed increase on the occasions the OS needs to access a non-loaded OS file

2. Encourages your programs on SATA.  Default installation will put all of your programs on the / partition, which encourages OS on SATA.  However, these files that it would be loading will be very small, for the most part.  The SATA would offer a spead boost, but not one you're likely to notice, or if you do, it'll be inconsequential.  You might be able to leave the OS on PATA but get it to instal your programs on SATA, which would eliminate the issue entirely.

3. You want your data files on SATA, not only for the increased storage, but because this is where your BIG IO comes in.  You can reasonably expect your data files to be > 1mb on average, while the average system file is probably going to be around 2kb.  

4. See 3.

5.  You're going to read and write to a 500mb - 2 gb swap file every time you start using a program that's been cached.  Whether you need this on SATA or PATA depends largely on your usage, i.e. how many programs do you use at once. For example, I'm only using 21mb of swap right now.  For me, putting it on PATA wouldn't cause a signifigant decrease.  If you like to minimize your Memory Hog Game to go chat on IM and browse the forum while you wait for X Event, you're likely to be using a signifigant ammount of space.

But either way, there's no performance increase to be gained by putting it on PATA, unless you put the OS on SATA.  

So in sum:

Files want to be on SATA.
Files want to have a seperate IO stream from the OS
Thus, OS should be on PATA and Files on SATA.
Thus, swap should be on SATA so it has seperate IO from OS.

Of course, ideally, you'd just have two sata drives on seperate busses, but barring that, I think the best performance you can get is to put the OS on PATA and everything else on SATA.  You may or may not be up to the task of making your apt installed software put on the SATA drive; I don't know how difficult it is and haven't tried to do this..  It would increase performance, but it's an extra ammount of difficulty, could become messy if you start uninstalling OS's and end up with, say, KDE programs laying around you don't want because you have Gnome and Fluxbox setup or something.  To keep things simple, I would just eat the little bit of speed you're losing on little file reads, and save the performance boost for where you'll see it most, on large files.  And you have the added bonus that ti's a seperate bus, giving you parallel IO.

My setup is as follows:

Win2k on hda1 22gb
Ubuntu / on hda 3 18gb (they were 18/18 and then 1/1 swap space, but when I got my SATA I put the 2 swap back on Win2k)

/mnt/storage on sda1 60gb
/mnt/shared (fat32) on sda2 18gb
Win2k swap on sda3 1gb
Ubuntu swap on sda4 1gb

I keep all my files on /storage, unless I want to use them on both, then put it in /shared, both of which are on the faster, larger SATA, much like blueturtl's setup

---

