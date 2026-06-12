---
title: "Biting the bullet!"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by fwlii on 2011-01-06
I have been happily using Ubuntu 10.04 inside Windows XP for the last 3 months as a dual-boot install.  Ubuntu has been flawless and has made my old Compaq desktop run like a supercharged race car!  Now I'd like to bite the bullet and 1) Repartition my entire harddrive, 2) Do a clean install of 10.04 and 3) Install Virtualbox and run XP as a guest OS inside Ubuntu as I have Windows 2 apps that I have paid licenses for that aren't offered and don't run under Linux. 

I would like to preserve all of my currents settings, etc. from my existing Ubuntu environment, but I just did a basic install, so I don't have /home running in a separate partition.  

I'm a Linux newbie, but a 30-year developer and admin in the IBM world, so I am pretty intuitive.  Any suggestions/advice would be greatly appreciated!

Thanks!

---

### Post by prince_sabin on 2011-01-07
If your ubuntu is on a separate partition right now then you can delete the windows partition and resize your ubuntu (using gparted from the live cd).  If you want to reinstall or have a wubi install. Here are some tips:

All your settings are in your home directory.  They are named starting with a dot (.) which means they are hidden.  Use ctrl-h to see them.  When you backup your home directory grab all those files too.  When you restore home directory all your setting come with it.

If you have your programs installed through the repository, then you can use this trick to install all those programs (and packages) again:

[http://linuxandfriends.com/2008/11/13/backup-and-retrieve-list-of-installed-packages-for-quick-software-restore-in-linux/](http://linuxandfriends.com/2008/11/13/backup-and-retrieve-list-of-installed-packages-for-quick-software-restore-in-linux/)

---

### Post by Bucky Ball on 2011-01-07
Hmm, but when you install Ubuntu it will make a /home folder with its own settings. Guess you could then plonk the contents of your /home backup in there (ONLY if installing the same Ubuntu release and kernel) and overwrite the existing folders/files when you get the 'Folder/file already exists, do you wish to overwrite?' message.

When you say you are running Ubuntu inside Windows do you mean using VM? Either way that is not a dual-boot exactly. Dual-boot generally refers to side-by-side on separate partitions. ;)

Welcome to the forums! With your background I'm sure you'll pick things up quickly. Enjoy the learning curve. 

PS: if you want to see it really race try the Xfce Desktop Environment! Once you have your current problem sorted, that is. It is easy but I'm jumping the gun.

Good luck with it. :)

---

### Post by Rubi1200 on 2011-01-07
Hi fwlii,
there are two things I would like to suggest:
first consider migrating the Wubi install to a partition on the drive and then work from there.

Here is a guide by bcbc on migrating Wubi:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

If you want to backup your Wubi install, see here:
[http://ubuntuforums.org/showpost.php?p=10304745&postcount=49](http://ubuntuforums.org/showpost.php?p=10304745&postcount=49)

I have not had time to read the whole article, so I cannot say whether it would then be possible to import settings etc. into a new install on a dedicated partition.

In any event, I hope this helps.

Good luck!

---

### Post by fwlii on 2011-01-07
Thanks for the tips guys.  Here a little more detail:

I've been reading a lot about recommended partitioning schemes and was thinking this was the best time to do it right.  My old Compaq has 1gb of ram and a single hd of 200gb.  What seems to make the most sense to me is a single primary partition of 10gb for root and a single extended partition for the rest of my hard drive.  Then cutting it up into separate partitions for /home (10gb) and /swap (2gb), then the rest as a single data partition.  This make sense to you or you have other recommendations?

Bucky Ball, to answer your question, I used Wubi to do my initial install of ubuntu to run as a dual-boot along side of XP.  Sorry about the confusion.  I am quite ready to leave the Windows world forever and ubuntu is definitely a great 1st step.

Last question (for now anyway...), for my backups, currently I just take a weekly full image backup of my hardrive using Macrium Reflect under XP.  It runs while XP is active, so I just disable my network connection to prevent any traffic. Only takes a couple of hours & since everything is XML, I can easily restore everything or anything.  Once I get everything under ubuntu as host OS & XP as guest, not sure that will work as most of the disk imaging products I've read about require un-mounting the partitions you want to image.  Any recommendations here?

Thanks again guys!

---

### Post by Bucky Ball on 2011-01-07
Your partitioning ideas are sound. Go for that. The way to do it. ;)

Don't forget, as you are not using Windows you don't need any NTFS data partition so you could in fact make /home as big as you like with the /swap partition at the end. /home has default folders for vid, music, documents, downloads, etc. And then just make them all EXT4 partitions. Or stick to your plan and make them all EXT4 anyhow.

If you are going to want to network with Windows machines you might be wise to stick with your plan and make the data partition NTFS. Windows can see that, not EXT4 partitions natively (although there is apparently software to coax Windows into playing with EXT4). 

I would go for 10.04 LTS but if you want to do some tweaking 10.10. That may of course work faultlessly on your machine. Hard to know until you try. Try running it off the LiveCD first.

ps: if a disk is unmounted it is not active so not sure how you would image that. :-k

---

### Post by fwlii on 2011-01-07
Thanks Bucky Ball!  I have 2 laptops on my home network running Vista, but don't see a need to share anything from ubuntu with them.  My main shares are on a 250gb USB drive connected to the Compaq (with music, pics, vids, etc.), so Samba was easy to set up & my Vista laptops can get to anything they need.  Sounds like the hot setup is to, as you suggest, give /home the balance of the storage.  Both XP & ubuntu are now backed-up, so off we go...

Many thanks again!

---

### Post by Bucky Ball on 2011-01-07
Beautiful. Get into it. 

When you get to the partitioning sectioning go for manual and set up those three partitions and you're cookin'. You'll find /, /home, and /swap as default partition names in there so piece of p**s. ;)

---

