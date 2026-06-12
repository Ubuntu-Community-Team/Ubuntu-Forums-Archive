---
title: "Multibooting and importing settings from /home."
date: 2011-11-15
forum: Installation &amp; Upgrades
---

### Post by Dry Lips on 2011-11-15
I've been multibooting a lot lately, but I've never imported the settings from my default /home partition before. Basically I need a few questions answered from people more experienced than me...
 

 **1.** Is it possible to use share the /home partition between different active operative systems? Will I mess things up if I have several different OS with different programs installed sharing the same /home partition? I've seen the option of importing settings from another OS installed, is “importing settings” the same thing as essentially sharing an existing /home partition, or does it simply just copy a few settings without otherwise touching the existing user account.  
 

 **2.** Is it possible to import the settings from my /home partition across DE's? At the moment my dedicated home partition is used for an installation of Ubuntu 11.04 running gnome2, can I import the settings from the /home partition if I run a distro that uses KDE or Xfce? 



Cheers,
Dry Lips

---

### Post by Dry Lips on 2011-11-16
Ok, let me ask another question then...
 I've got a separate partition for home:
 
 partition 1     ******/** Ubuntu ***11.04***
 partition 2   ******  /** + **/**home another distro
 **partition 3   /home for Ubuntu* 11.04***
 partiton 4         **/** + **/**home for yet another distro
 
My question is: If I replace Ubuntu 11.04 on partion 1 with for instance X/Kubuntu, 
Mint, or possibly Debian, would the content of the old /home partition become 
overwritten if I assigned /home to partion 3. What kind of information would be kept,
 and what would disappear in the process?

---

### Post by oldfred on 2011-11-16
You do not want to share /home. Some applications may be the same but different versions and cause conflicts. The separate /home is to make it somewhat easier to upgrade as you do not have to backup & reinstall /home (but you still need backups) when you do a clean new install. Software is designed for upgrades so old config files will get upgraded, but an old version may have setting issues with a new version.

But you can share data, so many of us use separate data partitions. Depending on systems, even separate data partition can have ownership and permissions issues but that is a lot less that the potential issues of a shared /home.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by Dry Lips on 2011-11-16
**oldfred**, as usual your posts are immensely useful. This is all I wanted to know &#8211; and more. 
Thanks a lot for your detailed and comprehensive reply! As and aside note, I just wanted to 
let you know that more than half a year ago you provided some instruction in [another thread]("http://ubuntuforums.org/showpost.php?p=10548942&postcount=22") 
of mine that since has prevented disaster at least a couple of times. A well deserved KDE star 
is coming your way:  :KS

---

### Post by oldfred on 2011-11-16
Glad I could help.:)

---

### Post by gordintoronto on 2011-11-16
> **Dry Lips said:**
> Ok, let me ask another question then...
 I've got a separate partition for home:
 
 partition 1     ******/** Ubuntu ***11.04***
 partition 2   ******  /** + **/**home another distro
 **partition 3   /home for Ubuntu* 11.04***
 partiton 4         **/** + **/**home for yet another distro
 
My question is: If I replace Ubuntu 11.04 on partion 1 with for instance X/Kubuntu, 
Mint, or possibly Debian, would the content of the old /home partition become 
overwritten if I assigned /home to partion 3. What kind of information would be kept,
 and what would disappear in the process?

When you install a new version or "similar" distro, you can specify what to do about /home. For example, if you installed Kubuntu 11.10 where Ubuntu 11.04 currently resides, you could specify to mount partition 3 as /home, and do not format it. I've done this several times without losing any data.

But make sure you have excellent backup, because there's a moment when you're one bad click away from losing everything.

---

### Post by Dry Lips on 2011-11-17
> **gordintoronto said:**
> When you install a new version or "similar" distro, you can specify what to do about /home. For example, if you installed Kubuntu 11.10 where Ubuntu 11.04 currently resides, you could specify to mount partition 3 as /home, and do not format it. I've done this several times without losing any data.

But make sure you have excellent backup, because there's a moment when you're one bad click away from losing everything.

So... Do you think Debian/KDE is similar enough to Ubuntu 11.04 (gnome2)?

---

### Post by gordintoronto on 2011-11-17
I don't know. Probably, but I don't know.

I tend to think of any distro which uses .deb files as "similar." However, I've been wrong before.

---

