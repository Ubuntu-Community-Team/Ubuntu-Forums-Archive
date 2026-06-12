---
title: "Home Directory Help"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Socratez on 2010-05-07
I am wondering if I can get some clarification on something from a guru. First some background ... I have been a long time *NIX user and since day one it was suggested to me that I keep my /home on it's own partition. Now the thing is I have ALWAYS kept all the data on there. I've gone from Solaris to Redhat to SuSE to Ubuntu over the last 10 years and I still have the same original partition I created from day 1. My question is I am not sure which .xxxx files are relevant anymore e.g. .bashrc .xsession etc . Which ones are for which OS / Distribution and I wanted to clean this up without having to archive the entire disk and reformat. Can anybody tell me a good method for finding which of these files are obsolete? I have a pretty good idea what I am doing however this is something I've never had a good understanding of. 

Much appreciation in advance for the help. Thanks


Soc

---

### Post by jbrown96 on 2010-05-07
A ```
ls -alht ~/
``` would help a lot. That will sort by access date. All the config files in /home will automatically recreate by applications that need them. You can archive some of it somewhere else and see what settings are missing. 

.bashrc is your bash profile and you will want to keep that, assuming you use bash.
I don't have a .xsession anymore, and something like that would be dynmaically created. 

.dmrc is one of the more important files, and you get nasty error message on graphical login if it is missing or has altered permissions.

---

### Post by Socratez on 2010-05-07
Thanks what I was going to do is tar them all into an archive and then reboot the machine to run level 3 and login to see which ones are recreated. Then replace those with the previous ones in the archive. I am just uncertain if the system will hurl an error at me if I do. I don't want to do anything that is unrecoverable.

---

### Post by jbrown96 on 2010-05-07
You should be fine, but may have problems with graphical login if .dmrc doesn't exist (with proper permissions). I find keeping .bashrc is helpful if you have made changes and .bash_history is nice if you frequently use the same commands, but neither is necessary. 

There shouldn't be any need to go to level 3 either. Most of those files won't get recreated until a graphical login is done. Though, I am assuming that this machine uses X.

---

### Post by Socratez on 2010-05-07
Ok thanks a million. I'll do this and see what the results look like. It seemed crazy to me to see some of these 9 and 10 year old files. I never quite wrapped my head around the profile files for some reason.

One further question. If there are multiple users will the .dmrc file be a problem. Obviously I'll take your advice but I am just curious so I have a good overview of this for the future and on other machines.

---

### Post by jbrown96 on 2010-05-07
Each user has his/her own .dmrc that needs to be there. It's funny I've never looked at the file, but it's really simple > [Desktop]
Session=default just make sure it's owned by that user and permission 600. 

It's not really that big of an issue, but I don't on Gnome it throws up an error that won't let you log in. Just drop to a console and chmod it fixes it most of the time.
I've only ever seen problems when people will chmod -R 777 ~/ or something dumb like that. If it's not there, it will probably just be recreated. 

You shouldn't have any problems removing any files in /home, but there may be settings that you want to keep. I'd be pissed if I lost my Amarok music ratings (stored in .kde/share/apps/amarok).

---

### Post by dino99 on 2010-05-07
in such case, i think you may need to use fsck and dpkg to fight against hidden troubles, then make some room with gconf-cleaner , bleachbit, gtkorphan. Of course you may hardly thing about daily or weekly backups.

Time to time its good to reinstall from scratch as the last distro have left behind some mechanics (hal/udev, ext2/ext3/ext4, ...), try partedmagic

---

