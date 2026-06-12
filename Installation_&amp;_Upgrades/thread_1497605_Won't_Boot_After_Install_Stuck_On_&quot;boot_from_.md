---
title: "Won't Boot After Install Stuck On: &quot;boot from CD&quot;"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by JoeGoalie on 2010-05-30
Let me preface this by saying I've dabbled with Ubuntu several times in the past but it never really suited replacing my Windows until now.  I installed Ubuntu 10.04 on my Toughbook the other day and fell in love with it.  I then decided to try and put it on my desktop to replace Windows 7.  So, I'm not new to installing Ubuntu but, I am new to trying to set it up the way I wanted.  Now for the problem...

My Windows is setup across 4 HDD's like this:
32GB SSD is my boot drive and where Windows is installed
2x250GB drives in RAID0 is where I install all my programs, and my paging file
1TB is where I keep all my pictures/videos/etc...

Would I be correct in thinking that a similar Ubuntu install would be:
32GB SSD as /
2x250GB RAID0 as /usr and a section for swap
1TB as /home

I downloaded the alternate install CD for 10.04 and partitioned the drives like this:

sda 1TB ext4 /home
sdb 32GB SSD ext4 /
sdc1 1.5GB swap
sdc2 248.5GB physical space for RAID
sdd1 1.5GB swap
sdd2 248.5GB physical space for RAID

Then I went into "configure software RAID" and setup md0 as RAID0 and go back to the partition screen.  At the partition screen I then set md0 as ext4 /usr.

Then I continue with the install and everything goes smooth, no problems at all.  When the PC goes to reboot everything is fine until it gets past the BIOS screens and tries to boot from HDD.  I set it up to boot first from hard drive and then CD.  Well, you can hear it spin the drives and then nothing...  Then it tries to boot from CD and all it leaves me with is:
"press any key to boot from CD/DVD"

Earlier when I used a live CD and installed the SSD as / and the 1TB as swap and /home it worked just fine.  I've tried two different "alternate" install CD's one a 32bit and the other 64bit and all I get is the boot from CD text. What is going on?

---

### Post by JoeGoalie on 2010-05-31
Anything guys? I'm going to try and unplug all my drives except for one and see if that does anything.  Is it possible that my SSD is messing it up? I'm really confused as to why this isn't installing properly.

---

### Post by JoeGoalie on 2010-05-31
So, I disconnected all but one of my hard drives and set it up like that with my alternate install CD. I set up a /boot partition, /,/home, and swap. The install worked perfect and booted up no problem. I'm wondering now, did I set up to many "physical" partitions? Would that cause Ubuntu not to load? I'm going to try again later using mostly logical partitions and see how that goes.

---

