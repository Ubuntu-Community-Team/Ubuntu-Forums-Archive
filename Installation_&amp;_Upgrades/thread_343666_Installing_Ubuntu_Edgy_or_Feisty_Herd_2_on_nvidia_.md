---
title: "Installing Ubuntu Edgy or Feisty Herd 2 on nvidia raid 1"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by J4Life on 2007-01-21
Hello Everyone,

This is my first post and I am some what new with Linux. I am slowing making the transition after running MS OS's for 10 years or more. I have a back ground in IT so I am no newbie in the computer environment but I am still wet behind the ears with Ubuntu.

What I was hoping to find out is if there is a straight forward easy approach to dual booting using a nvidia raid 1 configuration. I know that this isn't a true hardware raid but it still provides the benefits of data redundancy. Also this is something that is very easy to do with with Windows and I think that it should be something that can or should be easily done with Ubuntu. So I am asking for any assistance that anyone is willing to offer.

I must say thought besides this minor issue I am very much impressed with Ubuntu overall. I have found it quite easy to learn and the best part is that it is free and loaded with some really nice applications. Also OpenOffice 2.1 is great as well.

Thanks in advance,
Bill:p

---

### Post by jpeddicord on 2007-01-21
I really don't know much about a hardware raid, but I feel obligated to post this little tidbit of info anyway:

Do **not** use Feisty. Yet. It is far from ready, and will give you more trouble than it is worth.
Use Edgy, or even Dapper if you want supported upgrades.

Sorry, I had a need to say that. :biggrin:

---

### Post by unperson on 2007-01-22
Hi Bill,

I just got a new mobo myself with an nVidia nForce 410 chipset with RAID capability.  I haven't gotten my RAID going yet, but I thought I'd share a little of what I've learned looking around on the web.  Take it all with a grain of salt, of course.

Like you said, nVidia RAIDs are apparently not true hardware RAIDs but rather a mix of hardware and software functionality that seems to widely be known as a "fake RAID" (or fakeRAID).   From what I gather, if you had a real hardware RAID controller, it'd be completely transparent to the OS, but in these much of the RAID functionality is implemented in software, so you need a special driver with the functionality built-in.  On nVidia's site, they refer to the linux kernel module sata_nv.  It isn't 100% clear to me whether this is simply for the SATA controller or whether it includes the RAID functionality.  Ubuntu Edgy Eft (6.10) already has this driver and it did not seem to allow RAID functionality for me.  It may simply require a newer version, which you can get from [nVidia's site](http://www.nvidia.com/object/linux_nforce_1.21.html).  Unfortunately, the zip file contains modules only for Redhat/Fedora and SUSE, but I think you can use the source to compile it for your system using steps [like these](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346).

In any case, it looks like the module dm_mod can allow RAID functionality with such controllers.  E.g. I ran Knoppix 5.1 (a live CD with a system similar to Ubuntu) on my system and the RAID seemed to show up.  I didn't actually try to setup the disk, though, so that's  the most I can tell you there.

You may also find the following helpful to look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

For myself, I decided not to use the "fake RAID" and just to go with a straight up software RAID.  From what I read, the straight software RAID has performance that's as good or better, and things I read suggested that the fake RAID would only be readable to that controller, so if you stuck the drives in another computer you wouldn't be able to read them.  The upshot is that the fake RAID works consistently between Windows and Linux, which is a must if you're dual booting, but it's irrelevent for me.  However, now I'm having trouble getting Ubuntu installed with the software RAID, so maybe I didn't make the right choice.

In any case, good luck and welcome to Ubuntu!

---

### Post by J4Life on 2007-01-22
Thanks Guys. I appreciate the replies. Ok I will stick with the Edgy Eft 6.10 version and see what solution I can come up with. I will make certain that once I have this worked out I will share it with the community. One of the things in the past that has detered me a little from Linux was some of the complexity. I like keeping things simple and straight forward. Of course I enjoy new challenges as well. That is what keeps IT folks sharp.

I have read through the FakeRaidHowTo and felt for some reason that it didn't apply to Edgy Eft 6.10 as much as it did to Dapper so I backed off. I will continue to do more research and see what I come up with. 

Thanks,
Bill

---

