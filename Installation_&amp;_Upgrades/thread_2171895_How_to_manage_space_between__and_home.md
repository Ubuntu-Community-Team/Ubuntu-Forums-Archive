---
title: "How to manage space between / and /home"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by AAEIV on 2013-09-02
Hello to everyone!

I am running a dual boot system with windows vista and ubuntu 10.04.
Yesterday, I decided to re-install vista, but after that I wasn't able to boot in ubuntu, so I want to take the chance to upgrade to 12.04, and rearrange my HDD's partitions.

My plan is to split my 250 GB HDD as follows

[LIST]
[*]120 GB Vista
[*]50-60 GB NTFS storage partition, that will be used both in vista and ubuntu
[*]60-70 GB ubuntu
[/LIST]

I've decided to use 4GB swap(equal to my RAM), but I don't know how much space to give on / and /home.
I suppose that in rot directory /, all the programs are installed.

In ubuntu I use CERN's root, maybe a bit of LaTeX, I watch movies, browsing, pdf reading and stuff like that.

So, how to arrange  root directory and /home?
In addition, is there a way to create a root account while installing ubuntu?

Thank's a lot!

---

### Post by lukeiamyourfather on 2013-09-02
Ubuntu uses a different paradigm for administration, more like Windows and UAC instead of a traditional root account. You can enable the root account if you want just know what you're getting into.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What specifically do you want to know about setting up the partitions? Like, if it will work? Or a step by step guide?

---

### Post by newbie-user on 2013-09-02
At my work, I have full Ubuntu 12.04 installs, including necessary 3rd party software, crammed into as little as 4GB (accidentally). Home dirs are on an NFS server. It's not pretty and doesn't work well at all when doing updates with only 4GB.

If you want only / and /home partitions, I'd recommend at least 6GB for the / partition, as it doesn't look like you'll be installing much.

As for a root account during installation, the only way I've seen that done in Ubuntu is by preseeding.

---

### Post by vanadium on 2013-09-02
In your dual boot scenario, I would keep the Ubuntu root partition rather limited, at about 12 - 15 GB. This leaves plenty for the system (typical need: 6 GB) and for user configuration data in the home directory. User data can then be placed on the common ntfs data partition, where it is accessible from within both operating systems.

Data can easily appear to be available in your home directory by using symbolic links. Replace the Documents (Pictures, Videos, etc.) folder by a symbolic link to the relevant directory on you data partition, and you seamlessly can access these data from your home, just as if it all were physically there.

I would certainly not setup a separate /home partition in your case.

---

### Post by AAEIV on 2013-09-02
> **vanadium said:**
> Data can easily appear to be available in your home directory by using symbolic links. Replace the Documents (Pictures, Videos, etc.) folder by a symbolic link to the relevant directory on you data partition, and you seamlessly can access these data from your home, just as if it all were physically there.

I would certainly not setup a separate /home partition in your case.

Thank you very much!
How is it possible to use symbolic links(I don't even know what that is)?
How can I install ubuntu with only swap and / without /home ?

---

### Post by mastablasta on 2013-09-02
i have it all on / partition (well appart from /swap area). no /home, no problem :-)

---

### Post by AAEIV on 2013-09-02
How can I not add /home directory?
Where are the "Photos", "Music", "Downloads" etc directories going to be created?

I don't know how to add just swap and / ...

---

### Post by su:bhatta on 2013-09-02
If you do not create a separate /home then it will by default be created in the / partition only !

When you are installing choose your partition and select mount point as / that will do it.

/ is available from the same dropdown menu where you get /root, /home , etc..

It is not necessary to create two different partitions for /root and /home. If you choose mount point as / , then by default both /root and /home is created in the same partition.

---

### Post by AAEIV on 2013-09-02
But will I be able to use / without having to switch to root user?
For example, to save a document in /, like it's happening when using software like dropbox, copy, etc...

---

### Post by su:bhatta on 2013-09-02
If you choose mount point as / a default /home/user is also created where you get all the 'Documents', 'Music' etc personal folders. 
You dont have to be a root to access /home/user, where user is the user you created.

Dropbox folder is created in this /home/user directory . 

This can be used by the user created for all files etc.

---

### Post by oldfred on 2013-09-02
If not having the separate /home I would make / (root) a bit larger. I use 25GB for partition but my working install uses 9GB with lots installed, so it could easily be a partition of 12 to 15GB. But I like to have extra room and writing a DVD may use 4GB of tmp space so I want that also. 

My /home is 2GB of the 9GB total but most of that is .wine as I have the Windows version of Picasa. But I am aggressive about moving data to my data partitions. I move some hidden folders like Firefox & Thunderbird so I could share with my XP install. I do not now use XP but have not moved the data in my NTFS shared data partition to my Linux data partition.

---

### Post by su:bhatta on 2013-09-03
> **oldfred said:**
> If not having the separate /home I would make / (root) a bit larger. I use 25GB for partition but my working install uses 9GB with lots installed, so it could easily be a partition of 12 to 15GB. But I like to have extra room and writing a DVD may use 4GB of tmp space so I want that also. 

.

Definitely a good idea. And if you want to use programs like VirtualBox, you might make the / partition in ranges above 50Gb. 

The size of / partition depends on what all you want to keep in the personal folders, like how much Music or Movies also how much downloads you want to do.
Mostly 10-15Gb is sufficient for the basic Ubuntu Os, but add more depending upon how much stuff you want to put in your personal folders.

I've found that if I dont use VirtualBox then 20-30Gb is generally more than sufficient, if regularly the big files are moved to the Data partition!

I suppose you got it working. Play around, thats the best way to learn and develop your own tastes.

---

