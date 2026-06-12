---
title: "Safely Trying To Go From Dual Booting 9.10/Windows 7 To 11.04/Windows 7"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Nocturnes on 2011-06-23
Hey everyone, first time posting, and I come to you seeking advice.

Bit of back-story, I built the current computer I'm using, and my first installed OS (64-bit) was Ubuntu 9.10, as I didn't have any other OS at the time. I knew I might eventually, so during the install I split my hard drive into two partitions.

A short time after, I got Windows 7, and installed it on my 2nd partition so as to dual boot the two. For 1-2 years now I've mainly booted Windows 7 for everyday work. And by now, as you well know, 9.10 has hit EOL.

What I want to do at this point is format my Ubuntu partition(s), merge them with my Windows 7 partition, then restart, interrupt start up to boot from a CD containing Ubuntu 11.04, install it, and split the resulting partition (of the earlier merge) between Windows 7 and Ubuntu 11.04.

Now come my questions... First of all, have I got the basic idea of how to properly do this down (I don't think of myself as an expert on this sort of thing)? I've heard horror stories of being locked out of Windows 7, or even losing Windows 7 data, after attempting something like this, so my aim is to do this safely, without error. Second, if I don't, what have I missed?

Third, the reason I said "Ubuntu partition(s)" earlier is because when viewing my partitions in Windows 7, I see two nameless partitions sized at 39.04 GB and 1.72 GB respectively, along with my 192.02 GB C: drive (W7) partition and my 100 MB System Reserved (W7) partition; I assumed the two nameless ones were Ubuntu and GRUB or something along those lines, since all are listed as healthy, primary partitions... Am I correct?

Any and all advice is appreciated, especially if you read everything!

---

### Post by dino99 on 2011-06-23
hi,

first: run w7 and cleanup/defrag the system, then resize the w7 partition(s) if needed. 

second: follow this howto: [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Nocturnes on 2011-06-23
So, you're telling me I can't/shouldn't just boot from CD, install Ubuntu and partition my drive during the installation process?

---

### Post by oldfred on 2011-06-23
Have you backed up all data including the hidden files in /home if you have customized your install? Since some can make errors in installing it is also a good idea to have a full backup of important data from windows also.

I do not understand your desire to merge & then split the partitions. You can just use manual install and choose to install to the sda1 or 39GB / (root) partition. You specify format and it will totally overwrite it with the new install. It will find the current swap and reuse it.

Dino99's suggestion is to format in advance and include a separate /home. I also suggest a separate /home as then when you do a total reinstall it saves all your data & user settings that are in /home. My normal suggestion is 10-20GB for /, 2GB (or size of RAM if planning to hibernate) for swap and the rest of whatever space you want for Ubuntu as /home.

Screens have changes slightly from older versions but process is the same:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Nocturnes on 2011-06-23
I desired to format and then merge the Linux partitions so as to not only wipe my old Ubuntu data (anything important was backed up already), but to also allow my Windows partition to have more space than before. As it stands, I barely use 40 GB in Ubuntu, whereas my Windows 7 partition is already using more than 100 GB.

Regardless, what I was doing (and did) was a lot simpler than my OCD made it out to be.

1. Backed up EVERYTHING. Just in case.
2. Set BIOS to boot from CD.
3. Logged into Windows 7, opened the partition manager, "Right Click > Delete" on both the 39.04 GB and 1.72 GB Linux partitions.
4. The resulting Free Space needed to be "Right Click > Delete" 'ed one more time, so as to turn it into Unallocated Space.
5. "Right Click > Extend" on the C: partition, so as to merge the Unallocated Space into it.
6. Just to be safe, ran cleanup and defrag on the new, larger Windows 7 partition.
7. Inserted Ubuntu 11.04 CD into CD drive, and rebooted the PC.
8. The PC booted from the CD into Ubuntu 11.04's "Try" mode, listing 2 items on the desktop, 1 of which was Install.
9. Ran the installation, selected Run Ubuntu Alongside Windows 7, and adjusted the partition slider as desired.
10. Completed the installation, rebooted, no problems whatsoever.

---

### Post by dFlyer on 2011-06-23
Regardless of what you do, backup both windows and your linux home directory. If you can clone your windows all the betters. It seems anytime you mess with a partition without a backup something goes wrong, call it Murphy Law.

---

