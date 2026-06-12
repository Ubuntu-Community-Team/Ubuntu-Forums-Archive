---
title: "Partition advice"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by bossa on 2008-01-23
Hi all

I have a 250 gig sata hard drive that I want to partition for maybe two or three distros with Ubuntu being the main. What would be the best formula taking into account future upgrades etc.
I have been dual booting different flavours of linux on separate hard drives for some time but would really like to put at least two on this one drive. I have windows on it at the moment ...but I never use it these days . 
Thanks Steve

PS I have 2gis of ram..I'm a bit confused on the correct amount of hard drive space to allocate for root,swap, home etc for two distros. Also I would like to be able to upgrade in the future and leave all my data etc intact

---

### Post by cotcot on 2008-01-23
I keep 40 GB free per testing distro (1 root + 30 home) and i have a second version of my default distro installed. I try out an upgrade on the second version of my default before doing the default.
I have 2 satas installed. The second version and default are on different drives. Data are on both drives as backup. So in case of a hdd failure I always have a distro and my data on the other drive as backup.

---

### Post by bossa on 2008-01-24
Thanks cotcot.
So if I was to split the hard drive into three ,how much would I have to allocate for swap ,how much for root and home .What would be right to accomadate three Distros. Maybe  or should I allocate the correct amount of space using half the drive and keep half as ext 3 for futher distro/data...is trhat right? sorry I'm very new to this . All the guides I have seen usually refer to  dual booting with windows .Idont want to do that.

---

### Post by housam on 2008-01-24
I suggest to have the following : 
- 3 x 20 GB  for three distros of ubuntu
- 2 GB for swap 
- the rest for data partition ( prefer fat 32 ) to accomodate dealing with distros other than Gutsy.

---

### Post by bossa on 2008-01-24
Thanks housam

Would I label the three 20GB partitions /home? and what about / (root). Does there need to be order that this is done ?,when looking at Ubuntu that I have installed with Gparted 
it looks like / boot then swap and then /home.

---

### Post by imT on 2008-01-24
do a google search for swap. don't worry with 2 gig ram you don't need swap, swap is for low ram machines.
about partitioning... 10 gig for root "/"  ;  10 gig for windows probably  ; and the rest for " /home"
you don't need to install several distro's with 2 gig of ram...use virtualbox or vmware; is just more simple...

---

### Post by housam on 2008-01-24
> **imT said:**
> do a google search for swap. don't worry with 2 gig ram you don't need swap, swap is for low ram machines.
about partitioning... 10 gig for root "/"  ;  10 gig for windows probably  ; and the rest for " /home"
you don't need to install several distro's with 2 gig of ram...use virtualbox or vmware; is just more simple...

Wrong ( no offend ). swap is not for the low RAM machines. it is needed for the complete ubuntu installation. if you open the system monitoring tool during multi proccess operations, you'll see that the swap is used even the RAM is only half of it capacity is used. Read [[COLOR="Red"]this discussion[/COLOR]]("http://ubuntuforums.org/showthread.php?t=360554").

---

### Post by imT on 2008-01-24
i'm not offended, and also i'm not sure that i'm right, never the less i put myself the same question as the topic starter a few weeks ago and i serached with google and all i find was saying thai ram is not necessary with a updated pc like the one bossa said he has.
i have no ideea how true is this but i found on several sources so i assumeed it must be right.

---

### Post by housam on 2008-01-24
> **imT said:**
> i'm not offended, and also i'm not sure that i'm right, never the less i put myself the same question as the topic starter a few weeks ago and i serached with google and all i find was saying thai ram is not necessary with a updated pc like the one bossa said he has.
i have no ideea how true is this but i found on several sources so i assumeed it must be right.

If you read the link in my last post , you 'll find that many users had noticed the usage of the swap partition. I did noticed that my self many times.

---

### Post by bossa on 2008-01-24
Thanks for your input guys. My machine is AMD64 3700 2GB 3200ddr 250gb Sata Hard drive. Getting back to labeling and order of partition whats the best thing to do and in what order?

---

