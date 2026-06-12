---
title: "Dual Boot Win XP &amp; Karmic"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by jimmyUT on 2010-01-17
So I like ubuntu and want to start using it more, but because of a work website that I need to access (developed for IE and only IE or Firefox running IETAB has full functionality) , I still need to use XP.  

Is it better to install Ubuntu on a partition or install within Windows and use Windows loader?? I see the two choices when using the Ubuntu CD I made.

I already have XP Pro SP3 installed on my thinkpad T60 with dual core CPU and 3G RAM


What are the advantages or disadvantages?

Thanks for your help in advance.

---

### Post by ivan.p on 2010-01-17
Definitely in its own partition. That way, in case you ever want to get rid of Windows or need to reinstall it, it will simply be easier. Also, this gives you a fallback option: if Windows fails completely, if it gets infected with a virus, you can easily reboot your computer and start Ubuntu.

If you finally get used to Ubuntu and rebooting is just too annoying, may I suggest that you try installing a Windows **inside** Ubuntu using VirtualBox? I use this all the time, and it works great. Just install VirtualBox in Ubuntu (from the Ubuntu Software Center), then create a new Virtual Machine, and install Windows in it.

---

### Post by oldfred on 2010-01-17
I think most of us here would recommend installing in a separte partition.  Wubi is installed in the NTFS partition and is a better way to try Ubuntu than just running from the liveCD. But once you want to start using it, you should have the full install running on its file system.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

---

### Post by jimmyUT on 2010-01-17
Cool, thats what I figured.

I see a lot of different opinions on how big the Ubuntu partition should be.  I have a 100G HDD ... 

What is your suggestion on size of Ubuntu partition?  I don't do any programming or anything like that, would just be using it for web, email, and the basic stuff.  

I just like the way firefox and thunderbird operate under Ubuntu better than XP.  I also notice that my HDD doesn't get access nearly as much in Ubuntu compared to XP and my fan runs quite a bit in XP, but not nearly as much in Ubunutu.

---

### Post by ivan.p on 2010-01-17
Short answer: as much as you can.

Long answer: I'd normally say 8GB minimum, but in your case 15GB seems a good first bet to avoid having to resize partitions in 2-3 months. The amount of programs you'll have by default will only take 3GB or so, but you'll soon be installing new programs and possibly virtual machines (to avoid having to reboot your PC).

---

### Post by oldfred on 2010-01-17
If you have 100GB you can easily use 15GB for root (/) and 2GB or your system memory size if you will want to hibernate for swap and use the rest for data. If you want to share data with windows use NTFS. If not use ext3 or ext4. Many suggest a separate /home as that has your configuration files (hidden) and your data. Separate /home makes it easy to do a total reinstall and reuse /home preserving all your settings & data.

I recently went with a separate /home but have a /shared partition for some data I still may want in windows, although I am not in windows much anymore and another /data partition for most of my data. My /home is now only 1GB with all the data elsewhere and only has system settings and a few misc things.

---

### Post by jimmyUT on 2010-01-17
Thanks for the info.

So do I need to partition my hard drive before I install Ubuntu 9.10?  Or will the installation CD guide me through that?

---

### Post by Gardenhomey on 2010-01-17
The installation will guide you through that.

---

### Post by jimmyUT on 2010-01-17
Ok so I did the install and it set up a swap partition of only 1.8 G

Partitions:
1- IBM Preload (xp pro) 52GB

2- Service 4.9 GB - I assume this is Rescue and Recovery from IBM (showed NT/2000/XP in the Ubuntu partitioner when I set  it up)

3- Extended  43GB (contains 2 logical partitions)
       a- File System 41GB
       b- Swap Space 1.8GB

 
I have 3G of ram, so shouldn't the swap be 6G?

How do I change that?

---

### Post by jimmyUT on 2010-01-17
I also noticed there are 2 Ubuntu OS in Grub   .17 and .14  Do I need both?

It also gives me the option of XP and another line with windows NT.. whats that about?

---

### Post by raymondh on 2010-01-17
your swap is Ok.

The two ubuntu options are kernels.  it is suggested often here (in the forums) to have two kernels ... that way you can boot into the other should your existing kernel bork.

The windows NT entry is for the recovery partition.

see DRS305's guide about editing GRUB

[http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)

Have fun and happy ubuntu-ing.

Raymond

---

### Post by jimmyUT on 2010-01-18
Awesome, thanks for all the help.

I love the quick response time from all the member here.  GREAT RESOURCE!!!!

---

