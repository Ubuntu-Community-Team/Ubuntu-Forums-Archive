---
title: "Ubuntu server keeps hanging during install!"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by Matchboxx on 2012-09-04
I have been trying this for days. And I am sick and tired of it just not working. I'm about to go back to Windows Server 2003, which runs fine on both of these machines.

I have a server. HP ProLiant DL360 G3. Windows Server 2003 ran fine on it. I decide to jump into Ubuntu server. I put the disc in, boot into it, and it refuses to work. Halfway through the boot process - right after DHCP detection - it just hangs at a purple screen with a white bar along the bottom that I can type in but it does not run commands. Nothing is reported on the BusyBox console when I hit alt-f2. It is completely useless. It gives NO error whatsoever.

Finally I decided maybe it was the hardware. I go out and buy a **new server**. This was not a cheap expenditure. It is a HP ProLiant DL320 G3 and is significantly newer than the previous server (despite the step backwards in model number, don't ask me). Ubuntu is now doing the SAME THING after "loading additional components" - purple screen, white bar I can type in, worthless console that gives no helpful information or error codes.

Both machines are apparently i686 architecture and I am using the 32-bit version of Ubuntu. I have checked the md5sum and confirmed my disc image burned and the ISO downloaded correctly. I have also had Ubuntu run a CDROM integrity test which it passed 100%. There is no good reason for this. What is wrong.

---

### Post by TheFu on 2012-09-04
[http://serverfault.com/questions/179201/installation-of-ubuntu-server-edition-on-hp-proliant-dl360-g3](http://serverfault.com/questions/179201/installation-of-ubuntu-server-edition-on-hp-proliant-dl360-g3) seems to say the RAID controller is the issue. Can you swap that out?

HP has tested this model with these OSes: [http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=3288138&lang=en&cc=us&prodTypeId=15351&prodSeriesId=316558&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=3288138&lang=en&cc=us&prodTypeId=15351&prodSeriesId=316558&taskId=135)  Neither Ubuntu nor Debian were tested.  Before you run back to Windows, I would suggest trying CentOS first.

These systems are old - really old - from RHEL 4.x days.  [http://www.ubuntu.com/certification/make/HP/](http://www.ubuntu.com/certification/make/HP/) says that G5 and later servers from HP have support.  The G{x} value matters more than the DLxxx part.

[http://linuxhcl.com/browse/product?id=6680](http://linuxhcl.com/browse/product?id=6680) says that Ubuntu 8.04 works, but 8.10 doesn't due to a grub error.

---

### Post by Matchboxx on 2012-09-04
Okay, now I have a new problem. At advice of a colleague, whenever the install would hang, they said to hit Ctrl-C. I did this on the new server [the DL320 G3] and it seems to make it through install just fine. Then it installs GRUB to the MBR and now I get a "Cannot Display This Video Mode" from my monitor. This happened on the old server too the one time I managed to get it to choke through the install, I just forgot to mention it before.

I googled this error yesterday and it appears that GRUB tries to run at 1280x1024 60 Hz which somehow these monitors don't support (I've tried 3 different models of Dell LCD monitors, all VGA). That's ridiculous on so many counts. **1.** Why is something stupid like GRUB trying to run at such a high-resolution anyway? I don't need to see my partitions in stunning HD. **2.** My monitors work fine running 1280x1024 as Windows ran at that, AND, as the above poster said, I had CentOS on here at one point too which worked fine (but I want Ubuntu because this is for a Minecraft server).

And most importantly, **3.** Why is this so difficult? You would think when Canonical chucked out Ubuntu *SERVER* edition, they would have gone, hmm, how can we make this compatible with *the most popular rack server line in the United States???*

---

### Post by Matchboxx on 2012-09-05
Bumping this.

---

### Post by Matchboxx on 2012-09-07
Bumping, still no answers to this problem.

---

### Post by drdos2006 on 2012-09-07
Your answer is here.

[http://linuxhcl.com/browse/product?id=6680](http://linuxhcl.com/browse/product?id=6680) says that Ubuntu 8.04 works, but 8.10 doesn't due to a grub error.

I have really old equipment which will not work with newer versions of Ubuntu as well.

Do you have a copy of 8.04 ?

regards

---

### Post by TheFu on 2012-09-07
[http://www.minecraftserverhosting.org/how-to-set-up-minecraft-server-on-centos/](http://www.minecraftserverhosting.org/how-to-set-up-minecraft-server-on-centos/) explains how to setup Minecraft on CentOS.  

If you prefer APT (like I do), then perhaps you can install Debian Server?  Yep [http://www.minecraftserverhosting.org/how-to-set-up-minecraft-server-debian/](http://www.minecraftserverhosting.org/how-to-set-up-minecraft-server-debian/) explains that too.  Debian server and Ubuntu server are similar.

Even if you do get this working under Ubuntu, you won't be able to maintain it. There will always be "issues."  At this point, I can't even recommend installing 8.04 - I'm actively migrating servers off 8.04 because support ends in 6 months.

Linux is not MS-Windows. Those comparisons are not helpful.

These two posts
* [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)
* [https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers) 
will help us.

---

### Post by Matchboxx on 2012-09-10
I do have 8.04 lying around somewhere - difficult to find it online since for some reason Canonical has made the Ubuntu website difficult to find anything other than the "simple, here you go" ISOs (I can see why they do this for the average Joe, but for more technically oriented folk like us, it makes it more difficult). But I don't want to use 8.04 since it is much more outdated and probably less secure.

If what you say is true and Ubuntu is unstable for Minecraft server hosting, I'll try CentOS or Debian. I figured Debian would be the next best thing to Ubuntu - but I'm also more familiar with CentOS/RHEL/using yum so maybe I'll give that a try too.

Thanks for the responses.

---

### Post by TheFu on 2012-09-11
> **Matchboxx said:**
> I do have 8.04 lying around somewhere - difficult to find it online since for some reason Canonical has made the Ubuntu website difficult to find anything other than the "simple, here you go" ISOs (I can see why they do this for the average Joe, but for more technically oriented folk like us, it makes it more difficult). But I don't want to use 8.04 since it is much more outdated and probably less secure.

Thanks for the responses.

8.04 is still under support, so it is not any less secure. That support ends in 2013.

**Technical people** use ISO mirrors, not the site halfway around the world.  The local university here mirrors almost every Linux disto out and keeps old ones around.  They also have a huge pipe, so downloads are 10x faster.  Search for "ubuntu mirror" to find one close to you.  

A single search and this was found [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

Knowing how to search for things on the internet takes time.  Very few people would be looking for a version about to go out of support after 4+ yrs, so Canonical is correct to make newer versions easier to find.

There are reasons for almost everything, if we stop to consider the many different viewpoints.  A few days ago, I thought I'd found a bug ... turns out that I'd done something odd and the fact that it worked really was not intentional. At some point in the future, that bug which allows my configuration to work will probably be closed.  If I don't fix my setup soon, it will be forgotten until it breaks later and I get frustrated.

I believe that you are in the same situation.  Your 2 servers are not new and I really hope you didn't waste too much money on them.  A $200 used Core2Duo desktop would probably have been a better purchase for your Mindcraft needs.  

Servers are not investments, they are more like old, rusted, rotting boats. Old servers have many issues - hard to get parts, slow, lots of heat, inefficient power supplies, disk size limitations are just a few.  For my day job, we help companies replace old servers with more efficient ones and consolidate them  10-to-1 since newer hardware is faster.  They save money in the first year since cooling and electricity are much less. Plus the HDDs are under support and failures don't cost anything.  At one client we swapped out a HUGE APC 20K UPS for a 4K UPS.  Yes, old servers are like old boats that need to be taken out and sunk in deep water.

---

### Post by joker535 on 2012-09-12
FYI - 10.04 LTS works pretty well on the HP G3 machines. I have a half dozen DL360 and DL380s running it with no issues. Make sure you flash the bios with the latest available from HP, set the OS selection to linux,  and dump the raid container and create a new one. 12.04 just doesn't work without screwing with it and you really don't want to have a server platform with a hacked together OS. 10.04 has run great for us and done everything we have asked it to.

---

