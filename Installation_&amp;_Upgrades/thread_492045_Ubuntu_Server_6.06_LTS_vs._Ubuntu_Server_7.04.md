---
title: "Ubuntu Server 6.06 LTS vs. Ubuntu Server 7.04"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by evolving_monkey on 2007-07-04
Hello all,

I have been impressed dual booting with Ubuntu on my main computer. Now i think I would like to replace Windows Server 2000 on my server. I am not sure which of the versions I should use (Ubuntu Server 6.06 LTS or Ubuntu Server 7.04). I realize that the LTS version means long term support. I need something stable and i am not sure of the benefits of using one instead of the other.  

The network would then include an Ubuntu Linux Server and at least 2 Windows XP systems via ethernet (to run work related software with no Linux equivalent). Eventually we might add Macintosh work stations.  All connect through a router with ethernet and wireless capability. On occasion wireless laptops running Windows XP will also connect.  It's a  small office network. (if this isn't enough information about our setup please let me know.

I am curious what the community thinks. Any opinions or suggestions are welcome.

Thank you for your time.

---

### Post by az on 2007-07-04
On a production system, use LTS.  If you just want to play around, use whatever version.  If you need cutting-edge versions of an application, you may want to use 7.04.

The upgrade path to the next LTS will be easier if you use Dapper now.  You will be able to upgrade form Dapper to the next LTS, but to go from 7.04 to the next LTS, you will have to upgrade to each release in between.

---

### Post by evolving_monkey on 2007-07-04
My main goal is stability and dependability as this will be the main data storage for our office. It will be continually written to because the work programs we use auto save changes every 2 minutes.

I will probably dual boot with Windows Server 2000 until I am sure it is completely safe to dump the Windows install.

So far it sounds like the LTS version is my best choice. I would still like to hear about the experiences of those that has used or uses Linux on their servers or from anyone who cares to respond. 

Thank you az.

---

### Post by evolving_monkey on 2007-07-04
I forgot to mention that the server has two 500gig hard drives in a mirror r.a.i.d.  array which is where data is stored. The OS is and will be on a 40gig ata hard drive. Also, the mainboard has 2 on-board nics. One is Nvidia and one is 3com. Not sure if that would make a difference.

---

### Post by evolving_monkey on 2007-07-05
I have question I didn't consider. All of the partitions on the server are ntfs and the largest being around 400gigs. Is that something Ubuntu can serve. I have been playing around with Ubuntu on my main system and I haven't had any problems sharing but I haven't tried it with an ntfs partition that large.

Any input is appreciated.

Thanks

---

### Post by Soybean on 2007-07-05
For a server, I always recommend LTS unless you come across some specific feature you need/want in 7.04. Usually, you want to get your server working and then more or less leave it alone for as long as possible, and that's what LTS is all about. :)

You mentioned some specific hardware there... I assume you're concerned it won't be supported? It sounds easy enough, but just in case, I'd try to find a definite make and model number for all of those things (the RAID controller and the 2 network cards) just in case you need it later. Often, these things "just work," but it's good to be prepared. :) Those are the parts I'd be thinking about too, BTW.

As for NTFS, Ubuntu can handle it, but it's not ideal. You'll need to install ntfs-3g if you want to be able to write to the NTFS partitions... and the reason it's not installed by default is that the Ubuntu devs don't trust it enough. I haven't heard of anyone actually having a problem with it, but if you're the "better safe than sorry" type, you might not want it on an important server. The preferred solution is to migrate to a different filesystem, though of course that may be easier said than done with half a terabyte of data.

---

### Post by Wim Sturkenboom on 2007-07-05
For an office environment, don't consider anything but LTS. Or do you want to upgrade every 18 month because it's no longer supported.

With regards to disk size, I did just read somewhere that ext3 supports up to 16TB (think it was on the RedHat site).

And I suggest that you use a native file system and not ntfs. You should have backups anyway, so you can copy them back (OK, will take a while).

---

### Post by evolving_monkey on 2007-07-05
My current work stations now run XP. If I change the file system on the server won't it just cause a problem with the work stations. I realize that there is software to read Linux partitions from Windows. But doing that just seems like I'm shuffling the problem around. Is adding software to windows really a preferable option?

I would like to migrate all of the systems to Ubuntu but that isn't currently practical because crucial work software doesn't  have a Linux option (unfortunately not even a Mac option). I have considered running Windows     through VMware inside Linux but I'm not sure If that is the best option (just starting to look into it and I know very little at this point). Luckily this isn't something that needs to happen immediately so I have time to figure it all out.  Would running windows in a virtual machine make Windows able to work with the ext3 without the need install anything special in Windows?

---

### Post by az on 2007-07-05
> **evolving_monkey said:**
> My current work stations now run XP. If I change the file system on the server won't it just cause a problem with the work stations. I realize that there is software to read Linux partitions from Windows. But doing that just seems like I'm shuffling the problem around. Is adding software to windows really a preferable option?

Over Samba or whatever network sharing protocol, you are filesystem-agnostic.  The local kernel reads the file from the disk, not the remote client.

---

### Post by evolving_monkey on 2007-07-05
Az, let me make sure I understand (I'm still noobish). It doesn't matter what the the file system is on the server because the data is coming from the server. Windows would only have a problem if it were a local ext3  drive (on the work station).

Did I get it or did I completely miss your point?

---

### Post by az on 2007-07-05
> **evolving_monkey said:**
> Az, let me make sure I understand (I'm still noobish). It doesn't matter what the the file system is on the server because the data is coming from the server. Windows would only have a problem if it were a local ext3  drive (on the work station).

Did I get it or did I completely miss your point?

Bingo!

---

### Post by evolving_monkey on 2007-07-05
That just made things much easier. Also, several things now make sense that didn't before. 
Thank you very much. 

Thank all of you very much.

---

### Post by evolving_monkey on 2007-07-05
Just though of another question. I was thinking about installing the LTS and dual boot with windows 2000 server. I want to set up a smaller partition with ext3 and get used to using Ubuntu as a server and learn  more before I completely dump Windows. Also I want to make sure that this is what I'm looking for. Based on my experience with using it as a desk top I doubt I'll be disappointed. I just want to make sure. 

.Is that "dangerous" or is it a rational idea?

---

### Post by trentend on 2007-07-05
> **evolving_monkey said:**
> Just though of another question. I was thinking about installing the LTS and dual boot with windows 2000 server. I want to set up a smaller partition with ext3 and get used to using Ubuntu as a server and learn  more before I completely dump Windows. Also I want to make sure that this is what I'm looking for. Based on my experience with using it as a desk top I doubt I'll be disappointed. I just want to make sure. 

.Is that "dangerous" or is it a rational idea?

Personally I would always test on a separate machine, and then configure how you want the server, and *then leave it alone* (except for adding users and security upgrades and the suchlike - or general maintenance).   I would never test on a production server.

I've toyed with an Ubuntu server myself, but always ended up going back to centos.  Simply because the software I require is better supported on that platform.  You might want to think what it is you want to do, then which software you want to use, then try a few server platforms on your test machine, and then when you're really happy with your choices and configuration implement it on a server, and aim to keep it stable.  If ubuntu works for you, then the LTS version is definitely the one to aim for.

It's tempting to think that you want the latest greatest software to maximise your hardware performance, but in most cases stability and ease of maintenance is more important on a server.  Consequently  I am currently still using 32-bit server operating systems even on 64 bit hardware.  This choice is not in the least defined by availability of key services and their 64bit stability.

Think conservatively, rather than extravagantly.

---

### Post by az on 2007-07-05
> **evolving_monkey said:**
> 
.Is that "dangerous" or is it a rational idea?

I would install it on a cheap, headless box to play with it.  All you really need is a pentium with 128 megs of ram and a few gigs of hard drive space.  Unless the windows server box you currently have is a test box....

---

### Post by Wim Sturkenboom on 2007-07-07
If you are going to dual boot your production machine, it's a bad idea as your production machine will be down while in 'linux mode'.

See if you can't find an old machine that's no longer in use. Else buy an 'el cheapo' box.

In my company, I collect all 'old' boxes that are 'obsolete'. The collection ranges from PII's 233MHZ with 64MB mem and 6GB HD to early P4's. I usually install Slackware on them and use them as servers for development purposes.

---

