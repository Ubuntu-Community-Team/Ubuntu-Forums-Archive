---
title: "What's the most efficient partition scheme?"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by cokhavim on 2006-06-13
hello,

i'd like to include these partitions on my harddrive:

ntfs (windows)
ext3 (/) (ubuntu root)
ext3 (/home)
swap
fat32 (for sharing files)

i've heard that the order of the partitions affects speed and efficiency.  for example, i've heard that windows should be first, and that the linux root partition should be as close as possible to the swap, and yet also as close as possible to the top.  can any of you confirm this?  what do you guys think is the best order for me to set up the above partitions for maximum efficiency? (note: i hardly ever use windows).

thanks!

---

### Post by spyke01 on 2006-06-13
youre actually stuck with windows being first, XP requires that it be installed on the first partition of the first drive. I believe that 3.1-98se are not like this, but those afterwards are.

Your scheme like it is should be fine, mine is very similar, but i don't have a seperate parition for my home folders.

---

### Post by mattlach on 2006-06-13
Agreed.

I would do 
-NTFS
-ext3 (root)
-swap
-fat32

When I first started using Ubuntu I was surprised it by default doesnt have a separate boot partition.

Every other linux distribution I have used prefers that configuration.

---

### Post by ubnoobie on 2006-06-13
[QUOTE=cokhavim]hello,

i'd like to include these partitions on my harddrive:

ntfs (windows)
ext3 (/) (ubuntu root)
ext3 (/home)
swap
fat32 (for sharing files)

[/QUOTE]

if i was going with the above, it'd look like this:

hda1 ntfs windows
hda5 swap
hda6 /
hda7 /home
hda8 fat32

if i had plenty of ram (1gb +), anticipating minimal-to-no swap usage, i'd probably put swap after /home instead of before /

what i have, though, is two windows installs (98/xp) and only 512mb ram, so i've got this instead:

hda1 fat32 win98 (unmounted)
hda5 ntfs winxp (unmounted)
hda6 ext3 /boot
hda7 swap
hda8 ext3 /
hda9 fat32 /media/backup
hdb5 fat32 (2nd drive) /media/docs

installing 98, then winxp. xp/98 dual boots using winxp. then linux was installed on top of that, grub to first hd's mbr. grub menu has ubuntu & windows; and the windows option brings up the nt boot menu (with 98/xp as the options). hda was imaged both before and after linux installation, so i can recover the entire drive or individual partitions if needed.

---

### Post by cokhavim on 2006-06-15
hey, thanks for the advice!

---

### Post by aysiu on 2006-06-15
I've never heard of Windows being first as increasing speed and efficiency. I think it just demands to be first on the drive.

That said, if you want an efficient partitioning scheme, consider getting rid of your FAT32 partition and instead installing [http://www.fs-driver.org](http://www.fs-driver.org) on Windows to read/write Ext3.

Read more here:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by blackmh on 2006-06-15
[QUOTE=spyke01]youre actually stuck with windows being first, XP requires that it be installed on the first partition of the first drive. I believe that 3.1-98se are not like this, but those afterwards are.
[/QUOTE]

I believe it's vice-versa since my XP are installed on D:

---

### Post by Herman on 2006-06-15
Hello group,>  I've never heard of Windows being first as increasing speed and efficiency. I think it just demands to be first on the drive. Yes, probably that's right, aysiu, it's likely as simple as that. It might be for historical reasons from the 8.0 GB BIOS limit days too.
>  i've heard that the order of the partitions affects speed and efficiency.  for example, i've heard that windows should be first I had a comment on my website about this subject in case that's where the idea has come from. I think it was more along the lines that I suspected that Windows might *prefer* being first on everyone's disk because the first of the disk might have a speed advantage. I didn't say anyone *should *place Windows first though.
There could in fact be a speed advantage in being first on the disk. I don't know if it would be enough on a modern hard disk to be noticable to the average user.
I first got that idea from reading this page: [Linux Partition HOWTO]("http://www.tldp.org/HOWTO/Partition/")
In particular this section of that page: 4.4. [Swap Partitions]("http://www.tldp.org/HOWTO/Partition/requirements.html#SwapSize") , specifically, section 4.4.3 "Where should I put my swap space?"
and also the linked reference: "Kristian's more recent [comments]("http://lissot.net/partition/mapping.html")         on this issue."

I don't think Windows *has* to be first on the disk, but it seems easier. Some people have more than one version of Windows on a disk, so obviously Windows is capable of running on partitions that are further inside the disk. I have never bothered to experiment with that. Maybe I'll give it a try today and see what happens. Maybe I should find out how to move Windows (with GParted) and put Ubuntu first on everyone's disk instead.

Regards, Herman :D

---

### Post by Herman on 2006-06-15
>  ntfs (windows)
ext3 (/) (ubuntu root)
ext3 (/home)
swap
fat32 (for sharing files)

i've heard that the order of the partitions affects speed and efficiency. for example, i've heard that windows should be first, and that the linux root partition should be as close as possible to the swap, and yet also as close as possible to the top. can any of you confirm this? what do you guys think is the best order for me to set up the above partitions for maximum efficiency? (note: i hardly ever use windows).
 Well I just conducted my experiment and it seems to have been 100% successful. I used GParted LiveCD to copy my resize both partitions quite small first, to give me plenty of free space for manouvering.
Then I copied and deleted each partition a number of times until I got them each where I wanted them, (Ubuntu first, Windows second), with their original partition numbers back again. 
If this is done during a fresh install, and Windows is on the disk by itself, it would be simpler. Windows could just be resized and moved, leaving space for Ubuntu at the beginning of the disk. That would not change Windows partition number.

It is important to stress to anyone who may try this if they are doing it after the install like I am, they need to copy and paste their partitions twice each to get the original partition numbers back unless they want to re-install GRUB. I don't know how it would affect Windows to have its partition number altered, it might remain unbootable. I copied and pasted mine until I got the same partition numbers again.

    I have rebooted both operating systems three or four times each to make sure. They both seem to be working fine.

Right now I am thinking (if everyone's computer will behave similar enough to mine under these circumstances), it would be better to install Ubuntu at the beginning of everyone's disk and move Windows towards the end. It makes an extra step in the install process, but it would be better in the long run. I think this not so much for any possible speed advantage, but because it would be better to have Ubuntu at the beginning is for the purpose of re-sizing Ubuntu later on. Linux partitions can be resized from the end easily  but not from the beginning of the partition. Having Ubuntu first on the disk means  new people who are dual booting for the first time can adjust Ubuntu's porportion of their disk space very easliy if they don't get it right the first time or their needs change. (For example, it is common for them to want to shrink Windows and allow more room for Ubuntu after a few weeks).
Right now the way we have been doing things all along seems backwards all of a sudden. It makes a lot more sense to me to have Ubuntu first and Windows second. (On the disk)  For me Windows needs to be installed first (chronologically) though, because I have those Windows 'Recovery disks', Windows will erase Ubuntu otherwise.

cokhavim,
I think your partitioning scheme is okay. Personally I don't believe in a seperate /home partition at all though. I know lots of people do, but I'm a real independant thinker. It is much better to make a small copy of your Ubuntu partition (after adding your favourite software, tweaks and settings) and paste it to the end of your disk somewhere with GParted LiveCD. Then if you ever need to restore the whole operating system someday, you can do that in a few minutes with GParted LiveCD, just have your files backed up somewhere else. 
Those are my ideas. Regards, Herman :D

EDIT: (Spelling)

---

### Post by RRS on 2006-06-15
Herman;
Thanks for not just the results if your experiment but running it in the first place.

I have a second machine that I plan to reinstall Windows on and then do a fresh install of Dapper to replace Breezy         (I did a pre-beta upgrade on this one). If I have time this weekend I'll follow your example and move Windows to the end.

Thanks again
P.S. don't mean to hijack thread, sorry.

---

### Post by Herman on 2006-06-15
RRS: Don't mention it, experiments like this are my favorite passtime!

I would like to thank  cokhavim, for asking such a great question! I know I will be moving Windows to the end and installing Ubuntu at the beginning of my disk from now on! And I'll be advising others to do the same whenever anyone asks.

I'm thinking of re-editing my install website too, but I'm not sure to what extent yet. That will take time. I had been dreaming of some MBR/bootloader experiments all week while I was at work, I might do those first.
Regards, Herman :D

---

### Post by cokhavim on 2006-06-16
wow, didn't know my question would start an experiment!  thanks Herman for doing the experiment.  i think i'll follow your example and put windows at the end.  i hardly ever use windows anyway.  

however, i'm not sure i understand why you don't want a /home partition.  what do you see as the disadvantage of having a /home partition?  

for me, the disadvantage of *not* having a /home partition is that you have to move all your files every time you do a clean install of a new ubuntu version.  i have all my tweaks and programs in a special folder in my /home directory, complete with my personal notes so i can install everything again easily.  in fact, i may write a little script to reinstall all my programs automatically every time i do a clean install of ubuntu.

---

### Post by catlett on 2006-06-16
I agree about the home partition. Not everyone has unlimited disk space to have full backups of all their data. Also some people have huge amounts of data in their home folder. If someone just plays around with linux I can see not having a seperate home. But if you are going to have linux be your only computer OS  I think it is just prudent to have home on a seperate partition where it is safe from a system failure. If anything ever happens to your system then you can reformat and reinstall without affecting your personal data. How is that not prudent and advisable?

---

### Post by pelago on 2006-06-16
I don't have a separate partition for /home, because I'm not sure how big to make the / partition. I don't want to make it too small in case apt-get updates take up more space, and I don't want to make it too big as that's valuable disk space wasted that I could do with in /home!

If I want to do a clean install I boot with a liveCD, mount the partition read-write and carefully delete everything except /home. Then I install to that partition, making sure not to format it.

---

### Post by Herman on 2006-06-16
I think now that we have [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") it's time to have a fresh look at our old ways of doing things. It's so much quicker and easier now to do anything we like with our partitions than it was only a few months ago. An entire operating system, minus data and reduced to minimal size, can be copied and pasted to the end of a hard disk as a back-up copy.

I like to keep each operating system on a single partition to make it easier to apply that strategy. Also, I like my hard disk to be nice and neat and tidy for multiple booting. Doubling the number of partitions that all look the same quickly becomes a headache when multiple booting. The minimal sized back-up copy or copies don't get in the way though because they are at the end of the disk and easy to identify by their small size.

When the next edition of Ubuntu becomes stable enough, I will install it alongside the current version and it's very easy to transfer data from the current version to the test version to try it out. If the test version fails I can just re-install it again either from one of these 'partition back-ups' or from CD.

I think it would be very difficult to beat my back-up plan for safety, speed and efficiency. I keep all my data backed up in a seperate external USB drives. I have two of them. I store most of my data on the USB drives and only have some of it on my main disk at a time for immediate use. Not very much of my data is exposed to any risk. 
Hard drives are getting cheaper nowdays and external USB drives are very fast and convenient to use. For a dollars per GB of storage value, they would compete with DVDs and CDs. For ease of use they win hands down. Mine are old laptop hard disks, (2 1/2"), so the size of the case is just right to fit into a shirt or jacket pocket if I'm travelling. It was only $20 or so for the case (caddy). A 40.0 GB laptop hard disk costs about $120 (Aust.) new.

Now backing up all our added software, tweaks and settings is something most people would like to be able to do.
Your idea of making re-install scripts to automatically re-install programs sounds like a great idea, cokhavim, I'd like to learn more about that. I have used automatix, but I  haven't tried making my own scripts. I have  a copy of '[Linux Rute Users Tutorial]("http://rute.2038bug.com/index.html.gz")', where I was learning the [basics of making a script]("http://rute.2038bug.com/node10.html.gz"). Maybe I should get back to working on that soon. Thanks for that tip, cokhavim, can you tell us more? Perhaps show us an example?

The way I have my entire operating system (with the data removed and resized as small as possible), pasted to the end of my drive makes it simple and quick for me to restore my complete operating system in the event of a disaster. I just boot GPartwed LiveCD, delete the 'hosed' OS partition and copy and paste the backup copy of it back in the now empty space it came from. Then I resize it to normal size for adding my data. As soon as I reboot I'm ready to go again in a few minutes. All bookmarks, email settings, customizations, added software, it's all there set to go.

Now I can't see the need for having a seperate /home partition. If we have data exposed that we haven't got the media capacity or is too inconvenient and time consuming to back up, sooner or later we are going top loose it all. Then we'll be  very sad. If we are installing a newer version, it's pretty quick to just install it alongside the older version and just transfer the data across. Then when the lates version gets released, delete the previous version when finished with it.

As pelago stated, we either make the /home partition a little too big to leave room for growth and waste some space, or we make it too small and have to resize it someday.  Directories are always exactly the size we need, they resize themselves automatically. That's very convenient. I have helped people with trying to resize these /home or '/' (root) partitions often enough. Because the Linux filesystems are fixed at the start point it can be quite a juggling act to get everything pasted and copied around, resized and back to normal again. Resizing partitions can be very inconvenient.
I like pelago's idea here,> If I want to do a clean install I boot with a liveCD, mount the partition read-write and carefully delete everything except /home. Then I install to that partition, making sure not to format it.
I'll give that a try someday. 

Now, admittedly, I'm making an extra partition too, but it's compact and small, there's no wasted space in it, and it's neat and tidy and out of the way at the end of the disk where it is easy to identify. And it won't require resizing.

I have a new install now, with Ubuntu first on my disk and Windows at the end like we were discussing earlier. Soon when I have it all set up I'll run a test and see how long it takes to delete and then fully restore my system  and I'll let you know and I'll challenge anyone to come up with an easier and more effective back-up plan. I'll need to specify details about exactly what needs to be backed up restored and how many GB of data, etc, for comparisons to be valid.
This could be fun and we might all learn some new tricks!
Regards, Herman :D

---

### Post by cokhavim on 2006-06-18
[QUOTE=Herman]
Now backing up all our added software, tweaks and settings is something most people would like to be able to do.
Your idea of making re-install scripts to automatically re-install programs sounds like a great idea, cokhavim, I'd like to learn more about that. I have used automatix, but I  haven't tried making my own scripts. I have  a copy of '[Linux Rute Users Tutorial]("http://rute.2038bug.com/index.html.gz")', where I was learning the [basics of making a script]("http://rute.2038bug.com/node10.html.gz"). Maybe I should get back to working on that soon. Thanks for that tip, cokhavim, can you tell us more? Perhaps show us an example?

[/QUOTE]

well, i haven't written the script yet; in fact, i haven't even installed the new ubuntu yet, as i've been a bit busy.  but writing a shell script purely for reinstalling programs should be pretty simple.  there shouldn't be any need for complicated loops or functions.  the simplest shell script is basically a list of terminal commands that you want to execute one after the other with one command.

for reinstalling programs, i was thinking of something like this:

```

#! /bin/sh

#for installing programs from apt-get
sudo apt-get install my_favourite_program  
sudo apt-get install another_favourite_program 

#for installing programs for which you already have the .deb
sudo dpkg -i myprogram.deb

#etc, etc,

exit 0

```

save this script with some name like "installmyprograms" then 

```
chmod u+x installmyprograms
```

and the command ```
installmyprograms
``` should install everything, prompting for your password once.

your personal settings, like bookmarks, wallpaper, etc, should already be saved in your /home directory.

if you want to do more things like edit configuration files with a script, you could simply have a copy of all your config files in a special "ubuntutweaks" folder in your /home directory, and tell the script to copy them to the appropriate place after you've done a clean install.  for example, to change my xorg.conf file, add something like this to the script:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_original
sudo cp ~/ubuntutweaks/xorg.conf /etc/X11/xorg.conf

```

i probably don't recommend this because i don't know if configuration files differ for each ubuntu release.  blindly changing them with a script may break things.  of course, you could also write a script to restore the original config files in case you do break something, which you could execute in ubuntu's "recovery mode."

once i get around to doing all this, i'll post my example.

---

### Post by Herman on 2006-06-19
Here's my humble effort so far, it works great for evolution!
Firefox has a directory in it that always has a different name, so I can back up firefox, but not the bookmarks only. 

Backup script,
```
#!/bin/sh
mkdir june06bak
cp -r .evolution/mail june06bak
cp -r .evolution/addressbook june06bak
cp -r .evolution/calendar june06bak
cp -r .evolution/tasks june06bak
cp -r .mozilla/firefox
``` Restore script,
```
#!/bin/sh
cp -r june06bak/mail .evolution
cp -r  june06bak/addressbook .evolution
cp -r  june06bak/calendar .evolution
cp -r  june06bak/tasks .evolution 
``` My time is limited right now, but I can see this has great potential, I can hardly wait to get some spare time so I can get this a little fancier! 
Thanks, cokhavim, I'm enjoying learning this!
Regards, Herman :)

---

### Post by pdk on 2006-06-19
[QUOTE=Herman]Well I just conducted my experiment and it seems to have been 100% successful. I used GParted LiveCD to copy my resize both partitions quite small first, to give me plenty of free space for manouvering.
Then I copied and deleted each partition a number of times until I got them each where I wanted them, (Ubuntu first, Windows second), with their original partition numbers back again. 
If this is done during a fresh install, and Windows is on the disk by itself, it would be simpler. Windows could just be resized and moved, leaving space for Ubuntu at the beginning of the disk. That would not change Windows partition number.

It is important to stress to anyone who may try this if they are doing it after the install like I am, they need to copy and paste their partitions twice each to get the original partition numbers back unless they want to re-install GRUB. I don't know how it would affect Windows to have its partition number altered, it might remain unbootable. I copied and pasted mine until I got the same partition numbers again.

    I have rebooted both operating systems three or four times each to make sure. They both seem to be working fine.

Right now I am thinking (if everyone's computer will behave similar enough to mine under these circumstances), it would be better to install Ubuntu at the beginning of everyone's disk and move Windows towards the end. It makes an extra step in the install process, but it would be better in the long run. I think this not so much for any possible speed advantage, but because it would be better to have Ubuntu at the beginning is for the purpose of re-sizing Ubuntu later on. Linux partitions can be resized from the end easily  but not from the beginning of the partition. Having Ubuntu first on the disk means  new people who are dual booting for the first time can adjust Ubuntu's porportion of their disk space very easliy if they don't get it right the first time or their needs change. (For example, it is common for them to want to shrink Windows and allow more room for Ubuntu after a few weeks).
Right now the way we have been doing things all along seems backwards all of a sudden. It makes a lot more sense to me to have Ubuntu first and Windows second. (On the disk)  For me Windows needs to be installed first (chronologically) though, because I have those Windows 'Recovery disks', Windows will erase Ubuntu otherwise.

cokhavim,
I think your partitioning scheme is okay. Personally I don't believe in a seperate /home partition at all though. I know lots of people do, but I'm a real independant thinker. It is much better to make a small copy of your Ubuntu partition (after adding your favourite software, tweaks and settings) and paste it to the end of your disk somewhere with GParted LiveCD. Then if you ever need to restore the whole operating system someday, you can do that in a few minutes with GParted LiveCD, just have your files backed up somewhere else. 
Those are my ideas. Regards, Herman :D

EDIT: (Spelling)[/QUOTE]
I have just downloaded my first Ubunto 6.06, and am enjoying the challenge of my second install. The first default put a bad boot record on my hda disk which has XP on, and the wife wanted system back that evening.
(built a new XP, got back on line and found fdisk /mbr :) )
Now I want to put it on my hdc drive behind the backup XP.
This thread has definitely shown the way to complete my second try.
However what happened to the concepts of
/   root
swap
/home
/usr
/var
/opt

I guess with the limit of 4 primary partitions I would go for
/
/usr     
/opt     (for software)
swap
the ntfs of XP taking the first primary.
Seperate partitions make for a clean system and easier backups.
With linux , if you run out of space you can simply create a link.
Peter  (PDK)

---

### Post by Herman on 2006-06-20
>  However what happened to the concepts of
/   root
swap
/home
/usr
/var
/opt

I guess with the limit of 4 primary partitions I would go for
/
/usr     
/opt     (for software)
swap
the ntfs of XP taking the first primary. As far as I know, Windows is the only operating system that 'insists' on being on a primary partition. Oh, and I think Mandriva Linux did too, when I tried that. Ubuntu (and most other Linuxes probably), can be installed on all logical partitions, and you can have up to 63 of those I believe. on an IDE disk. So you can make an install on as many seperate partitions as you please! There is no difference in performance  whether you use primary or logical partitions for Ubuntu that I can detect. :) 
He-eh, I guess each to their own, everyone is free to set up and configure their Ubuntu system they way they think best, and we all think our own way is best! That's part of the fun I guess! :D
Good luck with it, pdk, and enjoy! Regards, Herman. :)

---

