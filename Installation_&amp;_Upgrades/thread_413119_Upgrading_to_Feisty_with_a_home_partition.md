---
title: "Upgrading to Feisty with a /home partition"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by me1on on 2007-04-18
When I installed Edgy, I created a separate /home partition. What is the preferred way to upgrade to Feisty if I already have a /home partition? Should I install from the CD, formatting everything except the /home partition? What are the advantages/disadvantages of installing using this method?

---

### Post by mexlinux on 2007-04-18
I always do clean installs, and I have always used a separated /home partition
The benefits are of course that you can keep all your files and configurations (but back up anyway!).

When I installed Edgy over Dapper, the Edgy installer had an option to chice which partitions to format, so the Feisty should have the same.

I do not see any disadvantage in have a separated partition for the /home

---

### Post by Ken T on 2007-04-18
For the uninitiated, can you please explain to me the difference between a clean install and one which is not? I wonder if a "clean install" is the standard install, presumably off the CD, and an "unclean" one is a custom install. Thanks, K

---

### Post by me1on on 2007-04-18
Alright, thanks.  Just had to make sure that's what I was supposed to do. :) 

> **Ken T said:**
> For the uninitiated, can you please explain to me the difference between a clean install and one which is not? I wonder if a "clean install" is the standard install, presumably off the CD, and an "unclean" one is a custom install. Thanks, K

Usually by "clean install" people mean installing from the CD. This will wipe your root ("/") partition. If you have a /home partition, you can choose not to format it, leaving all your files and user-specific settings intact. It will still wipe everything else out though, such as the programs you've installed and global configuration files. I like doing clean installs because if I've messed anything up, it will be fixed when Ubuntu is reinstalled.

An "unclean" install would be just using the upgrade manager to upgrade to Feisty. This keeps all your files, setting, and installed programs untouched (although many of your programs will be updated), but sometimes (not often, but occasionally) it can cause problems, especially if you don't know what you're doing.

Somebody correct me if I'm wrong.

---

### Post by rs8000 on 2007-04-19
Questions on leaving your /home intact during a fresh install of Feisty from Edgy?

1. What is the impact on your app config hidden folders? What if the app version in Feisty is newer, can the config structure be different? What will happen to my Thunderbird messages for example? 

2. If I had an app previously that is not on the Fesity default install, and then go to install it again after Feisty is loaded, will it overwrite the config files?

3. During the install do I create a user with the same name as my previous user? If so, will this not overwrite the /home/username folder?

---

### Post by Gwystyl on 2007-04-19
> **rs8000 said:**
> Questions on leaving your /home intact during a fresh install of Feisty from Edgy?

1. What is the impact on your app config hidden folders? What if the app version in Feisty is newer, can the config structure be different? What will happen to my Thunderbird messages for example? 

2. If I had an app previously that is not on the Fesity default install, and then go to install it again after Feisty is loaded, will it overwrite the config files?

3. During the install do I create a user with the same name as my previous user? If so, will this not overwrite the /home/username folder?

1. I noticed that Thunderbird 2 RC1 uses /home/<user>/.thunderbird in stead of /home/<user>/.mozillathunderbird. Took me a while though :). Smartest thing is to backup your old profile, install the new Thunderbird (or other app), find out where that version keeps it's settings and put back your old profile over the new one (maybe it's wise to backup the new profile before you do that?). Apart from finding the new profile dir I had no trouble with Thunderbird though.

2. If the config dir isn't changed, it usually will use your old settings or prompt if they are replaced by 'fresh' ones. You can see what config dirs you have by selecting 'show hidden files' in your homedir in Nautilus or Konqueror

3. I tried that a few times now, and it works like a charm. This is actually the main reason I keep my /home on a different partition. Wouldn't be much use if you save your settings and don't use them afterwards? I'm not shure, but I guess /home is empty when you'd do a clean install including cleaning /home. Of course, Gnome or KDE will put it's settings there as soon as you boot up the first time, but here again I think it will use your old settings in stead of replacing them by a fresh set.

---

