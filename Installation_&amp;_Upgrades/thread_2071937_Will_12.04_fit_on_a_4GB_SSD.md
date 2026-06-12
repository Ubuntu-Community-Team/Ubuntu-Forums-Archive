---
title: "Will 12.04 fit on a 4GB SSD?"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by bofak on 2012-10-16
Are there any figures available for the amount of space required for a clean install of 12.04?

A few years ago I was fool enough to try and save a few $$ by buying a netbook with a hard drive of only 4GB.  I've been running 10.04 on it satisfactorily, but the $$ I saved had to be spent on a slot card to give me space for my files.

Now I'd like to go for 12.04 but I'm wondering about space.  If it won't fit, will I be given a warning right at the start that there is insufficient space or will I find out the hard way?  I don't want to risk messing up an OS that is working just fine, though a little out of date.

---

### Post by cybrsaylr on 2012-10-16
No. IMHO you need more room for 12.04.

I just installed 64 bit 12.04 on a SSD. After updates and installing several of my fav programs/apps, 5.0GB of space has been used.

---

### Post by jerrrys on 2012-10-16
Not recommend

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

May want to look at [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), it can use Ubuntu software.

---

### Post by bofak on 2012-10-16
Yes -- it seems the recommended minimum drive-size is now 5 GB.

Would it be feasible to run Ubuntu from a USB stick or slot-card?  These little netbooks don't have CD/DVD drives.  Would there be complications?  I'm getting a bit out of my depth here, technically.  Could anyone steer me toward documentation on doing that sort of thing?

Thanks, guys, for the help so far.

---

### Post by oldfred on 2012-10-16
Full Ubuntu will not fit. Lubuntu may also fit.

Lubuntu one stop thread - amjjawad
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Now older
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

You can also install the minimal which is just kernel & a driver to get onto the Internet to download only those apps you want.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by wojox on 2012-10-16
> **bofak said:**
> 
A few years ago I was fool enough to try and save a few $$ by buying a netbook with a hard drive of only 4GB.  I've been running 10.04 on it satisfactorily, but the $$ I saved had to be spent on a slot card to give me space for my files.

I have an Asus 900 eeepc that I mount root on the 4 GB internal and then home on a 4 GB slot card. Runs fine. 
I did upgrade the memory from 512 MB to 2 GB. I let my daughter test 12.10 on it.

---

### Post by bofak on 2012-10-16
> **wojox said:**
> I have an Asus 900 eeepc that I mount root on the 4 GB internal and then home on a 4 GB slot card. Runs fine.

Well that's basically what I've been doing.  But would it work the other way round?

---

### Post by jerrrys on 2012-10-16
I haven't got around to it yet, but I also have 4gig to work with and going to give puppy a go.

[ATTACH]225644[/ATTACH]

---

### Post by wojox on 2012-10-16
> **bofak said:**
> Well that's basically what I've been doing.  But would it work the other way round?

Sure, follow that third link from oldfred. You have to fake out Ubiquity at first. :P

---

### Post by bofak on 2012-10-17
> **wojox said:**
> Sure, follow that third link from oldfred. You have to fake out Ubiquity at first. :P

I think this may be the way to go.  Thx.

Please just explain one last thing:  I've no idea what you mean by fake out Ubiquity at first.

---

### Post by wojox on 2012-10-17
> **bofak said:**
> I've no idea what you mean by fake out Ubiquity at first.

[Ubiquity should have a command line option to override the free space check]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124")
It won't let you install on under 4GB of space. Last time I had to edit casper/filesystem.size

---

