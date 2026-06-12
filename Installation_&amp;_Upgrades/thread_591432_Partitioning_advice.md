---
title: "Partitioning advice"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Excalibre on 2007-10-25
So I'm planning to install Ubuntu (alongside XP Home) as soon as my new computer arrives. I'm wondering how best to partition it. It's got a 250gb and 500gb hard drive, which is probably more space than I'll ever use but hell, they're cheap nowadays.

Anyway I'm wondering what the best strategy is for partitioning. My plan is to split the 250 gig down the middle and use half for each OS (with a few gig reserved for the Ubuntu swap partition) and keep all my personal stuff on the big hard drive. I want that available in both Ubuntu and Windows (I understand Gutsy can read and write NTFS, so that's what I'll use.) Would I want to just turn the whole 500 gigs into my /home partition, or would it be better to make a small EXT3 home partition (and then probably mount the big NTFS partition somewhere under my main account's home directory)?

Or something else? There's lots of sort of contradictory advice out there about partitioning . . . Thanks in advance.

---

### Post by logos34 on 2007-10-25
I'd go with 

/  (~10 GB) 
/swap (~1 GB, more than adequate for average user)
/home (remaining space on 250gb drive)

*you should leave some space on 500gb drive for backups

mount windows read+write with **ntfs-3**g/ntfs-config in **/media** directory (standard place)

get **fs-driver** so windows can access ext2/3

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)

---

### Post by Excalibre on 2007-10-25
Is there some reason I'm not clear on why I'd want a /home partition that big, then? Because most of my files will be stored on the larger, second hard drive so that Windows can see them too.

---

### Post by logos34 on 2007-10-25
> **Excalibre said:**
> Is there some reason I'm not clear on why I'd want a /home partition that big, then? Because most of my files will be stored on the larger, second hard drive so that Windows can see them too.

make /home as big or small as you want...You might consider creating one big **extended** partition out of the linux half of the 250gb drive and put /, /swap and /home (of whatever size) inside as logical partitions...This will allow you maximum flexibility to divide up the leftover space. 
> 
keep all my personal stuff on the big hard drive. I want that available in both Ubuntu and Windows (I understand Gutsy can read and write NTFS, so that's what I'll use.) Would I want to just turn the whole 500 gigs into my /home partition, or would it be better to make a small EXT3 home partition (and then probably mount the big NTFS partition somewhere under my main account's home directory)?

If you're thinking of formatting the entire 500gb drive as NTFS and making it /home, I wouldn't advise that.  Make a smaller ext3 /home on the 250gb drive and keep the NTFS 500gb partition(s) separate. 
 
Man, that's a lot of disk space to figure out what to do with!  If only I had half that...

---

### Post by Excalibre on 2007-10-25
> **logos34 said:**
> make /home as big or small as you want...You might consider creating one big **extended** partition out of the linux half of the 250gb drive and put /, /swap and /home (of whatever size) inside as logical partitions...This will allow you maximum flexibility to divide up the leftover space. 


If you're thinking of formatting the entire 500gb drive as NTFS and making it /home, I wouldn't advise that.  Make a smaller ext3 /home on the 250gb drive and keep the NTFS 500gb partition(s) separate.
Okay, thanks. It seemed like the easiest way to keep all my non-system files together, but yeah, I felt a slight twinge of unease about keeping an integral part of my linux install on an NTFS partition where it's vulnerable to whatever Windows does. So I'll do what you said. Thanks!
 

> Man, that's a lot of disk space to figure out what to do with!  If only I had half that...
Yeah, I've completely outgrown the 120 gigs on my current system. I have no idea what to do with this much space. You know, you can get a 400 or 500 gig hard drive for like a hundred bucks nowadays . . .

---

