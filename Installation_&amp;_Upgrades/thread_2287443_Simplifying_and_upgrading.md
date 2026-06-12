---
title: "Simplifying and upgrading?"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by raen on 2015-07-19
I'm currently running Ubuntu 12.04 LTS. When I first set up, I was a bit manic and giddy because I had a brand-new computer with lots of RAM and hard drive capacity, and so I installed a rather large number of DEs (so I could see what they were all about, have some variety, etc.). That wouldn't have been quite so bad if I hadn't gotten it into my head to re-organize the shortcuts using Main Menu (partly because now I have multiple programs that all do pretty much the same thing: different terminals, different calculators, different screenshot apps, different simple text editors, etc.). I only ended up making an even bigger mess (because it turned out to be a huge job and I gave up halfway through) and it's a little ridiculous. And some DEs share the menu edits/desktop backgrounds and some don't. I've overly complicated things unnecessarily, and now I regret it. GNOME Classic is really all I need (aside from a minimal infusion of KDE because of a program I have that requires it).

There is a "revert" option in Main Menu, but the irrational paranoid part of my brain insists that if I click that, my menus will revert to pristine factory settings and not include any programs I've installed since then.

I want to start over with the current version, but I don't want to do a clean re-install if I can avoid it. I do have my system and my files in two separate partitions. (I'm also dual-booting with Windows, which is on an entirely separate hard drive.)

I understand this will likely be a multi-step process. Where do I begin? What is the best way to go about doing this? (And if I must do a clean re-install, I can live with that.)

Thank you.

---

### Post by sudodus on 2015-07-19
It is probably easier and faster to do a clean re-install, if you want a clean system.

It should be possible to remove the 'doublet programs' that you are not using, but may actually take longer time, because in some cases it can cause problems, that take time to solve.

Of course, in both cases it is important to make a ***backup*** of all your personal files, maybe also settings (in the hidden files of your home directory). You can also make a list of added program packages, that you want to re-install in the new system.

---

### Post by raen on 2015-07-19
Yeah, it's doing the backups that makes a clean installation my second choice. I've done clean installs before. They always come with a side of anxiety.

---

### Post by sudodus on 2015-07-20
But you need the backups anyway. The HDD can be damaged any time (and without a warning).

---

### Post by raen on 2015-07-20
That's true. I'm prepping for the big backup right now. (And yes, I know I should do regular backups, but I'm lazy.)

I don't usually bother with backing up settings, and I usually just manually make a list of the programs I have. Is there a more automated way to do this that will produce human-meaningful output?

---

### Post by sudodus on 2015-07-20
I think a manual list of programs works well. If you forget a package, it is easy to install a program when you need it, and you will probably not need all the programs that you installed in the previous installed system.

---

### Post by vasa1 on 2015-07-20
> **raen said:**
>  ... (aside from a minimal infusion of KDE because of a program I have that requires it).
...
Mind sharing the name of the program?

---

### Post by oldfred on 2015-07-20
I use rsync to backup and include some other documentation like bootinfoscript which shows partitions and which boot loader is in which drive.
All your user settings are in /home. If you made some system settings like grub menus, NFS, or networking you may have settings in /etc. I try to remember to just manually copy those files into /home so my backup of /home covers everything I need. 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

In links above is the export of installed apps. It is a long list as it includes all the default apps and dependencies. But only those not already installed will be installed when you reinstall them from list.
       
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

   and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

