---
title: "Fresh installation - what about the home directory and programs?"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by evillan on 2008-09-24
Due to some problems I've had with a program, I want to install 8.04 again (currently running 8.04). 

What will happen to my home directory, the programs I've installed and my settings? Is there any way to export them to the fresh installation?

---

### Post by Herman on 2008-09-24
You should make a backup of your /home/username directory, and a backup of /var/cache/apt/archives/ so that you can restore everything again later.

Your /home/username directory will contain your regular files and directories plus some hidden files and directories. The hidden files and directories contain your settings. They can be seen by typing 'ls -a' in a terminal, or in GUI mode, just click 'Places'-->'Home Folder', and then 'View'-->'Show Hidden Files'. If you take a look around inside some of those hidden files you'll find things like addressbook,  calendar,  mail,  memos, and   tasks in .evolution/ , which you can copy into the same directory in your new installation to restore Evolution with. Or you can use the import/export wizard.
There should be a hidden directory for most of the programs you had installed.
The settings for other programs can be backed up and restored in a similar fashion. 

You can copy contents of your /var/cache/apt/archives/ backup to your new /var/cache/apt/archives/ directory before you start re-installing all of your software, (installed programs), that way you won't have to wait while you re-download them from the internet, they'll already be there. That saves a lot of time and some bandwidth too.

Other files you may want to back up might be /boot/grub/menu.lst if you had yours customized and personalized, /etc/apt/sources.list if yours had special repositories in it and any other files. Care should be taken restoring those, unless you know what you're doing, (just in case your new installation has a different partitiion number or something), you may only want to restore certian lines from those kind of files.

There are some excellent programs like sbackup and srestore which can make this job easier for you if you want to try them out. Look for them in 'Applications'-->'Add/Remove' or in 'System'--'Administration'-->'Synaptic Package Manager', or use apt-get to install them.

The most important thing is to always have a backup of at least our most important files on some other media, and not in the same hard disk as the installation we have the original installation in.

Regards, Herman

---

### Post by evillan on 2008-09-24
About /var/cache/apt/archives/:
I've used ubuntu since 7.04 and have a lot of programs installed, a lot of them are not present in that directory. It's only about 20 of my most recently installed programs/files (and the majority is installed through "aptitude safe-upgrade"). 

I've now made a back up of my home directory. Should have done it anyway...

---

### Post by Herman on 2008-09-25
> About /var/cache/apt/archives/:
I've used ubuntu since 7.04 and have a lot of programs installed, a lot of them are not present in that directory. It's only about 20 of my most recently installed programs/files (and the majority is installed through "aptitude safe-upgrade").If you have usd the command 'apt-get clean', that would have deleted them all. Other than that' I don't know why your /var/cache/apt/archives directory wouldn't contain the .deb files for your installed or updates software. Nevermind, it's no biggie, it's just that is will take you a little bit longer while they re-download, that's all. :)

EDIT: I don't know what 'aptitude safe-upgrade' does, maybe that deletes your /var/cache/apt/archives/*.deb files. I don't know.

---

### Post by ronnielsen1 on 2008-09-25
> You should make a backup of your /home/username directory, and a backup of /var/cache/apt/archives/ so that you can restore everything again later.
Are there any plans to make this easier? Mepis has a checkbox where you can save /home and it works great (even if /home is on the same partition) or is this a Mepis patented thing?

Not cutting Ubuntu down at all. Ubuntu has tools that Mepis doesn't. It would be nice if a distro could have all of the toys.

---

