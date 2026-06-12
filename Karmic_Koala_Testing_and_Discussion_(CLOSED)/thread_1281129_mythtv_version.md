---
title: "mythtv version"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by reub2000 on 2009-10-02
I was wondering why Karmic is packaging mythtv 0.22, which is currently alpha. I doubt something that is currently alpha will be released in a month.

My backend is running 0.21, and different versions of mythtv are incompatible. What is the point of something that is this bleeding edge?

---

### Post by ranch hand on 2009-10-03
This is still an OS in testing.  The new version of Myth will have to work on this kernal.  Where better to test it.

Now that is not quite right, we are on 2.6.31.38 and are headed for 2.6.32 but I am sure you see my point.

---

### Post by reub2000 on 2009-10-03
1. It is not the job of Ubuntu to test packages out for upstream.
2. Mythtv is userland program and shouldn't care what version of linux it is running on.

---

### Post by Baron Bosse on 2009-10-13
I have to agree. I'm really anxious to get 0.22 up and running, but including alpha software of such a prominent package seems like a recipe for disaster. 

I hope I'm wrong, though, since 0.22 seems really sweet! :)

---

### Post by rommel74 on 2009-10-25
I've done an dist upgrade from Hardy Haron to Karmic Koala RC and it completely hosed my systems.

The upgrade completed successfully but on reboot the "fun" began.
First of all, my system would not boot with any kernel. During boot I managed to see that it was unable to mount the filesystem. After some investigation I found that one of my drives was not showing up in /dev/drives/by-uuid (was working perfectly fine before). Tried to edit /etc/fstab but the file systems were read only in recovery mode and it just hangs during normal boot. I managed to get around it by setting some kernel options at the recovery selection. After this edited fstab, removed all mounted file systems except the boot drive and ran an apt-get dist upgrade. This allowed me to boot to a command prompt. Fixed up Xorg and managed to boot to gnome desktop.

Mythbackend was not running so I tried to restart it. This did not work, the process crashed straight away. There was nothing in mythbackend.log as to why, nothing at all. Tried running mythtv-setup, this also crashes out. No setup wizard for schema update as I would have expected. Daemon.log is full of errors about mythbackend process stating and terminating but no clue as to why. No log files provided any useful info about mythbackend. The mysql db is fully accessible according to the mythtv check script in /etc/mythtv. 

The only reason I upgraded the backend system was because the frontend machine which was also "upgraded" to Karmic would no longer work with mythtv 0.21. BTW the frontend machine also had the exact same boot issues initially encountered after the upgrade and that was upgraded from Jaunty with entirly different hardware config and only standard packages.

To cut a long story short I'm restoring from backup, hopefully it will work.

I don't understand how this release could be classified an RC with such major issues. I would stay well away from this release.

p.s. I want my weekend back

---

### Post by seeker5528 on 2009-10-26
The changelog when the packages using the 0.22 branch were introduced indicated they expected 0.22 to be ready by the time Karmic was released.

Looks like that didn't quite happen, but the upstream is RC now, so I suspect the packages in Ubuntu are at the same level or close to what the upstream RC is.

Just sayin' it's not like the Myth TV software is Alpha level and with the significance of the upgrade there is plenty of argument that the benefit outweighs the drawback, in particular since Lucid will be an LTS release.

Also it seems to me there is plenty of argument that if you are using Myth TV on a dedicated box, you probably want to be more conservative anyway and stick with Jaunty for the time being, if you don't have some kind of strategy to test new releases without killing the old one. 

Later, Seeker

---

### Post by pj7 on 2009-10-26
Hi,

I too did the upgrade of the backend machine from jaunty (0.21) to karmic (0.22) for the same reasons.

But you have to be a bit more careful in the update;
I did not do a dist-upgrade. Instead: 
- I backed up my old install (/etc /home /usr /var) and the mythdb database (using mysql-admin) 
- I did a clean install of Karmic (the beta version) and setup the system as I wanted first.
- Installed mysql and imported the backup of 0.21 mythconverg
- Then installed mythtv. It automatically converted my database schema to 0.22.

Job done, I have a 0.22 backend running smoothly and I have no problems so far.

---

### Post by reub2000 on 2009-10-28
> Also it seems to me there is plenty of argument that if you are using Myth TV on a dedicated box, you probably want to be more conservative anyway and stick with Jaunty for the time being, if you don't have some kind of strategy to test new releases without killing the old one. That's exactly what is going on. I have 0.21 running on a gentoo box. But I would like to run a front end on my laptop, which is running karmic.

---

### Post by fenian on 2009-10-29
Release cycle for Mythtv is quite long 0.22 has benn in development for over a year.It is now at release candidate and runs quite well in Ubuntu 9.10 with some awesome improvements such as better support for VDPAU,mysql database only on the backend,mythbrowser supprts flash among otther thimgs.I've been running Mythtv 0.22 for a while now and would be upset if the release candidate was not the version in 9.10.

---

