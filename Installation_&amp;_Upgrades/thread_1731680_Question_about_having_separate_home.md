---
title: "Question about having separate /home"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by mtantawy on 2011-04-17
I read many times about recommendations that i should have a separate /home partition, and that by doing so, when a new release is out, i can do fresh install without loosing my files.

My question is, if i did so, all my installed applications will be wiped right? after new installation i mean!

Also, does the installer understand that it should not wipe the old /home but update it (if needed) ?

Is there any way to save time of re-installing all applications again & again every 6 months? without upgrading, because simply, many new stuff do not get applied when upgrading, fresh install is much more recommended everywhere!

One last thing, how much space should be left to / & /home if they are going to be separated? i know it varies from user to user, but average or minimum is much welcomed though!

---

### Post by TheExposedOne on 2011-04-17
wouldn't you just do an upgrade as it is?

---

### Post by mtantawy on 2011-04-17
> **TheExposedOne said:**
> wouldn't you just do an upgrade as it is?
No, i want to do fresh install whenever a new release of Ubuntu is out to take advantage of all new stuff, applications, tweaks, settings, interfaces "Unity for example"!

But i want to keep my files & some applications that i installed, like my web development applications & other applications.

Also, i want to keep the settings i modified in every application because i like to tweak each & every bit of my applications to better suit my needs.

So, i just don't want to repeat all the hard work every time i fresh-install Ubuntu, is that even possible? :D

---

### Post by TheExposedOne on 2011-04-17
do you have an external hdd?

---

### Post by mtantawy on 2011-04-17
> **TheExposedOne said:**
> do you have an external hdd?

Yes! i do have external HDD & i do have other partitions that are NTFS-formatted for use by Windows & Linux.

---

### Post by dino99 on 2011-04-17
here is how i do an install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Of course the main advantage of creating /home is to keep safe your data and the apps config/settings. So either with upgrading or fresh install, while formatting, the installer ask you what to do, you select to NOT format /home indeed (take time to set your choice before pulling down the Enter key :))

---

### Post by TheExposedOne on 2011-04-17
Well i think there' a way to install your most necessary apps that you don't want to lose on there and keep all your files on the external

---

### Post by dino99 on 2011-04-17
> **TheExposedOne said:**
> Well i think there' a way to install your most necessary apps that you don't want to lose on there and keep all your files on the external

Please dont confuse others if yourself dont really know :)

---

### Post by rewyllys on 2011-04-17
> **mtantawy said:**
> No, i want to do fresh install whenever a new release of Ubuntu is out to take advantage of all new stuff, applications, tweaks, settings, interfaces "Unity for example"!

But i want to keep my files & some applications that i installed, like my web development applications & other applications.

Also, iw want to keep the settings i modified in every application because i like to tweak each & every bit of my applications to better suit my needs.

So, i just don't want to repeat all the hard work every time i fresh-install Ubuntu, is that even possible? :D
By far the best way to achieve all of the objectives you enumerated is to use a separate partition for your /home directory.  That way, your files and the configuration files for all the programs you use will be preserved during the upgrade of your system in the / (the root) directory on its own partition, different from the partition holding your /home directory.  (For me, this capability of easily separating my personal data and configurations from the program files is one of the strongest arguments for using Linux.)

You will have to re-install any programs you use that are not part of the new system installation, but that is easy using the Synaptic Package Manager and the Ubuntu Software Center.  You will not have to re-configure such programs; they will find their previously established configuration data in your untouched /home directory.  (To aid my memory, I keep a written list of the programs that I need to re-install.)

Just be careful that you DO NOT format your /home partition during the upgrade or new installation of your system!

---

### Post by mtantawy on 2011-04-17
Thank you all for the help.

I have one more question, what size -or minimum size- the / & /home need?

And, to summarize things up to make sure i fully understood you all:
[LIST]
[*]I should uncheck the box where it says "format" beside /home
[*]settings i change & configurations i make to applications are saved to my /home AUTOMATICALLY so after fresh install i only need to re-install my applications
[/LIST]

i keep a list of my installed apps as well :D

Just please someone confirm that i fully understood your replies & if possible answer my question about partition sizes :)

---

### Post by oldfred on 2011-04-17
I have installed a lot of apps and my / (root) is about 6 to 7GB. My /home is only 1GB with .wine & Picasa taking up most of that. I have all my data in other partitions.

One place recommended to keep / at 25% use. I have typically recommended 10-20GB for root. Writing a DVD may use another 4GB in /tmp so I like to have room and have 20-25 GB for every root I have.

You may want to houseclean apps before making list. I still am reinstalling python 2.5 which I do not want anymore for example.
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

### Post by tlcstat on 2011-04-17
Greetings,
Here's my opinion and experience on this. 
This scheme keeps the grub files off of you root partition so that your boot doesn't get messed up if you restall root. USR and Home are preserved. Always backup Home and USR before reinstalling, especially if you are an expert. Noobs will usually mess-up on the backup part but experts should know better. This scheme will result in an extremely fast system and so far I haven't seen my 3Gig Swap file used at all.

SDA1 512Meg EXT2 Primary Boot for grub files
SDA2 3Gig Primary Linux Swap
SDA3 20Gig EXT4 Primary /
Remainder Extended Partition
SDA4 20Gig EXT4 USR
SDA5 20Gig EXT4 for testing other OS if wanted
SDA6 Remainder_Gig EXT4 Home
SDA7 Possibly a small NTFS Partition if you need it for sharing files.

tlcstat


For Dual boot Windows Partitions vary with HD size.

SDA1 50Gig Primary NTFS (fully install Windows to boot before continuing)
SDA2 EXT 500Meg for Grub files Grub in SDA
SDA3 3Gig Linux Swap
Extended
SDA4 20Gig EXT4 /
SDA5 20Gig EXT4 USR
SDA6 ?Gig EXT4 HOME
SDA7 ?Gig NTFS for shared files with Windows
SDA7 20Gig for testing partition if wanted

---

### Post by rewyllys on 2011-04-17
My / directory contains about 7.8GB at present.  The partition I use for it has 40GB, so I'm in line with the advice that Oldfred mentions: to keep your / partition's actual use to about 25%.  Incidentally, that sounds rather conservative to me, but one should certainly try to have no more than 65% to 70% of the available space on a system drive be actually occupied.

My /home partition has 1TB available to it; the hard drive that houses my Ubuntu system is a 1.5TB drive (which seemed very large when I bought it two years ago:p).  I actually have about 50GB of files occupying /home at present, so I don't have to worry about adding further files.;)

---

### Post by georgemc on 2011-04-17
OP, take a look at post #3. 


[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

hope this helps.

George

---

### Post by tlcstat on 2011-04-17
Greetings,


> OP, take a look at post #3. 
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

hope this helps.


Great post! I think I will add most of that to my Lucky Backup as a reinstall profile. That way most of the work will already be done.

tlcstat

---

