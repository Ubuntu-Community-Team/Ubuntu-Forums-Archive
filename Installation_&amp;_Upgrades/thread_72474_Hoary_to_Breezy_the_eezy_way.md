---
title: "Hoary to Breezy the eezy way?"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by alfotis on 2005-10-06
Hi all,

Is it possible to change add a repository in my /etc/apt/sources.list that contains the breezy packages and update my hoary distro to breezy without ANY problem? 

I tried it, but the update tool told me something that not all packages can be updated (followed by a LONG list), so i thought that i'd have a lot of conflicts and quit. 

Has anybody tried this? Is anyone sure that i won't have problems? Any tips?

---

### Post by Dr. Nick on 2005-10-06
You can do it, its documented somewhere on here. I assume you opened sources.list and changed all hoary to breey? After that you must open a terminal and type sudo apt-get update, followed by sudo apt-get dist-upgrade.

I cant guarntee you wont have any problems as Breezy is still not "stable", but I and many others have been fine, though if you read these forums you will see that some people had problems, so if you decide to take the plunge , backup your data and make sure you have access to internet by other means than you current hoary in case you have problems and need to lookup up help.

Tips? Some reccomend you close Xorg and do it from a single user mode 
In a terminal type "sudo init 1" it is I believe or "sudo init 3" then the apt-get commands.

Good luck

---

### Post by alfotis on 2005-10-06
Ok, thanks

I'll try to partimage my hdd, so in case anything goes wrong, i won't have to format->configure and all these stuff for days (oracle db, mysql db, php, apache etc), wait for breezy to go stable, update and write my comments.

Thanks.

---

### Post by landotter on 2005-10-06
I did it via Synaptic's gui, removed backports, then changed all instances of hoary to breezy, then did an upgrade. Choose "smart" upgrade when it prompts you. This can take hours, so best to just walk away for a while and don't stress.

My Xserver config broke, so I had to edit xorg.conf with nano to fix, which is really really easy, if you're capable of reading a text file and reading the comments. I just had to remove the "videoram=" section, then a "startx" and all was good.

---

### Post by Dr. Nick on 2005-10-06
Yeah some of the problems are easy to fix, but if I had all them servers to reconfigure I think I would wait for stable, and even then back up all the config files :), I mean WOW talk about some time to configure if it failed. Well when you decide to upgrade, Good Luck, Breezy has some nice features,  I hope you dont lose any of that config in the process.

---

### Post by landotter on 2005-10-06
Was worth the risk to me, as I'd done a lot of customisation, and plenty of installed source apps in /usr/local. It's not like XP where you don't have a separate /home partition by default and a reinstall borks everything. :P

---

### Post by Dr. Nick on 2005-10-06
Dont get me wrong, I did it too :) , plus I dont have a seperate home partition, I forget why but at the time it seemed like a good idea to only have 1 partition for linux :confused:  Anyway I do have a seperate fat32 partition so I can share between linux and XP so all my important files get backed up to that aswell so worse case scenario of a failed upgrade would only lose my configuration not my data, I havent had a failed upgrade though that I couldnt recover from using the  comand line :o

---

### Post by GTvulse on 2005-10-06
If there is no independent /home partition, you can back up your home directory to an existing  FAT32 partiton, as long as you don't let the actual files touch it, like this:
```

cd /home
tar cjf /path/to/FAT32/dir/my_home_directory.tar.bz2 my_home_directory

```
If for some reason you botch your home directory during the dist-upgrade to Breezy, you can recover your data by doing a simple:
```

cd /home
tar xjf /path/to/FAT32/dir/my_home_directory.tar.bz2 

```

---

### Post by alfotis on 2005-10-07
Do you think partimage (in order to preserve ALL configuration and not Copy/Paste) later wouldn't do? Has anyone faced any problems with partimage?

---

### Post by randlieb on 2005-10-14
> My Xserver config broke, so I had to edit xorg.conf with nano to fix, which is really really easy, if you're capable of reading a text file and reading the comments. I just had to remove the "videoram=" section, then a "startx" and all was good.

could you give more details of how you fixed the broken xserver? that looks to be my hangup from getting in to the breezy gui. step by step would be great as i am still working my way around this new (for me) linux terms.

thanks

---

### Post by landotter on 2005-10-15
[quote=randlieb]could you give more details of how you fixed the broken xserver? that looks to be my hangup from getting in to the breezy gui. step by step would be great as i am still working my way around this new (for me) linux terms.

thanks[/quote] 
Well I just opened the config file with:

$ sudo nano /etc/X11/xorg.conf

and poked around till I found the monitor subsection, I remembered from an install a long time ago that I had a problem with the "videoram" entry, so I edited the line out by putting an # in front of it. I then saved the file and typed:

$ startx

and it worked

alternately, this is probably easier:

$ sudo dpkg-reconfigure xserver-xorg

and you'll be guided through xserver configuration

BTW, I highly recommend installing Nano if you're a noob or just a lazy person like myself that doesn't want to learn Vi or Vim, it's a self explanatory little text editor.

---

