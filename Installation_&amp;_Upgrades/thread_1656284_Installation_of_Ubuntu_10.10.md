---
title: "Installation of Ubuntu 10.10"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by rookie@linux on 2010-12-30
Hi all!

I am a new ubuntu user and I have the following question.

When installing the ubuntu 10.10 there is the option "Install Ubuntu alongside another operating system". How safe is it to use this installation option without partitioning and backup-ing my windows files? Does this option make an automatic partition? Is it possible to loose existing windows files? Currently I am using Windows Vista.

I know that I can use WindowsInstaller, but I 'd like to avoid it.

Thanks in advance!

---

### Post by Herman on 2010-12-30
[COLOR=Red]**It's not safe at all, please do not try this option !!!**[/COLOR]

Maybe with earlier Ubuntu releases that option could be okay, but not in 10.10, refer to thread [COLOR=#980101]**[ubuntu]**[/COLOR]                          [Understanding the new live installer/ubiquity]("http://ubuntuforums.org/showthread.php?t=1622388"), by kansasnoob.

You should also always make a backup before using any partition editor.
You should make regular backups anyway, so right before partitioning is a good time.

Windows Vista is particularly vulnerable to booting problems if the whole partition is accidentally moved too, Windows Vista is the first version of Windows to have its partition starting at sector 2048 instead of the traditional sector 63, after the end of the first track of the hard disk. 
The Ubuntu installer has never had any inclination to move any other systems partitions, but a few old versions of GParted used to do that if they were made before Vista came out or if users didn't know how to use GParted properly.
Maverick Meerkat's GParted is great, and uses the new partition alignment settings by default.

If you need to shrink your Windows partition by more than half way, you can only do that with either GParted or the Ubuntu installer's inbuilt partition editor. You don't need to defrag if you use those tools, but I recommend running CHKDSK /R first and again after. If you forget, Windows  will run a file system check on first boot anyway, this is normal and it is induced byGParted as an extra safety.

If you use Vista's inbuilt partitioner to shrink Windows as many experts recommend, you will probably need to defrag first, and it will only allow you to shrink Windows to half way because the MFT is in the way. Sometimes the Windows page file can be the way too. I'm not sure if the page file is always on the same side of the MFT or not. When I was practicing shrinking Windows 7 mine was not in the way.

I don't know anything about the 'Windows Installer'.

---

### Post by rookie@linux on 2010-12-31
Many thanks Herman! 

Your answer is really of great value to me! I did not want to loose any data, so I was not sure if it could be wise to use the option.

All Best

---

### Post by Herman on 2010-12-31
:p Okay, Happy New Year for 2011! We already had ours here in Australia, but I can see in my mini world time zone map under the small calendar we have under our clock in Ubuntu that it's around midnight in greece now, or getting close.
Good luck with your Ubuntu install. :)

---

