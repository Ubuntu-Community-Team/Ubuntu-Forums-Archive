---
title: "Using RAID cards..."
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by focaccio on 2009-12-28
Hello,

I want to build a new Ubuntu server dedicated solely to storing virtual machine backups from a G3 HP DL360 running VMware ESX.

I would like to create one NFS share out of an array of 3 or 4 disks built with hardware RAID 3 or 4.

Has anyone built something like this?  If so what are the materials and methods?

Is there a hardware RAID controller most often used or best supported in Ubuntu?

Has anyone successfully installed a hardware RAID controller (capable of RAID 3 or 4) with Ubuntu 9.10?  If so, can you please share the brand and model plus your installation experiences?

Thanks,
Greg

---

### Post by fro1269 on 2010-01-09
i would like to bump this thread, i have the same exact question

---

### Post by phillw on 2010-01-09
Grub 2 and RAID seem to still have some issues, there is an update for Grub2 that increases raid capabilities, with more work underway.

Whilst I confess to being on little more than nodding terms with RAID (I know what it is & have worked with it in the past) There are a couple of recurring themes.
1) Using hardware RAID - less processing for the CPU

[LIST]
[*]However, that's not really an issue these days, with fast CPU's & dual / quad core beasts)
[*]If the RAID controller dies (and, they do) It can be impossible to read **any** data using a different make / model of RAID card - The card dies - So can your data.
[/LIST]
There was a good discussion on the topic over here --> [http://ubuntu-tutorials.com/2008/06/14/hardware-raid-vs-software-raid-your-opinions/](http://ubuntu-tutorials.com/2008/06/14/hardware-raid-vs-software-raid-your-opinions/)

A lot of guys are using software RAID, and also using Grub Legacy because of issues with Grub2 and RAID

Grub2, or its Sunday name of Grub 1.97beta is the Grub shipped with 9.10 - With 10.04 (the next system due out) they're on 1.97 and may possibly even squeeze in Grub 1.98 - but that is very much a 'would like to' rather than a 'will ship' - Grub 1.97 (current 10.04 one) has had some further work done with it for RAID The Grub 1.97 (for 10.04) *should* be available to Karmic, but I'm not sure how to go about getting it (apart from pointing to a lucid repositry, but then I'm not sure of any dependencies - so, someone else may be better placed to answer it).

>  If /boot is on an MD device and we're using GRUB 2, install GRUB there
      rather than (hd0); GRUB 2 will interpret that as meaning that it needs
      to install to each of the RAID members.
    - Mount /target/sys when running update-grub.
    - If using GRUB 2 and installing to a RAID device any of whose
      components are partitions, then default to installing to the MBRs of
      each of the containing disks, since GRUB 2 will refuse to install to
      the partition devices.
  * GRUB 2 now supports installation on SATA RAID and multipath.


I'm told a lot of work is being carried out, as Grub2 is going to **have** to be happy with RAID for the next LTS  (10.04).

From other threads on the subject, some have simply gone back to Grub Legacy (v0.97) which has a good track record with RAID.

Using Ubuntu 8.04 (now at 8.04.3) has a couple of potential advantages for you, and any RAID users 

[LIST]
[*]It works (I always love that)
[*]8.04.4 is due out end of Feb 2010, in readiness to transfer over to 10.04 (Which also kinda sweet - as they're working to 'make that happen')
[/LIST]
So, two decisions - Do you stick with hardware raid - less stress on cpu, faster response, real easy plug and play with borked hard-drives - but with that problem of a borked raid controller, or, do you go with software raid ?

Hopefully that thread I posted will help, and the information above will also be of help.

I do need to add, however, that my comments on Grub2 and RAID are to the best of my knowledge - I do keep as 'up to speed' as I can on the matter, as coming from a server environment I appreciate just how important it is to a small but significant and important user base.

Regards,

Phill.

---

### Post by fro1269 on 2010-01-10
Thank you for your response..

I was looking around different vendor websites and found the

Highpoint Technology RocketRAID 4460 card does have supported drivers for Ubuntu 6.10 thru 9.04 here is a link to their guide

[http://www.support-highpoint-tech.com/Main/RR3xxx_4xxx/Linux/Install_Ubuntu_RR3xxx_4xxx.pdf](http://www.support-highpoint-tech.com/Main/RR3xxx_4xxx/Linux/Install_Ubuntu_RR3xxx_4xxx.pdf)

They also support a few other distros, you can find the info here
[http://www.highpoint-tech.com/usa/bios_rr4460.htm](http://www.highpoint-tech.com/usa/bios_rr4460.htm)

I have not deployed a server with this card yet, as I am only in the early planning stages ; however, this might be a good starting point for people who have the same question. When I reach the point where I actually deploy the sever I will update the thread with my results. :P

---

### Post by phillw on 2010-01-10
> **fro1269 said:**
> 

Highpoint Technology RocketRAID 4460 card does have supported drivers for Ubuntu 6.10 thru 9.04

9.04 was the last release on Grub Legacy - So it looks like sticking to grub legacy, for the time being at least, seems the less painful way forward.

There are a few discussions of the use of 9.10 & RAID, but most I've come across seem to use grub-legacy.

So, choose a version of ubuntu you like. 8.04 will update to 10.04, 9.04 will possibly not, if you're running raid, as you'd have to go 9.04 --> 9.10 --> 10.04.

At the last check, karmic was going to be staying with Grub1.97beta and not moved up.

Phill.

---

### Post by focaccio on 2010-01-19
Nice responses, phillw and fro1269, thanks! 

This is definitely not a one size fits all area. I will wait for LTS 10.04, then experiment with RAID 5 using the least expensive HighPoint RocketRAID controller I find that supports it (currently the 2300 series for about 118$ at newegg). I'll end up buying two controllers and test to make sure they are interchangeable before I put the storage server into production.

---

