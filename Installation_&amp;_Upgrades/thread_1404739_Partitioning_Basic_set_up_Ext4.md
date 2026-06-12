---
title: "Partitioning Basic set up? Ext4?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by bambii7 on 2010-02-11
Hi all, I'm extremely new to this whole Linux thing. I've spent a few days downloading various versions, and making multiple CD's. Today the CD drive decided it was dirty and wouldn't read my first successful CD LOL, tried the manual approach, failed. Tried Unetboot which worked like a charm.
After that brief personal history it brings me to permanently installing Ubuntu over Vista. But am again hellishly stuck, the partitions this time. I tried the basic set up from the wiki
**Name**
   **Size**
    swap
   size of RAM
    /
   at least 3GB, at most 15 GB
    /boot
   at least 100 MB, at most 250 MB
    /home
   the rest of the disk

Which translated to

swap 1000mb
/       10000mb ext4
/boot 250mb ext4
/home 108800mb ext4

But while installing (formatting) I get
"the ext4 file system creation in partition #5 of SCSI1 (0,0,0) (sda) failed."
Along with some other messages prior to that, about device being busy and rebooting.

I'm really new, have never touched Linux before, or partitioned anything. Is ext4 the correct format to use on SCSI? I tried fat32 but it only gave me Windows options....

---

### Post by Sef on 2010-02-11
> swap
   size of RAM
    /
   at least 3GB, at most 15 GB
    /boot
   at least 100 MB, at most 250 MB
    /home
   the rest of the disk

Which translated to

swap 1000mb
/       10000mb ext4
/boot 250mb ext4
/home 108800mb ext4

The root parition should be 8 -10 GB.

Swap should be the size of RAM, if you are going to use hibernation or suspend.  Otherwise, 1 gb is enough.

A boot partition is not needed.  Is there some reason you need a separate partition?  

The rest for the home partition.


> But while installing (formatting) I get
"the ext4 file system creation in partition #5 of SCSI1 (0,0,0) (sda)  failed."
Along with some other messages prior to that, about device being busy  and rebooting.

I'm really new, have never touched Linux before, or partitioned  anything. Is ext4 the correct format to use on SCSI? I tried fat32 but  it only gave me Windows options....
[SIZE=2]

Ext4 should work just fine.   Are you sure that you have a good hard drive?  What were the messages that you got?

Manually partitioning the first time or two can be a bit tricky, but after that it is easy.

[/SIZE]                   		  		  		  		  		  	
  	
[]("http://ubuntuforums.org/editpost.php?do=editpost&p=8812380")

---

### Post by bambii7 on 2010-02-11
Thanks for a quick response Sef!
Tired again without boot (I read it was handy for upgrading/installing multiple versions).
I tried upping the memory limit, thought it was worth a go.

/ 15027MB 15GB
swap 5000MB 5GB (1 GB RAM on this laptop)
/home 100002MB

Same errors. I'll write them out as the come up, something about not being able to write to dev/sda

1: Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy. This means Linux won't know about any changes you made to dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

2: same as above but referring to dev/sda5

3: same again but dev/sda6

4: The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sdas) failed.

After that I get taken back to Prepare disk space stage of installation. I'm afraid to reboot because I'm guessing vista has been wiped and Ubuntu hasn't been installed LOL

In advanced options install boot loader is checked, and /dev/sda is selected. sda 1 and 6 are also available as options. Not sure if that's relevant but now you know :)

Got to go work in a bar, will check back in about 8 hours.

---

### Post by bambii7 on 2010-02-12
A little forum bump, and by chance is there a way to check whats running? I keep getting dev/sda in busy or in use..... I've got no idea. I've been really tempted just to restart and see what happens, although... I think I'll end up without an OS

---

### Post by random_excess23 on 2010-02-13
I had a very similar issue installing Karmic on my laptop. Had XP on it and it completely died on me. So figured I'd try out the new(ish) Ubuntu distro on it.

Tried a couple of times to set up the partitioning manually but it just wasn't having it so, being a little impatient, I opted for the automatic partitioning. It worked fine and I've been using it with no problems for the past few days. The swap came out at about a Gig which was what I would have specified anyway.

It's not ideal though, I wanted a separate /home to make upgrading easier.

I am enjoying Karmic though and intend to upgrade my main system to it, it's running hardy at the moment so I intend to do a fresh install and I will NEED separate partitions on this machine. 

I'll let you know if I have any success next time round.

---

### Post by bambii7 on 2010-02-13
Woot go Ubuntu!
Thanks for the reply random_excess23. I now posting from my first Ubuntu/Linux installation.
The solution dawned on me yesterday, it was a very noobish thing. My CD drive was bust and I didn't have a flash drive, so after reading about alternate ways to install I opted for Unetbootin from Windows hard disk.

That worked well, but silly thing I was doing was "Full Install" and I couldn't partition because "dev/sda" (what ever that is) was in use with the Ubuntu installer. Went out and brought a dirt cheap USB stick, again used Unetbootin to make a installable flash drive. Took about 5min, installed no worries. Well I learnt a lot over the past few days with all the reading.

---

