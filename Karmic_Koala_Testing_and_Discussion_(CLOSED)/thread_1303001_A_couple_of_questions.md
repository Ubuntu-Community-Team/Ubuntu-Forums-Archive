---
title: "A couple of questions"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phillw on 2009-10-27
Please bear with me, I know most of these questions will have been asked before - I'd just like to 'get it straight' in my own head.

I'm running 9.04. I am 'breaking' the rules for a server by having the install as my desktop system also (full GUI, browsing etc)

I have a full LAMP installation, and Mail-Server. I have 3 web-sites on my server These are all used for both my learning stuff & as the local test-beds for stuff before I upload it to my Host Provider.


[LIST]
[*]I've read a couple of threads & looked at the last 'bug' reports regarding auto-mounting & mounting CD/DVD media - It seems to be an outstanding issue for some.
[/LIST]

[LIST]
[*]For an update for a LAMP + mail server, will this work [http://www.unixnewbie.org/how-to-upgrade-to-ubuntu-910/](http://www.unixnewbie.org/how-to-upgrade-to-ubuntu-910/)   ?
[/LIST]
I intend to take a full backup of my system. My usual back-up script is this ...

```

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/mnt --exclude=/sys --exclude=/home/phillw/Desktop/PhillzMuzic --exclude=/dev / 

```
I'm still not too sure about either including or excluding /dev is the preferred / recommended way.

As you can see, I have a windows partition mounted as both media & as a shortcut - hence the excludes for them both.

I'm going to be following this post to get a list of all the 'stuff' I've added (like Ipod support, Bluefish editor etc..)

[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Whilst I'm fairly comfortable at command line, etc - I've never done anything like this before.

I need to have a snapshot, in case things go horribly wrong - Is the above enough for me to re-build ?

I also understand that even tho' ext4 is default in 9.10, I'll still be on ext3 for all existing files.
Once the dust has settled, will the above backup script be okay for me to backup, re-format to ext4 and 'spit' everything back on using the command 

 ```
 tar xvpfz backup.tgz -C /  
```

Soz for sounding like noob on this one - but I am !!!

Regards,

Phill.

---

