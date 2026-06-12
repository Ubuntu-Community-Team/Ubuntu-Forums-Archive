---
title: "I Stuffted up badly"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Liamkerrigan on 2007-08-18
hi there, im a complete nub to Ubuntu, i have never really tried it before and recently just got it up and running with dual booting windows xp and Ubuntu version 7. Ive had a little bit of a play with it and loved it, but today i was on there and  i went and was trying to install wine (another problem) but i clicked on desktop effects, it did some downloading and installing then i restarted it (as required) when i turned it back on everything stuffed up. something like x server (graphical interface) not correctly set-up.This isn't allowing me to log on at all. i really have no idea what i was and am completely lost. Is there some way of delete Ubuntu then re-installing it??? or fixing this problem!? ill post more info on it soon.. any idea greatly appreciated. :(:(:(:(:(:(:(:mad:

---

### Post by Liamkerrigan on 2007-08-18
Hello everyone, i know nothing about ubuntu i am trying to learn it, ive been using it for a few hours and i went and stuffed it up but clicking desktop effects, which made it download an update of some sort. then i restarted it as i was told, but on booting ubuntu back up nothing worked and there weere amlost two version of ubuntu (i am dual booting windows xp and ONLY ONE verions of ubuntu),  it comes up with strange screens and errors messages saying x server (graphical interface) not sett-up correctly i dont know, if there is any way to fix it, help gratly appriciated. If there is nothing i can do how can i delete ubuntu of my partitioned hard disk?? with out have to log onto ubuntu..?????? any help please i love ubuntu and need ot use it.:(:(

---

### Post by BoneKracker on 2007-08-18
Just reinstall like you did the first time.

Pay attention when you get to the partitioning, that's where you have the option to delete existing partitions (or use them again but format them).

You could also delete the partition(s) from within Windows or from the live CD.

---

### Post by Herman on 2007-08-18
Hello Liamkerrigan,
If you only had Ubuntu installed for a few hours and you didn't have any files yet that are precious you can probably fix it quicker by just re-installing, it will only take about half an hour or a bit more.

If you did have some files on there already that you might want to save you should be able to copy them to a USB drive or another computer with the Ubuntu Live CD. First you would boot your LiveCD with and 'mount' the partition to save the files from, like this, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").
You could then mount another partition in your computer and copy the files there  if you have another ext3 or a FAT32 partition.
If you have a USB drive you can plug it in and copy the files to that.
If you have another computer you can connect with network cables you can use SSH Networking to transfer any files you want to save, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").
Here is a web page that might help remind you about files you might want to save and tell you where you can find them, [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm") .

Then when you are ready you can just run the Ubuntu install CD again and pick the same Ubuntu partition as last time and choose manual partitioning and either delete the partition and make it again or at least re format the same partition for Ubuntu.

Unless you want to wait a while and see if someone comes along who knows something about 'System'-->'Preferences'-->'Desktop Effects'. I haven't tried that yet so I don't know what it is supposed to do much less how to fix whatever the problem is, sorry I'm not more help. I will look into it, but it will take me more than half an hour. You'd have Ubuntu up and running again by the time I'd be able to get back to you.

Regards, Herman :)

---

### Post by Nebby on 2007-08-18
Guessing you installed it from a Feisty disk, the second Ubuntu is probably a newer kernel, which would have been the update.

To fix it, can you log into command line? It's one of the options on the login page, or press Ctrl+Alt+F1. 

And if you really wanted to get rid of Ubuntu, you could do it from windows, you'd just need something to delete the partition Ubuntu's on, such as PartitionMagic.

Other than that, would it be possible for you to put the exact content of these strange screen and error messages?

---

