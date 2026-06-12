---
title: "Best way to upgrade to latest Ubuntu (karmic)?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bluenix on 2009-10-04
Hi, I've been using ubuntu exclusively at home since hardy and could never complain. Pretty excited about the upcoming Karmic release, but there is an issue to be solved before I upgrade to 9.10.

My setup includes separate /boot, /, swap, and home partition. In the home partition I have couple hundred gigs of stuffs which I have no means to take backups. What I want to do is:


Retain the personal files and media in the /home/username folder, and retain the username AFTER I install 9.10.

AND, at the same time,

Get rid of all the config files, firefox profiles, desktop configs - pretty much anything that is not documents or media that I've saved. It's because I want to enjoy (at least for some time) the "default" setup of things before I start tweaking the system to my liking.


I can't think of any way I can do that, so any help or suggestion will be greatly appreciated. Thanks!

---

### Post by wilee-nilee on 2009-10-04
If you have no way of backing stuff up you might consider just downloading the Live CD to check it out, I would wait to upgrade when it is considered stable. I did a upgrade yesterday it took forever, 8 hours and then it was borked in several ways. The slow server situation probably is part of the variables among others that caused this to happen. As it is the upgrade installed on ext3 rather then the default ext4, but I had a earlier alpha that was ext4 and just did a fresh install, and it is running great. There also appears to be wireless problems among several users.

---

### Post by stlsaint on 2009-10-04
to do what you ask you can just a manual install the same way you setup all your different partitions thru the installern using the Livecd and instead of formating everything just do your (/) or in your case /boot with new files and do not format /home...then just reuse the same user name...now for firefox should you want to get rid of those i would think that thats something you must do manually. 

on the other side condsidering that this will be a new os i would recommend a fresh install and just make backups of everything...you can use the simple backup/restore suite in repos...may be a little more work than you want to do but with karmic having so many issues i would recommend it as fresh. but thats one opinion...please take in other points of views in this and if a backup is not possible (which is a whole other issue in itself) than consider my first option.

---

### Post by bluenix on 2009-10-04
> **wilee-nilee said:**
> If you have no way of backing stuff up you might consider just downloading the Live CD to check it out, I would wait to upgrade when it is considered stable. I did a upgrade yesterday it took forever, 8 hours and then it was borked in several ways. The slow server situation probably is part of the variables among others that caused this to happen. As it is the upgrade installed on ext3 rather then the default ext4, but I had a earlier alpha that was ext4 and just did a fresh install, and it is running great. There also appears to be wireless problems among several users.

Thanks, I was intending to do a fresh install myself. Not before the final release though.



> **stlsaint said:**
> to do what you ask you can just a manual install the same way you setup all your different partitions thru the installern using the Livecd and instead of formating everything just do your (/) or in your case /boot with new files and do not format /home...then just reuse the same user name...now for firefox should you want to get rid of those i would think that thats something you must do manually. 

on the other side condsidering that this will be a new os i would recommend a fresh install and just make backups of everything...you can use the simple backup/restore suite in repos...may be a little more work than you want to do but with karmic having so many issues i would recommend it as fresh. but thats one opinion...please take in other points of views in this and if a backup is not possible (which is a whole other issue in itself) than consider my first option.

I was thinking about your first option myself - that is, a fresh install without formatting the /home partition and reusing the same username - but wouldn't that spoil the Karmic default setup, like looks and other stuff?

Maybe I need to do a backup after all! :( :(

---

### Post by desmane on 2009-10-04
Hi!

a clean install (with home on a different partition) is a good choice for karmic, because you will have the full advantage of the new file system ext4. 
[U]
**I have a few questions, maybe others are interested too:**[/U]

1) I'd like to know though if I can just **backup my /etc and just restore that folder after clean install of karmic**. Does it make sense? How would you recommend to backup and restore that folder?

2) last time I did a clean install, all my **saved wireless connections were gone**. How to solve that?

3) How can I **reinstall all packages that are currently installed** over synaptic package manager? (and does it make sense also?)

4) Since I prefer the clean install this time, any **other suggestions** I should consider?

5) My Home Folder is already formated as ext4 - is it probably a "pre" release and not the actual ext4?? Should I backup those files and **create a new ext4 home partition** with karmics live cd first?

THANKS!!

---

