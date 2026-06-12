---
title: "question about having 2 hard drives"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-06-27
I was wondering how things work when you have 2 hard drives on a machine. I've never had that before so I wonder how the o/s install goes then. Does the installer automatically recognize the other drive? Does it format both of them on it's own or you have to go in an manually put ext3 or ext4 on the other one? So what? You just plug the thing in to the ide cable and power supply and that's it?

I've never done this before and I'm not sure what to expect. I don't plan on installing a straight Linux distro (well not in the standard sense anyway). I'm gonna install Xen and I think it's domain 0 has to have some o/s installed for you to run it's management tools. Not sure which Linux I'll use for that but it will be a Linux.

Can anyone tell me how something like this goes? What I can expect or need to do?

Thanks in advance for any help.

---

### Post by trizrK on 2011-06-27
> **ClientAlive said:**
> I was wondering how things work when you have 2 hard drives on a machine. I've never had that before so I wonder how the o/s install goes then. Does the installer automatically recognize the other drive? Does it format both of them on it's own or you have to go in an manually put ext3 or ext4 on the other one? So what? You just plug the thing in to the ide cable and power supply and that's it?

I've never done this before and I'm not sure what to expect. I don't plan on installing a straight Linux distro (well not in the standard sense anyway). I'm gonna install Xen and I think it's domain 0 has to have some o/s installed for you to run it's management tools. Not sure which Linux I'll use for that but it will be a Linux.

Can anyone tell me how something like this goes? What I can expect or need to do?

Thanks in advance for any help.
1. Yes it automatically detect it.
2.They don't merge meaning everything on the two drives are seperated. 
3. You can still open and edit files on the secondary drive through your main drive.

---

### Post by trizrK on 2011-06-27
> **trizrK said:**
> 1. Yes it automatically detect it.
2.They don't merge meaning everything on the two drives are seperated. 
3. You can still open and edit files on the secondary drive through your main drive.
And you must put the ext. manually. It doesn't do this automatically.

---

### Post by ClientAlive on 2011-06-27
> **trizrK said:**
> 1. Yes it automatically detect it.
2.They don't merge meaning everything on the two drives are seperated. 
3. You can still open and edit files on the secondary drive through your main drive.

On (2) - Except if you do RAID right? Never done that before either and prob won't. Just that I'd heard of it before.


> **trizrK said:**
> And you must put the ext. manually. It doesn't do this automatically.

So you mean I'll have to run gparted manually or something for the other drive?

---

### Post by trizrK on 2011-06-27
> **ClientAlive said:**
> 


So you mean I'll have to run gparted manually or something for the other drive?
Oh no sorry i didn't mean that. Everything can be configured through just one gparted window.

---

### Post by ClientAlive on 2011-06-27
> **trizrK said:**
> Oh no sorry i didn't mean that. Everything can be configured through just one gparted window.


Ok man. Thanks. Guess I'll see more when I do it.

Have a good night brother.

---

### Post by oldfred on 2011-06-27
I have three drives and a full install in a flash drive, so does that make 4?

When I first installed and had two drives, I thought I wanted XP on one drive and Ubuntu on the same drive with lots of copying to the other drive for backups. Some how I made a mistake and it installed Ubuntu to my second drive. Best thing ever. I now recommend an install on every drive. You do have to partition how you want. If installing multiple installs you may want smaller root partitions and more data partitions. I then added a third larger drive and have several Ubuntu installs - my older, my current, testing and planning on kubuntu in another.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by ClientAlive on 2011-06-28
> **oldfred said:**
> I have three drives and a full install in a flash drive, so does that make 4?

When I first installed and had two drives, I thought I wanted XP on one drive and Ubuntu on the same drive with lots of copying to the other drive for backups. Some how I made a mistake and it installed Ubuntu to my second drive. Best thing ever. I now recommend an install on every drive. You do have to partition how you want. If installing multiple installs you may want smaller root partitions and more data partitions. I then added a third larger drive and have several Ubuntu installs - my older, my current, testing and planning on kubuntu in another.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.


Wow. That's really cool oldfred. Thanks. Installing and running Xen Cloud Platform is something I don't want to jump into without reading up on it a little. Thanks for the links. I do have some exper with gparted and gparted live and have done installs where there is only one disk lots before. I just wasn't sure how things would play out when there is more than one disk. These operating systems (and Xen too I'm sure) are pretty smart though - I'm sure I don't have much to worry about.

---

### Post by PCLinuxGuy on 2011-06-28
what about a small capacity drive for the distro/os and a bigger hdd for the /home, or would that work

---

### Post by ClientAlive on 2011-06-28
> **PCLinuxGuy said:**
> what about a small capacity drive for the distro/os and a bigger hdd for the /home, or would that work


Well this isn't a normal situation/ install. I wish I had a better resource to offer to explain this. Xen is virutualization software and FOSS. Xen has a few products that are no cost and one of them is a cloud platform. Well, if you get on you tube and start checking out tutorials you quickly see that people who use Xen for this usually have more than one server in the system and each server performs a different role within the system. For instance, one might just be a ticket server (for security and validating login), another might be an app server, and yet another might be storage for the user.

Well this applies to me too (even though I'm not some huge corporation with plans to sell cloud service to thousands) since I do intend to use this cloud service, not only for a personal reasons but also to offer to my company which will ultimately have quite a few people who need to use an online calendar and contacts system. Maybe I'll put the co's web site on there too. I don't know. So this idea of breaking up services seems applicable to what I'm trying to do to - even though mine is smaller scale. Since I don't own multiple servers I thought I could break it down using multiple hard drives. After all, they are physically separated from one another.

Here's a like to check out Xen and what it is: [www.xen.org](www.xen.org)

Here's a link to a you tube vid: [http://youtu.be/T011jzNRp-A](http://youtu.be/T011jzNRp-A)

Well that vid is not the best for what I was talking about but if you look for tutorial where they're showing you how to config different things you'll see what I mean (web clients, security tickets, etc, etc).

---

