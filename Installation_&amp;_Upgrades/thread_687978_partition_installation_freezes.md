---
title: "partition installation freezes"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by bigman6665 on 2008-02-04
hey guys, i am having a rough time with this computer.  I have decided that i was going to try ubuntu linuz on one of my systems.  But heres the issue.  I have downloaded ubuntu 7.10 with infrarecorder, i can get the live cd to boot fine.  When i go to install on my machine it gets so far and freezes at 5% during  
Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0) (sda)...

Here is another link to someone who had the same issue,, i tried everything he tried,, memoerytest was fine. Any suggestions on how i can get this running on that computer?
Any and all help / responses will be greatly appreciated.

---

### Post by Michl on 2008-02-05
Are you sure it froze?  Sometimes it just takes hours and
seems frozen, but isn't.  This has happened to me several
times.    In my case it would hang for a long time at 15%
but still complete the install.  It just takes a long time formatting.

But install does freeze sometime, too.

---

### Post by hums07 on 2008-02-05
What is your computer specification?

---

### Post by bigman6665 on 2008-02-05
hey there,, i hadjust run an application with ultimate boot cd, diagnostic harddrive fitness test and it came back that there were probably bad sectors.    
I had actually got my other laptop running ubuntu lastnight    i think i just may have to go purchace a new harddrive for this one. The one that is giving me grief is an IBM R51 thinkpad 1.65 GHZ 1.68 RAM   40 GB HD 4200 RPM.   
Do you suggest a new hard drive??

---

### Post by bigman6665 on 2008-02-05
trying to run wipedisk utilities and write errors just keep occuring..

---

### Post by hums07 on 2008-02-06
> **bigman6665 said:**
> trying to run wipedisk utilities and write errors just keep occuring..
You can try to manually format the harddisk (or the partition) you wish to use. Use GParted to do the formatting.
If this is successful, try running "fsck" onto the partition to ensure the file system is healthy.
Otherwise, I suggest you get a new harddrive.

---

### Post by thatoldchestnut on 2008-02-06
I've also had a problem with my system freezing when trying to create the partition. I have a 70gb hard drive (with 35gb free), and I want to give 30gb of that to ubuntu, but when I press 'apply' and it gets to the part where it says 'real resize', the system freezes completely after about ten seconds.

does anyone have any clue on what I might be able to do to rectify this? thanks in advance...

---

### Post by bigman6665 on 2008-02-08
thanks for the help,, i have decided to just go and purchase a new 80 gb harddrive for the laptop.  Its just to frustrating and fsck did not work,,  gparted did not even recognize a drive.

---

### Post by NIT006.5 on 2008-02-08
> **Michl said:**
> Are you sure it froze?  Sometimes it just takes hours and
seems frozen, but isn't.  This has happened to me several
times.    In my case it would hang for a long time at 15%
but still complete the install.  It just takes a long time formatting.

But install does freeze sometime, too.

FYI, I've also had that "freeze" on 15% on numerous machines when using automatic partitioning. In some cases it continued after an hour or so, in other cases it was definitely completely frozen. However, creating partitions manually (instead of going with default) solved this freeze in all cases so far. Not sure what causes it in the first place though. Although come to think of it, there was one machine that kept freezing, but strangely enough went through fine after I doubled its ram - which makes absolutely no sense to me at all, since at that stage of the install it claimed it was partitioning the hard drive.

---

### Post by stanleytberry on 2008-03-10
I have a freeze at 33%.  No apparent activity at all.

My HD is a Maxtor also on a virtual SCSII channel.  The "Check the CD" was successfuk.  A low level format of the HD was successful with no errors reported.

My install is ubuntu-7.10-server-i386.iso.  The burn to a CD had no hitches (like I said above, the CD check was OK).  It boots OK.  It goes through all the preliminary data gathering.  I selected the option to use the entire disk and to initialize LVM.  it stops with 
[CENTER]----| Partitions Formatting |----
  red          |  33%        blue
Creating ext3 file system for / in partition #1 of LVM VG ubuntuServer, LV root ...[/CENTER]

I know little about Linux (that's why I'm trying a pre-configured system).  The only other Linux installation I am running is ipCop ... it's been humming for months.

How can I get past this, please?  In detail, please.

Thanks,
Stan

---

### Post by stanleytberry on 2008-03-11
OK.  I've tried every way I could think of and this Ubuntu install cannot get past formatting the selected partition.  I've gotten not even a single comment from this forum.
---------------------
Hey Stan!
--------------------
What?
--------------------
Why don't you try a different Linux install and see what happens.
------------------------
OK.  How about a Debian 31r2-13 network install I just happen to have laying around from the last time I tried to build a Linux based web server?  It's pretty old but I should at least be able to tell if it can format the drive, huh?
------- a few hours later
Guess what?  The old Debian install had no trouble formatting the hard drive.  So what should I do with this Ubuntu 7.10 Server install?

Anbody out there in Ubuntu forum land got any ideas?
:confused:

---

### Post by stanleytberry on 2008-03-11
Well Stan ... I think you should probably shred it.
------------------------------
That's a good idea.  Want to know why?
------------------------------
Of course.
------------------------------
Still hoping, I downloaded the 6.06.2 Server ISO and installed it.
------------------------------
How'd it go?
------------------------------
Not a single problem.  Formatted that hard drive and installed everything, near as I can tell.  So I don't ever want to try and use that 7.10 CD again.

Thanks for all the help.

---

### Post by OutCell on 2008-04-11
I didn't see this post earlier. I have the exact problem but with different pc specs

i posted a thread here: [http://ubuntuforums.org/showthread.php?t=751313](http://ubuntuforums.org/showthread.php?t=751313)

Thanks Stanley, i will give Debian Etch a try and see what happens!

EDIT: I had the same problem/freeze when i tried to install Debian :( I just bought a new HDD and installed Ubuntu 8.04

---

