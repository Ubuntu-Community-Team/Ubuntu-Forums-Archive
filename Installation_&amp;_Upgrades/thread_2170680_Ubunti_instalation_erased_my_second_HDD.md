---
title: "Ubunti instalation erased my second HDD"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by YoYoDiN on 2013-08-27
Hello folks, 

well i think the title is kinda self-descriptionary. I worked with Ubuntu in VM for a while and decided to install it for the first time as second OS on my PC. 
I have 2 HDD: 
- 120 GB SSD (40 GB free)
- 1.5 TB HDD (1TB free)

I used first option in installation menu (install as second OS, saving your documents). Everything went kinda well OS booted up and I just shut down my PC and went sleep. Today I tried to boot into Windows and saw that system cannot detect my second HDD.
I used NTFS recovery tool to see what kind of partitions are on that drive and if I can restore them. But the only thing I saw was Ubuntu file system.

Seems like Ubuntu installer decided to "keep my documents", gently erasing my whole drive partition table. So the question is: WTF?! Or in other words is it possible to restore my data in easy way and how can I kill installer developers? 

Any suggestions about selecting recovery tool?

---

### Post by mastablasta on 2013-08-27
it did exactly what you asked it to do. it kept the "documents" folder and such intact.

recovery will be very difficult as disk is not only erased, but reformatted. someone else will help you with that (recovery). best would be to unplug that disk for now and don't do anything on it until you attempt recovery.
i am sure you read instalation procedure for dual boot before deciding on install. what you were supposed to do is either create an empty, unformatted disk space (using windows partition tool) and tell install to use largest free disk space (which would then format this created space and install the OS to it). or chose manual partitioning on install and then point the available partition where Ubuntu can instal and then create at least / (or root) and /swap partitions.

i am not sure what guide you followed, but these two procedures are simple enough to do. the most important thing to do is create backup before doing anything with disk file systems. easy backups can be made with Redobackup (or Clonezilla) and external disk.

the problem with windows is usually that preformated disk already takes all available 4 primary partition or UEFI and dual boot. both require some extra work and things thta can go wrong. but neither of these two are an issue in your case. i hope you manage to solve your issue and recover the data.

---

### Post by YoYoDiN on 2013-08-27
Yeah in I knew what in Linux world documentation is very important part of using OS. But I thought Ubuntu is going user-friendly way and I saw lots of advertising in Internet about how any person can do it. So I erroneously decided what Ubuntu installer have reached that intelligence level when it can find out what partitions on my HDD have the biggest free size value available for installation (1 TB probably should be enough on the single-partition HDD) take a slice of it and proceed. I don't really think it's such a big deal. So pretending I'm non-educated beginner (that is actually true) i just selected first option hoping everything will go just right and at the end i just lost all my data without any warning about possibility to loose it. Whats kinda sucks.

Ofc. I should read all that documentation or select advanced options and do re-partitioning myself. But why on earth selecting "Keep my Windows 8 installation saving all my blablabla" option just bring me in such kind of situation without any warnings? 

I don't really think Ubuntu should position itself as user-friendly with all that big buttons and  short descriptions, then it can just silently destroy most important part of any PC - user data.

PS. I had my documents and UserData folders on 1 TB hdd, so nope, it doesn't kept anything intact.

---

### Post by 1/0 on 2013-08-27
Well, installing Windows will do the same to other OS:es (and sometimes even itself) so reading the installation instruction is a must and backing up before doing installations and partitioning is always a have to!

Now that you have this problem, how important is getting the data back? If you want the data back (if it's possible) do not install or partition that drive further. Unplug it and access it from another computer. I used [Diskinternals Linux Reader]("http://www.diskinternals.com/linux-reader/") in order to access a drive that I accidentally formatted but that was ext4. Your's is NTFS and there's plenty more software for rescuing data from NTFS formatted drives than ext4. Some cost others are free. Diskinternals has one for ntfs, there's the getdataback software, testdisc and photorec. There's plenty more. If you really really have to save the data. Hand it over to a professional because if you use the recovery software in the wrong way, you will permanently delete the content.

---

### Post by YoYoDiN on 2013-08-27
Thanks guys for pointing how stupid I was :) I know it's mostly my own fault but one simple dialog saying "WARNING All existing data on your partition will be lost!" would save the day. 

It's simple logic: By selecting menu what says "save my data" I automatically assume what this indeed will save my data. All of it.  Or at least show some partitioning tool or warning. 
I downloaded ISO image a week ago and expected it would go out of the box without any additional readings. 
Well my bad. It was not so user-friendly as I expected. 

Honestly I had 2 options before I began installation 
1 - easy way - Ubuntu: insert CD, install, have fun.
2 - long way with any other distributive: researches, readings and self picking of all necessary packets.

Obviously I made a huge mistake. No fun for me

---

