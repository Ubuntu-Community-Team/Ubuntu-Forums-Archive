---
title: "ubuntu 12.04 64-bit installed by wubi is extremely slow"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by hexicn on 2012-06-02
Hi,

I installed ubuntu 12.04 64-bit version with wubi, and when I try to compile something, it is 10 times slower than 11.10 32-bit version.
If I run a simulation, I can see it lags every 0.5 seconds.

I have 64-bit cpu, and installed from a 64-bit windows7.

Is anyone experiencing the same problem? Do I need to switch back to 32-bit version with wubi?

---

### Post by mastablasta on 2012-06-02
since oyu are suing it for serious work wouldn't it be better to create a side by side boot? wubi is limited and ment only for testing the OS on ocmputer with minimum changes to the default widnows OS.

---

### Post by Mark Phelps on 2012-06-03
> **hexicn said:**
> Hi,

I installed ubuntu 12.04 64-bit version with wubi, and when I try to compile something, it is 10 times slower than 11.10 32-bit version.
The performance drop you get from running Ubuntu installed with Wubi is negligible.  You shouldn't even be able to notice it in normal usage.

Your major performance drop is due to switching from 11.10 to 12.04.

> Is anyone experiencing the same problem? 
LOTS of folks are reporting performance drops, although not a serious as the one you're experiencing.

> Do I need to switch back to 32-bit version with wubi? You're not going to see a performance increase switching to 32-bit 12.04.

---

### Post by asgromo on 2012-06-04
Run top in a terminal and see if mount.ntfs is working 80% CPU any time you're doing any disk intensive operation. I'm not a genius, but i have a feeeeeling whatever the issue that's causing that is in turn causing my Wubi problems. I'm going to repartition and see if it goes away, but my Wubi trial has been an enormous waste of time. Like, a "throw this perfectly modern and standard barely-used laptop across the room if i had more of a tendency to express my frustration" kind of waste of time.

If anyone tells you that you should just not, uh, use Wubi, tell them to be quiet and go away. Judging by the Google results it just looks to me like another "not a bug" problem so common with your Big Popular Linux Distros when they advertise features that in practice maybe sorta kinda work. I've used VFS-style installations of Puppy Linux on pretty ancient hardware... Snappy and stable compiling software or playing games. Granted Puppy's OS loads entirely into RAM; they're not directly comparable. Still, i get the feeling that something must have broke in this case.

Sorry i can't be of more help, i just had an urge to react to one of the sixty trillion pleading troubleshooting forum posts stuck with vague, irrelevant, or nonexistent answers.

---

### Post by Rebootin on 2012-06-04
> **mastablasta said:**
>  wubi is limited and ment only for testing the OS on ocmputer with minimum changes to the default widnows OS.

@ mastablasta: Where can I find the suggested changes to Windows default? I'm ready to install UB 12.04 with Win 7 on an Hp Pavilion and I intend to run 95% UBUNTU.

I can setup a dual boot without Wubi if I knew how to change the Win 7 default settings.

THX
Rebootin

---

### Post by SinkingRocket on 2012-08-12
well as of what i read about wubi or installing ubuntu on a seperate partition.. the performance is THE SAME!.. the only difference is that in wubi it is easy for the user to uninstall it cuz its in the same partition as windows..aside of installing it on a different partition.. to be honest i had a faster experience when i sided loaded 11.04 32bit on my older laptop.. now am using the 12.04 64bit so could that be the issue? it might be performance drop but atleast its much faster than win7!

---

### Post by hebbal1273 on 2012-08-20
Same problem here. My 10.04 Ubuntu 64 bit was super fast compared to 12.04. Even normal switching between applications & starting takes time forget compilation. My Windows XP on the same laptop is much faster than 12.04!. The only difference being 10.04 was intalled from Wubi from the wubi/sourceforge.net whereas 12.04 was installed from Wubi supplied by Ubuntu. Are there any major differences that might affect the performance? Has the minimum h/w requirement changed? I have a AMD turion 64bit dual core with 1GB RAM. Something has changed for sure.

---

### Post by hebbal1273 on 2012-08-20
To get a feel of how slow 12.04 is, just click on the software centre & wait for it to open. It takes around 35-40 secs to open up!!!

12.04 has a really good UI & it will lose a lot of users if this is not fixed quickly.

---

### Post by phazo on 2012-09-07
So, I had the same issue and here's what fixed it for me.  WUBI laid down Ubuntu on an NTFS partition by default.  Since the NTFS driver isn't all that great, any file transfer, literally any read/write would peg the the CPU. 

Try it yourself. Open up a terminal window, run top, then move a few files around that take long enough to copy that you can watch the CPU peg out.  If the process that's using 99% of the CPU is the NTFS driver, then its the same issue I ran into.

The only thing that fixed it was to kill the partition, boot from USB/CD and install Ubuntu on a fresh EXT4 partition.  Performance was like night and day.  Its a shame that WUBI uses NTFS by default, but I guess for maximum compatibility with Windows.

---

### Post by offgridguy on 2012-09-07
Good explanation.  Thank you
I just wanted to add, I have just installed ubuntu 12.04 alongside windows 7, and it's working fine
it seems just as fast as my old computer where it was the only OS.

---

### Post by Boogiwoogie on 2013-01-28
Hi! I had the same issue. What worked for me was the following:
1. Make a regular ubuntu 10.04.2 installation from within windows.
2. Boot into ubuntu and run synaptic package manager.
3. Search for "ntfs" and lock version of both packets "ntfs-3g" and "libntfs-3g75".
4. Close synaptic, start update manager and do a regular update.
5. Close and restart update manager, check for updates, click on "upgrade to 12.04".
6. Grab a cup of coffee, restart your box when upgrade is complete.
7. Run "sudo top" in terminal and look at "mount.ntfs" while doing some file operations
Things should run smooth.

Some remarks:
to step 1: Note that I used 10.04.2, not the most recent one.
to step 3: You lock a package by selecting it and check Menu->Package->Force version. Maybe locking "ntfs-3g" is enough, because the other one will be deinstalled regardless. Maybe you dont need to lock at all, someone could test that.
to step 4: The "upgrade to 12.04" button shows up while downloading the packages, I think you could cancel the update (for 10.04) and go for 12.04 right away. Someone could test that too ;)

cheers, boogi

---

