---
title: "Blank screen on boot - GRUB problems with RAID"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by agirman on 2011-03-19
So I am trying to install Ubuntu Server 10.10 on a computer with 5x 1.5 TB HDDs.  I went through the process of partitioning the five hard drives into three partitions each:

sd*0 is a 300MB partition for /boot, RAID1, 2 active, 3 spare
sd*1 is a 500MB partition for swap, RAID1, 2 active, 3 spare
sd*2 is a 1.5TB partition for /, RAID5+LVM, 5 active, 0 spare.

md0 is the raid1 on sd*0
md1 is the raid1 on sd*1
md2 is the raid2 on sd*2

During the install, everything seemed to work fine with the formatter, but the installation ended in error.  I booted into rescue mode and found that though all the drives were U (in /proc/mdstat), it was resyncing.  I let this run (overnight) and the next day, jumped back in and installed the OS successfully.  However, after installing GRUB, when the installation process asked me to reboot, the system came back up with a blank screen (blank, save for a blinking cursor) and didn't move from there.

I am thinking that the problem is GRUB, since I can boot into the main LVM partition via the rescue option on the install cd.  Here's what bugs me:

```

# df
Filesystem         1K-blocks     Used  Available   Use%  Mounted on
/dev/mapper/main--array-prime 5765507792 850712 5471786120 1% /
/dev/md0                      5765507792 850712 5471786120 1% /boot
tmpfs                           1899520    276   1899244   1% /dev
/dev/csd0                     5765507792 850712 5471786120 1% /media/cdrom

```

If you look at df, it looks like /boot is mounted on /dev/md0 (which is correct), but the used/available/etc. statistics obviously look like it's actually the LVM that I'm looking at.  It >looks< like the RAID is properly configured, is this an artifact of booting into /dev/mapper/main--array-prime from the CD?

here's /proc/mdstat:

```

# cat /proc/mdstat
Personalities : [raid0] [raid1] [raid6] [raid5] [raid4]
md2 : active raid5 sdb6[0] sda6[4] sde6[3] sdd6[2] sdc6[1]
      5857423104 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]

md1 : active raid1 sde5[0] sdb5[4](S) sdc5[3](S) sdd5[2](S) sda5[1]
      487360 blocks [2/2] [UU]

md0 : active raid1 sdb1[0] sdd1[2](S) sde1[e](S) sda1[4](S) sdc1[1]
      291776 blocks [2/2] [UU]

```

So, like I said, the problem is that when the system powers on, there's a blank screen with a flashing cursor on it.  Can anyone see what I've done wrong?  ls /boot returns nothing.

---

### Post by Hakunka-Matata on 2011-03-19
plagiarized, but we're in Open source land, right? 

I hope this link will help you. See the section named 'First Boot after installation is over'.

[http://ubuntu4beginners.blogspot.com...n-problem.html]("http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html")

---

### Post by Hedgehog1 on 2011-03-20
> **agirman said:**
> 

[B]sd*0 is a 300MB partition for /boot, RAID1, 2 active, 3 spare
sd*1 is a 500MB partition for swap, RAID1, 2 active, 3 spare
sd*2 is a 1.5TB partition for /, RAID5+LVM, 5 active, 0 spare.[/B]

...

So, like I said, the problem is that when the system powers on, there's a blank screen with a flashing cursor on it.  Can anyone see what I've done wrong?  ls /boot returns nothing.

agirman,

I think I see the issue here.  It's a brain teaser - but here goes:

You know that you can only boot from software RAID 1 (based of your sd*0 layout I am assuming you know this):

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/150px-RAID_1.svg.png[/IMG]

See how disk 0 is completely readable without software raid in the above picture?  The data on disk 0 is lined up the way the boot expects to find it.

Here is the thing: while sd*0 is RAID 1, the booting OS needs to figure out where '/boot' is.

The data to find this out is on '/'; but that is a RAID 5 software raid. The raid software is not loaded yet when booting (the disk data is still sliced up as far as the computer knows):

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/6/64/RAID_5.svg/300px-RAID_5.svg.png[/IMG]

Look at disk 0 - the data is scrambled (until raid software is loaded later) and the boot process dies on what it thinks is a messed up disk 0.

To fix this, you need both '/' and '/boot' on RAID 1. Something like:

[I]sd*0 is a 10gig partition for '/' & /boot, RAID1, 2 active, 3 spare
sd*1 is a 500MB partition for swap, RAID1, 2 active, 3 spare
sd*2 is a 1.5TB partition for /home, RAID5+LVM, 5 active, 0 spare.[/I]

***The 'Hardware Raid is Cheaper in the Long Run' Hedge***

:KS

---

### Post by agirman on 2011-03-20
Thanks for the responses, Hakunka, Hedgehog.

I don't think the link provided addresses my problem, as it is almost certainly not a graphics issue (and I am not running desktop).

Hedgehog, many thanks for the lucid explanation of what's going on.  That all seems to make sense, though I was under the impression that it was possible to mount / on a RAID5.  My scheme was actually based on a chapter in the book "The Official Ubuntu Server Book, 2e", where in the RAID chapter, he goes an example:

"RAID con&#64257;guration is done during the partitioning section of the install process. Once you see the main partition screen, select “Manual partitioning.” In my example I set up RAID on a three-disk machine. I have a threepartition RAID 1 array for /boot, a three-partition RAID 5 array for /, and a three-partition RAID 5 array for swap." (p.338)

Perhaps I did complicate things by setting up LVM on the RAID5, but I think my scheme is very similar to his, and he seems to indicate that this can be done.  What am I missing?  Is LVM the difference-maker?

I am not opposed to the scheme you present, especially if it works out-of-the-box; however, I don't really like the idea of that huge chunk of space being cloistered in /home.  Would it be possible to install ubuntu on a small upper partition, and have it log me into another ubuntu with its / on the larger partition?

---

### Post by Hedgehog1 on 2011-03-20
The '/home' is not the required mount point for the larger array.  It is just the most common for Ubuntu desktops.

You are doing a server install, so the mount point can certainly be something else.

I have never seen the "The Official Ubuntu Server Book"; so I cannot comment if I am in error (it happens, ask my wife), the book is in error *or* your understanding of the book is the issue.

The LVM (**L**arge **V**olumn **M**anagement for newer thread readers) partition setup; is the final 'virtual' partition LVM (the parititon you called '/' and I called '/home') the LVM, or are the individual partitions that make up the RAID all little LVMs?

You can quickly see why I prefer hardware raid.  But this is a learning exercise for us both.  *Remind me to thank you sometime...*

I just can't get my head around software raid 5 '/' working, no matter if it is LVM or not.  But in the interest of the empirical test, you can try a none-LVM RAID 5 of '/' and see if the book is in fact correct (that happens sometimes, too!).

***The Hedge***

:KS

---

### Post by agirman on 2011-03-20
I will do that and report back.  Hopefully I won't have to resync.  I do appreciate your help.  However, I'm out for the day and probably won't get to it until this evening.  I'll keep you posted.

---

### Post by Hedgehog1 on 2011-03-20
Here is a link about software raid: [setting-up-software-raid-in-ubuntu-server]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

It was last updated in 2009, and I don't know if things have changed since then, but it does say that: *Linux will only boot when the &#8220;/boot&#8221; and &#8220;/&#8221; partitions are on RAID1. It cannot boot when those partitions are on RAID5. Other partitions, however, can be RAID5*

However, ronparent indicates that ***fake*** raid O can be boot from: [Read 3rd post]("http://ubuntuforums.org/showthread.php?p=10581500#post10581500") and based on what I have just read he is quite correct (raid software is loaded early enough with fake raid).

It appears that fake raid will do RAID 5, too.  So that is a (more complex) option for you, too.

Way too many choices here...  My little ***Hedgie Brain*** is slowly frying...


***The Hedge***

:KS

*Hedgehogs prefer hardware raid...  More money, less work...  Hot swappable...  Like this: [Sans Digital TowerRAID 5-Bay]("http://www.amazon.com/gp/product/B003YDZE0Q/ref=s9_simh_gw_p23_d0_i1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1JWGGFFF6NQVKVCCRXF3&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846")*

---

### Post by agirman on 2011-03-22
So, I just wanted to say that it might be the LVM or raid.  I went back into setup and was going to change my partitioning setup as discussed, by deleting the LVM.  Well, having started the process, it's moving at a rate of roughly 3% every 8 hours, meaning I can expect it to run for 10 days or so O_o.

---

### Post by Hedgehog1 on 2011-03-23
**[SIZE="3"]OUCH!!!!!!![/SIZE]**

I guess we will talk again in about a week?!?!  Two Weeks?!??!

***The Hedge***

:KS

---

### Post by jonnyboysmithy on 2011-03-23
Now what if u had a power cut? hehe:D

---

### Post by agirman on 2011-03-23
I can't help but think that this may be related to my previous problem, because call me crazy, but I don't think it should take this long under normal conditions :-P.  It does make me wonder if it's the lvm, the raid, or the drives themselves.  Well, nothing to do now but charge forward.

---

