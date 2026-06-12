---
title: "[SOLVED] configure RAID when installing Ubuntu Desktop?"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by ARhere on 2007-11-13
I am trying to use Ubuntu 7.10 Desktop as my file server with a RAID mirror for my /home and other important data.

I have read the HOWTO: for setting up fake raid, but I do not have a fakeRAID controller card, I just simply want a software mirror on two spare 80G drives during the install process.

I booted the Live CD, and when installing there was no option in the manual partition setup to select a volume as a RAID array, apparently this is only available in Ubuntu Server install?

Ok, so I installed mdadm on my Live session using synaptic and set up a RAID mirror by typing...
```
# sudo -s
# mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/hdb /dev/hdc
```

This successfully created a device that I can see in gparted labled md0 and it is the size I expected.  Unfortunately, when I start the install process again, the installer still only see's hda, hdb, and hdc.

I am getting frustrated and am wondering if it would just be easier to create the RAID mirror after the install and manually moving "/home" to the mirror drive.  I am not confident this will work as "/home" is important to the OS and may not like me moving its physical location.  My other thought is to just install Ubuntu Server, but I want the GUI and I am nervious that installing gnome and all of the great packages that comes with Desktop is more involved then simply typing "apt-get install gnome"  ;-)

Inputs please?!
-ARhere

---

### Post by sporto on 2007-11-13
> **ARhere said:**
> I am trying to use Ubuntu 7.10 Desktop as my file server with a RAID mirror for my /home and other important data.

I have read the HOWTO: for setting up fake raid, but I do not have a fakeRAID controller card, I just simply want a software mirror on two spare 80G drives during the install process.

I booted the Live CD, and when installing there was no option in the manual partition setup to select a volume as a RAID array, apparently this is only available in Ubuntu Server install?

Ok, so I installed mdadm on my Live session using synaptic and set up a RAID mirror by typing...
```
# sudo -s
# mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/hdb /dev/hdc
```

This successfully created a device that I can see in gparted labled md0 and it is the size I expected.  Unfortunately, when I start the install process again, the installer still only see's hda, hdb, and hdc.

I am getting frustrated and am wondering if it would just be easier to create the RAID mirror after the install and manually moving "/home" to the mirror drive.  I am not confident this will work as "/home" is important to the OS and may not like me moving its physical location.  My other thought is to just install Ubuntu Server, but I want the GUI and I am nervious that installing gnome and all of the great packages that comes with Desktop is more involved then simply typing "apt-get install gnome"  ;-)

Inputs please?!
-ARhere

use the alternate installer instead of the livecd, the partitioner on the alternate cd allows you to create a raid drive.

:KS

---

### Post by ARhere on 2007-11-13
>smacks forehead< :(

Why is it I can spend hours working on a problem when the answer is right in my face.  Thank you, I will try that tonight.

I would like my last question answered if possible.  If I install Ubuntu server, how much more work is involved in getting a GUI then just simply typing "apt-get install gnome"?  I am imagining to get Gnome working like Ubuntu Desktop, to automatically load with the log-in screen, with X configured, will be a bit of work.:confused:

-AR

---

### Post by rkillcrazy on 2007-11-13
Peep this out: [http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2")

You can download the flash file or you can view the flash file in a browser.  It goes through with the 7.10 alternate disk.  It'll give you a basic rundown of RAID and I think the guy uses a MIRROR (RAID-1) so that'll also be helpful.

I just set up a RAID-0 in a VM and it worked fine.  I had to add a separate partition for the /boot partition in order for grub to install and work correctly.  However, your plan of mirroring the the home directory probably won't require anything like that if you just install the system on the root of one of the disks.

11-13-07
1040 EST

---

### Post by ARhere on 2007-11-13
Holy crap, that is awesome!

It is blowing me away how much support and resources are available for this OS.  Debugging this OS compared to every Win version I have been using has been..almost...pleasant!

-ARhere

---

### Post by rkillcrazy on 2007-11-13
> **ARhere said:**
> Holy crap, that is awesome!

It is blowing me away how much support and resources are available for this OS.  Debugging this OS compared to every Win version I have been using has been..almost...pleasant!

-ARhere

Yeah, now and then you may have a query that nobody can answer or answer easily.  I had one recently that nobody but myself would answer.  I figured it all out and reported what I found.  It was like having a conversation with myself!  :lolflag:

On average, your support here will be pretty good.  Most people here are rather understanding since they were in your shoes at one time or another.  The open source community is full of people like this.

11-13-07
1637

---

### Post by ARhere on 2007-11-13
Ok..WTF is going on??

I booted my PC using the alternate install disk for 7.10 and got to the disk partition section.  When I watch the video, "Use physical volume for RAID" is an option in the "Use as:"

When I do this on my PC, I only see an option that says, "physical volume for encryption" but no RAID option is seen.  I am going to go mad on this one!

-AR

EDIT:  Ok, here is some more information.  I have three disks, one 120GB on Primary Master, 82GB Primary Slave, 80GB Secondary Master, and a DVD for Secondary Slave.  For some reason, I can select "configure as RAID" for the Primary MAster, but it is not avalible for Primary Slave or Secondary Master no matter what I do.  Why can I not configure either 80GB drive for software Raid?  The only thing that is different is the 120GB drive I am asked if a partition is primary or logical.  With both 80GB drive neither is an option.  The column that normaly specifies "Primary or Logical" is just simply missing.

Any ideas?

-Andrew

---

### Post by ARhere on 2007-11-14
[SIZE="7"]SOLVED[/SIZE]

**The Problem**  When I started the LiveCD originally, I tried to form the RAID manually in the LIVE session using GParted, which was acting really buggy, but appeared to create new partitions.  For whatever reason, the drives were marked inactive by GParted and were therefore no longer able to accept primary or logical drive assignments.

**The Solution**  I booted the hard drives in Windows and using the disk management program, I marked the drives active and removed the current partition.  When I booted with the Alternate Install CD again, I was able to mark the drives as primary or logical and use them as a RAID array.

So the question is, why was the drives marked inactive by the use of GParted?

-AR

---

### Post by rkillcrazy on 2007-11-14
> **ARhere said:**
> [SIZE="7"]SOLVED[/SIZE]

**The Problem**  When I started the LiveCD originally, I tried to form the RAID manually in the LIVE session using GParted, which was acting really buggy, but appeared to create new partitions.  For whatever reason, the drives were marked inactive by GParted and were therefore no longer able to accept primary or logical drive assignments.

**The Solution**  I booted the hard drives in Windows and using the disk management program, I marked the drives active and removed the current partition.  When I booted with the Alternate Install CD again, I was able to mark the drives as primary or logical and use them as a RAID array.

So the question is, why was the drives marked inactive by the use of GParted?

-AR

When trying to set up a RAID array, it's always recommended to use the ALTERNATE install disk.  I'm told and have seen cases where using the LIVE install disk and GParted to set it up was buggy as hell.  In fact many people will tell you to do it from the command line **even when using the LIVE install disk**!

Without seeing all you were looking at it's hard to tell what issue(s) you were having with the ALTERNATE install disk.  You were using 3 different HDDs and that could've been screwing with your setup.  If you set up your partitions exactly the same on all disks being used in the array and you still had an issue, then it could've been something else.  However, it's hard to say what going by your post.

I too got mine working last night! :guitar:

11-14-07
0834 EST

---

