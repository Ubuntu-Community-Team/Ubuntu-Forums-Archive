---
title: "partitioning recommendation/advice needed"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by aqkshin on 2013-08-10
Hello all,

I have a 320 gb hard drive, and it has Windows 7 already installed. What I would like to is to install ubuntu besides windows (I will shrink/spare windows to 20 gb). But I also would like later to install other distros such as FreeBSD and Fubuntu for testing. Right now, I am thinking to partition my hard drive like this:

Windows  --  20 gb
/ (root) Ubuntu -- 25 gb 
home   --  20 gb
swap   --  2 gb  (the same as RAM)
Data (music, videos, docs/ebooks) -- 120 gb
?[maybe for docs/ebooks I would do a separate partition -- 10 gb]?
for two other distros, 15 gb each -- 30 gb
--------------------------------------------
this sums up to --  227 gb

I still would have about 100 gb free space! Doesn't look like an efficient partitioning to me. What would you guys recommend as more efficient??

By the way, for Data, I don't think I will need to fill up more than even 100 gb. For docs/books, yes, I have many files to fill up at least half of 10 gb.

I would really appreciate your advice. 
Thanks

---

### Post by ibjsb4 on 2013-08-10
I like simple.  Windows, ubuntu, data and swap.  A lot of people do like the separate home partition, will make it easier to reinstall or run multiple installs.  [More here.]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partition+schemes&sa=Search&cof=FORID:9")

---

### Post by aqkshin on 2013-08-10
Thanks for your reply, and the link. I actually did some search but it's very difficult to find exactly what I am looking for. I actually tried to install ubuntu, but when I wanted to set partitions, I ended up unallocated space more than 100 gb. So, I quit installing, and now trying to fix this from Windows 7. Also, sorry if this sounds dumb, but how come windows takes 2 primary partitions one for boot (100 mb) and one for C drive (30 gb)? Is this normal? I thought that windows would only take one partition. 

So, the thing that confuses me is what happens when I install ubuntu and thus grub? Where does grub go? to 100 mb windows partition or separate partition? Or is it just installed at root of Ubuntu?

---

### Post by ibjsb4 on 2013-08-10
Grub will take over your windows boot partition once ubuntu is installed.  I do not run windows, but it is my understanding that you need the windows recovery disk to restore windows boot if you remove ubuntu.

---

### Post by oldfred on 2013-08-11
Do not use Windows for partitioning. It may convert to dynamic partitions which does not work with Linux at all. And Windows cannot create Linux partitions. Use gparted.
Do use Windows for shrinking the Windows NTFS partition, but reboot Windows immediately so it can run its chkdsk or other repairs.

With Windows 7 they converted to using the separate (hidden) 100MB boot/repair partition. Primarily so you could encrypt the main install as the boot files cannot be encrypted. May also let you into repair console if main partition needs repair, but better to have a Windows repairCD or flash drive anyway which you can make from the Repair console while Windows still works. 

Never install grub to anything NTFS. Windows has vital boot code in the NTFS PBR or partition boot sector. With BIOS you install grub to sda, sdb or the MBR of the boot drive not to a partition's PBR like sda2 or sda3 etc.

My install is 25GB for / (root) including /home. I use about 9GB including 2GB for .wine with Picasa which still is in my /home and not in my data partitions. I have two data partitions. One 100GB still NTFS from when I booted Windows and just have not moved it to Linux formated data partition. And another 100GB for data in Linux format. I then have a lot of 20 to 25GB for other installs (may be large but I have the room).
But I am aggressive about moving data from /home and linking it back into /home, so /home really only has the hidden user settings (and .wine). I even move some normally hidden folders like Firefox & Thunderbird to NTFS so I used only one profile for all systems I have installed.

---

### Post by aqkshin on 2013-08-13
Thank you for thorough reply, oldfred. I did partitions and resizing windows as you suggested. Then installed ubuntu, and everything seems working as expected. I guess grub is automatically got installed to MBR, so no problems with Windows boot/repair partition. 

My partitions are:
/dev/sda1  -- windows boot -- 100 MB
/dev/sda2 --  windows        -- 30 GB
/dev/sda3 --  Data (ext4)    -- 114 GiB
/dev/sda4   extended
       --- /dev/sda5    --- /               -- 20 GB
       --- /dev/sda6    --- /home        -- 20 GB
       --- /dev/sda7 --- swap          -- 2 GB

unallocated     --    114 GiB
(doesn't sum up to 320 GB: i think this is just due to GB GiB unit difference things)

I read somewhere that it's good to put swap in the end of the disk. But since there would be about 114 GiB distance between OS partition and swap, i thought it would be a bad idea. So, I put swap partition just after home partition. That made more sense to me. 

If you think some other partitioning scheme would be better, I would be glad to hear that..

---

### Post by aqkshin on 2013-08-13
By the way, I would use this unallocated space for other OS's and maybe another data partition too.

---

### Post by Bucky Ball on 2013-08-13
Install Windows on the smallest (primary) partition you can first, at the beginning of the drive. Make a big extended partition with the rest. Sit down with a pen, paper and beverage of your choice and scratch out how you want the drive to look and work.

From what you are saying, you are going to end up with more than four primary partitions. That is not possible on one physical hard drive (unless you're using EFI I believe, oldfred can help there). You are probably going to need to rejig things already to have a max. of four. So, three primary partitions and an extended is the best you can do. BUT, you can have as many logical drives (for all intents and purposes regular partitions) inside the extended the partition. 

Hope that helps. No one can tell you what partitioning set up suits you best, but from what you've mentioned, you'll need an extended partition somewhere. I currently have twelve partitions on my one laptop hard drive, three Win related primaries and a large extended with everything else (shared partition, three Ubuntu installs and a couple of others for playing).

See attached screenshot for example.

---

