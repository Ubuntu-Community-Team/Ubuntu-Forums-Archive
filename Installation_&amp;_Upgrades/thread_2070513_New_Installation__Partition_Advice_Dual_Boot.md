---
title: "New Installation / Partition Advice Dual Boot"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by pitviper296 on 2012-10-12
Hello everyone I'm new here to the forum but not very new to Linux, but it has been some years since I used it. I'm looking to dual boot My Win XP sp2 with Ubuntu 12.04 and I have some questions if I may.

System Info - Dell Inspirion e1405 
2 gigs ram
1.60 ghz dual core processor 
1 tb seagate momentous 5400 rpm hdd

My machine currently has Winxp installed on a separate 120 gig hdd. And I have dual booted before. Main questions I have deal with partitions and do's and dont's

My factory machine came with windows xp and a hidden dell resources partition.  So what I would Like to do with the 1tb drive is create the following partitions for my install.

partition 1 - Win xp - NTFS 
partition 2 - Ubuntu - EXT4
partition 3 - Random Linux install - Prob change it often
partition 4 - Shared ntfs storage for both os's to use
partition 5 - dell resources ( hidden ) 
partition 6 - Back-up drive for images of os's 

Now this is where I'm confused - I have been doing some reading where people set up Linux with multiple partitions for " / "    " /home " and " /root " I believe. Why is this done or what advantages are there to doing an install this way. 

And for part 6 would this be correct syntax for using dd to create an .img file on my partition that I can use to restore an OS if some happens to my boot partitions.

sudo dd if=/dev/sda of=/dev/sdc/ubuntu.img to create an image file of my install?

Tips, suggestions. How would you do an install like this? I'm pretty open to idea's , kinda have a plan but yours might be better. Thanks for taking time to read and post a reply.

---

### Post by oldfred on 2012-10-13
I would try to keep both XP & Ubuntu system partitions on the smaller size. Some systems are having issues booting from beyond some point on drive. There was a known issue with old BIOS that could not boot from any partition that was beyond 137GB and the new issue seems similar. Not sure if BIOS setting, grub issue or some combination of both.

I also suggest the separate NTFS data partition. XP should be first on drive in sda1 and 20 to 30GB. Then install Ubuntu's / (root) partition. All the rest can be logical partitions inside one extended partition. That leaves one primary in case you need it in the future. Windows has to have a primary partition to boot from, Linux works just fine from logical partitions.

I think Herman does not even have a separate partition for swap anymore, but most of us do.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

If all or most of your data is in your shared NTFS partition you may not need a separate /home either, just make the / partition a bit large. I use 25GB for / but am real aggressive about moving data from /home into my two data partitions, one NTFS and the other ext3.

I do not like backing up MBR, it just is too easy to reinstall as long as you have a current revision liveCD or USB or Linux repairCD. I usually have several.

Gui, Terminal & alternate install CD rescue grub repair
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

There is no /root, some suggest separate /boot, but only older systems or servers usually need a separate /boot. If you have a smaller / (root) near the start of the drive then /boot is not required.

My standard suggestions, but see comments above as alternatives.
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by pitviper296 on 2012-10-14
Thank you [[COLOR=#DD4814]**oldfred**[/COLOR]]("http://ubuntuforums.org/member.php?u=852711") for such a detailed response and all the great resources you posted on this topic. Herman's info was very helpful as well.  Well I took a screen shot of what I ended up with. Decided to dual boot for now. May shrink a partition and tri-boot later on.

---

### Post by oldfred on 2012-10-14
You are welcome, glad I could help. :)

---

### Post by pitviper296 on 2012-10-15
Well oldfred as you know I'm up and running on Ubuntu 12.04 LTS and I have but another question for all who read this thread before I mark it solved.

I was trying to mess around with my themes a little to make my environment more spiffy. When I came across this theme [http://gnome-look.org/content/show.php/Slickness+Black?content=73210](http://gnome-look.org/content/show.php/Slickness+Black?content=73210) 

After trying to extract the files and copy them to /usr/share/themes and navigating to sys settings appearance, clicking the drop down I notice there is only four themes listed. Upon investigation I realized that it was meant for gtk2 .  Is there anyway I can still use this theme?

While looking around I also noticed in /usr/share/theme folder there was 15 or so diff themes listed but only four show in appearance settings? Any reasons to why or how to get them in the drop down for use?

Thanks in advance

---

### Post by oldfred on 2012-10-15
I do not use themes.

Also see Software Center for themes
[http://gnome-look.org/](http://gnome-look.org/)
[http://kde-look.org](http://kde-look.org)
Other third party
[http://ubuntuguide.org/](http://ubuntuguide.org/)

Some post how they do things:

 [B] 	 Ornery October Screenshots  
[http://ubuntuforums.org/showthread.php?t=2065175&highlight=October](http://ubuntuforums.org/showthread.php?t=2065175&highlight=October)
[/B]

---

