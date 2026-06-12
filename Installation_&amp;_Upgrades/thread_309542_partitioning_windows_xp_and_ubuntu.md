---
title: "partitioning windows xp and ubuntu"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by mcs101 on 2006-11-29
I'm a new Ubuntu user who would like to install Ubuntu on a new computer running Windows XP with a 160 GB hard drive and 1 GB RAM.  I have no experience partitioning hard drives.  The Psychocats partitioning guide ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)) suggests creating the following partitions:
- Windows XP (NTFS)
- Ubuntu /home - shared data (Ext3)
- Ubuntu / (Ext3)
- swap

I have a few questions about this:
1) Anybody have any suggestions as to what size I should make each partition?
2) The guide suggests using FS-Drive to allow Windows to access the shared data.  Is this easy to use?
3) Since I only have a vague idea what I'll be doing, what happens if I get stuck in the middle without access to another computer in order to get help?  Can I simply shut down the computer and start again later?

---

### Post by groggyboy on 2006-11-29
1 - that's up to you, and depends on your usage requirements.  there are plenty of posts on these forums where people have posted their suggestions.  i have 10 gigs for windows 9 gigs for linux, 40 gigs for linux home/shared, 1 gig for linux swap.  works fine for me - i have a large music collection.

2 - that driver is great.  just install it, set your shared partition as drive D or E (or whatever is available) and away you go.  i even install and play windows games on my ext3 partition.  install it after Ubuntu has been installed.

3 - its probably not a good idea to shutdown half way through install.  just run the graphical installer off the Ubuntu liveCD.  its really easy and usually error free.  just make backups of your important data.  the installer should set up everything for you.  you can even surf the internet or play solitaire off the liveCD while it's installing.

have fun!

edit: if you want a good graphical liveCD installation guide, use [this]("http://www.psychocats.net/ubuntu/installing").  when it comes to the "prepare disk space" page, choose the third option labelled "manually edit partition table" if you wanna follow one of the suggestions on the page you linked in your post.  the guide i linked has instructions for that as well.  partitioning and installing may seem intimidating, but its not that bad.

---

### Post by goodfella on 2006-11-29
First of all make sure before you attempt to install Ubuntu that you defrag your windows drive that you are going to repartition.

Your /home partition is going to be used for all your personal files as well as settings.  So you need to consider how much space you need for that.  

As far as the / partition I have 10gb reserved.

For the swap partition people usualy recommend 1.5 to 2 times the amount of ram you have in your system.

I have never used FS-Drive so I cannt comment on that.

The installation process is pretty straight forward but I would suggest searching the web for some guidance.  I had never installed Linux before and had no problems installing Ubuntu.  That was before Dapper so I believe the install is even easier now.  

Also make sure to back up your info, so if something goes wrong you can allways re-install windows without loosing anything.

---

### Post by louieb on 2006-11-29
I installed Ubuntu about 6 months ago.

[LIST]
[*]One word about Swap space. The 1.5 to 2 X memory really does not apply to you. With 1 gig of memory unless you are running lot and lot of applications at the same time your will probably never use Swap .5 gig should be plenty.   

[*]I may not use a computer the same as you but here is how the space on the Linux computer I use the most is utilized. 
[*]My / partition is 10 gig and 3.8 gig have been used. I do web development as a hobby and I have a couple of large Development Suites, Apache, MySql, and PHP Install for testing. and that about it over the base install. 
[*]My /home is 18 gig and 2.3 gig has been used. But I mostly store text files I don't have a lot of space eating media files or pictures.
[/LIST]

---

### Post by mcs101 on 2006-11-30
Thanks everyone.
About the suggestion to defragment before I begin - I'm installing Ubuntu on a new computer (<1 week old), with just about no personal files on it yet.  I'm assuming I don't need to defrag, and hope this assumption is correct.

---

### Post by Mangetout on 2006-11-30
> **mcs101 said:**
> Thanks everyone.
About the suggestion to defragment before I begin - I'm installing Ubuntu on a new computer (<1 week old), with just about no personal files on it yet.  I'm assuming I don't need to defrag, and hope this assumption is correct.

It's a good idea anyway; downsizing NTFS partitions can be problematic; the operation is made less (or less likely to be) problematic by prior defragmentation - in theory, the files will all end up being packed down into the start of the NTFS partition and the resize operation will only be lopping off empty space.

Even on a new-ish Windows installation, there may be files all over the partition.  Defrag first to save tears later.

---

### Post by Mangetout on 2006-11-30
You might also want to consider creating a modest-sized FAT32 partition; Last I checked, Linux can read NTFS, but writing is a bit dodgy; a one-gig FAT32 partition would be readable and writable by both Windows and Linux and might prove useful if you need to transfer stuff between one OS and the other without using external media.

---

