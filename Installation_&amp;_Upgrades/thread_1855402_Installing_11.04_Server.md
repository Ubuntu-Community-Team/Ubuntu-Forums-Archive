---
title: "Installing 11.04 Server"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Jimbo23 on 2011-10-06
Hi,

Seems an odd way to do my first post as an already sovled problem, but I saw some many threads that seems to be sort of heading towards this same problem, but not 100% the same. It's taken me about a weeks worth of work to figure it out, but I finally have!

Everytime I tried to install Ubuntu Server 11.04 64-bit, it would get to a certain point and then fail to install grub. Now the initial server I was installing it to was an old(ish) machine with a Pentium D 3.0GHz CPU and 4Gb RAM, but with an IBM SAS controller (based on an Adaptec AIC-9405) and a pair of SAS drives. All the hardware had been used in the past for various different tasks before it reached me, so I didn't know what was on the drives, nor did I care.

The very first install I tried was using the hardware RAID, but I couldn't get that to see any drives at all. Next was to try software RAID, that too seemed to give me problems (it was so long ago now, that I can't remember exactly what), but I finally plumped for just doing a straight, guided partitioner install on the first of the two installed disks and it worked fine.

Everything would have been ok, had I not a) completely messed up the compile and install of some software on it to the point where I couldn't sort it out and b) more importantly realised that I'd used 146Gb drives when I meant to use the 300Gb drives that were on my shelf.

So, I whipped the disks out, put a pair of 300Gb drives in and attempted to do a software RAID based install. Followed the instuctions in the server guide to the letter, but got the error that GRUB couldn't be installed.

I popped one 300Gb drive out, attempted a straight install on a single drive, same GRUB install error.

Went back to a single 146Gb that was working and did a fresh install over the top and got the same problem again. Very odd, as this drive had worked fine.

I tried using SATA drives in single and software RAID combinations connected to either the SAS or the onbaord SATA controller, no luck. I tried using a completely different machine, still no luck. Always the same error.

I tried installing Ubuntu Desktop 11.04 and also Ubuntu Server 10.04 and both of them installed 100% fine. As soon as I tried to install Server 11.04 afterwards, it failed.

I tried all the guides for installing GRUB after the server install was complete, but they all failed too.

I finally stumbled upon the fix, so here goes.

Boot a LiveCD of Ubuntu Desktop 11.04 (probably any version will do)
Launch GParted
Go Device>Create Partition Table
Click Advanced and choose GPT > OK
Apply Changes
Create a New Partition on the drive of about 100Mb (I think it can be much smaller in reality, but this is what I used), don't set a format > OK > Apply Changes
Right click the new partition and choose Manage Flags and then set the grub_bios flag
Apply Changes

If you are going to setup software RAID, do the above for both/all the disks.

Now, restart the machine and boot the install CD. Manually configure your partitions and make sure that you don't remove that little 100Mb partition at the beginning and bang, it all works!

It would appear to me (and I'm happy to be told otherwise) that the server install doesn't always correctly create the MBR.

I'm posting this in the hope that it will save someone the DAYS of anger that my colleagues had to suffer as I shouted in the corner of my office and because I saw so many people post problems like mine but with no solution.

Thanks,

James.

---

