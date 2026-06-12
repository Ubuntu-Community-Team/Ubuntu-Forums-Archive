---
title: "Multiple Distros, one /home"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by KdotJ on 2010-09-12
Ok, so I know it's possible to to have multiple distros on one hard disk, and set it up so you can just have one /home partition and use it for all of the distros on that system. My question is, how efficient is that? Does it bloat the /home out with a whole bunch of stuff that might slow a particular distro down because it's filled with stuff from another? (I.e configs). And let's say I have two distros that are of different bases, say ubuntu and arch, does this make a difference? I know obviously that my personal files will all be accessible and not matter which distro they are being read from, but I'm talking more about the hidden stuff. 

Thanks in advance

---

### Post by clrg on 2010-09-12
I've never tried that, but I guess it *could* lead to configuration conflicts, for example, if one Gnome installation writes something in a config file shared with another Gnome installation which the latter doesn't recognize. 

I guess the only way to find out is to try it. However, I think it'll lead to unforeseen conflicts.

Your "normal" files and folders should be fine, as long as you make sure you use the same UID and GID for your user on all distros (check /etc/passwd).

---

### Post by KdotJ on 2010-09-12
Yeah that was my guess too :( 
I have already had a go at this in a VM with Fedora and Debian, which are of course of different bases. It does work, both distros using gnome. But I haven't tested it extensively with changing settings etc, and of course this will be different in a 'real' life usage scenario. I'll check it out some more though, because it will be a pain having multiple /homes, I guess I could have a small partition as Fat32 and just back up my 'normal' files to it, then i can access them from each distro

---

### Post by ronnielsen1 on 2010-09-12
If you do slight modifications of your name you won't have the config issues. You only have one home but for Ubuntu you can use /home/ubuntu and for parsix - /home/parsix (examples only) You will still have access to all of your files under the other distros. Say you're in Parsix and you want access to music files in Ubuntu - create a link on your desktop to /home/ubuntu/music

---

### Post by KdotJ on 2010-09-12
That's a good point, so the /home folder (partition) will then have two folders in it... One for each of the users (me but different names)??

---

### Post by clrg on 2010-09-12
Exactly. Just create different user names for each distro.

---

### Post by KdotJ on 2010-09-12
Good thinking people, thanks! Now I just need to think of an alias haha... 

Marking as sovled

---

### Post by oldfred on 2010-09-12
Many of us use /data partitions and mount or link the /data partition into each install. Then the /home remains within each install (or can be a separate partition) and /home is relatively small. My /home when it was a separate partition was only about 1GB of hidden files & folders. I was aggressive about moving any program's data that saved lots of data into my /data partition.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

