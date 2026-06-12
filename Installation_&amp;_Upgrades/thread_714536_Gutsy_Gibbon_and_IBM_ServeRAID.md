---
title: "Gutsy Gibbon and IBM ServeRAID?"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by jonjonz on 2008-03-03
I have a pair of IBM series 345 available to use as web servers for our library website. We would like to   install Gutsy Gibbon based LAMP environments. One potential problem is that the disk drives are not plain hard disks, but drives with IBM ServeRAID 6m Controllers.  Our previous limited experience has been with installing Ubuntu and other Linux distros on basic hard disks, so RAID is new territory and it is unclear if Ubuntu and the RAID disks will work together.  The IBM support site for the raid drivers offer install CDs for SUSE and Red Hat Linux, albeit several years older versions.  

In searching here for ServeRAID and Ubuntu, I came across a number of unanswered queries as to this feasibility, and some threads outlining potential problems and a few giving steps on how to install dual boot setups with this raid.  Since we do not want dual boot, only Linux, I worry those guides may not be helpful to our situation.

I am going to spend the next day or so going over those guides, and may just go ahead and run the Ubuntu install and hope for the best, but I would appreciate any additional information or help.  

Shoulld Gutsy recognize and be able to deal directly with the drives (partitioning etc) or will we have to depend on trying to use the IBM SUSE or Red Hat RAID install for that?

---

### Post by jonjonz on 2008-03-05
FYI -- I tried loading the Gutsy Gibbon Live CD on this configuration, and not only would it NOT recognize the drives, but it locked up the server.  

After that I decided to bite the bullet and try and make do with one of the 2 distributions that the ServeRaid install CD says it will work with, (Red Hat or SUSE Linux).  I settled on Cent-OS (a Red Hat dirivative).

The Cent-OS installer loaded up right away and immediately recognized the drives and then installed without a hitch.

I still would like to hear from anyone who may have been successful in getting Ubuntu to run on an IBM xseries 345 with the LSI ServeRAID 6m.  

We have been using Ubuntu on another server with non-raid drives for a while and  really wanted to stick with it for all of our systems, but it looks like one needs to be an advanced linux guru to work out getting Ubuntu to work with this specialized arcane IBM raid.

---

### Post by waveform on 2008-03-06
If you're using a 64-bit environment, [post]4464944[/post] might prove useful - it's dealing with a ServeRAID 8k instead of 6m, but I suspect many of the steps will be the same / similar (IIRC, both these are just re-badged Adaptec cards and software). I'm going to try and find some time to make sense of my notes and add some full instructions to that thread later tonight.

---

### Post by techno-wiz on 2008-03-06
I'm also wanting to know how to do this as I'm wanting to set up an Ubuntu server on a xSeries 235 server.

---

### Post by waveform on 2008-03-07
I was too knackered to put together the instructions last night unfortunately, but I managed to finish them off this morning. See the [post=4464944]aforementioned post[/post]. I've also included a set of 32-bit instructions just in case (couldn't remember if the x235 was a 32-bit box ... I ought to as I'm sure we used to have a couple in our server room! Oh well, the little grey cells are not what they used to be ...)


Cheers,

Dave.

---

### Post by jonjonz on 2008-03-15
Thanks Waveform!

I have been so busy trying to set up a LAMP using Centos 4.3 on these servers, I have not checked back here.  The Serveraid disks that came with our servers were set up to accept Centos 4.3 so it has been a bit of a grind to find and install current LAMP components and get them working on top of it. 

I read over your instructions, and will really need some more time to absorb them.  If we can interpret them confidently, we may try them out as we would really do want to be on Ubuntu.

-jonjonz

---

### Post by waveform on 2008-03-15
If the instructions need any clarification on particular points, do let me know and I'll find some time to expand them. They're definitely a bit spartan at the moment!

Are you working with 32-bit or 64-bit servers? If 32-bit there's nothing to worry about - there's very few tweaks and the ones there are (postrm/postinst) are simple. 64-bit is more tricky where one needs to go digging through alien's guts to make it convert the RPM, and so on. However, if you're dealing with multiple servers at least either procedure (32 or 64-bit) is easily re-useable - i.e. at the end of the procedure you should have a .deb package you can simply copy and install on any (same arch.) server. So, it's a pain, but it's a one-off pain :-)

---

