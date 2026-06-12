---
title: "Accessing disc space and adding an additional data storage HDD"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by cygnus-X1 on 2010-02-27
I've been working on putting together my "dream machine" (ie - no windows) and have run into a problem. (And will probably run into another one when I go to add an additional internal HDD.)

To start with, here's the configuration:

```
  [COLOR="White"]-[/COLOR]

/dev/sda1   Primary [GRUB - Chainloader]
/dev/sda2   Extended
/dev/sda5   swap
/dev/sda6   8.04(32)
/dev/sda7   8.04(64)
/dev/sda8   9.04(32)
/dev/sda9   9.04(64)
/dev/sda10 10.04(32)future install
/dev/sda11 10.04(64)future install
/dev/sda12 /media/data (balance of disk space, approx. 60GB)
```{The above follows advice from other threads here and forums elsewhere.}

Booting and logging on to each OS is no problem! Updates work flawlessly! The /media/data {/dev/sda12} is automatically mounted when each OS boots. Here's the problem:

Nothing can be stored or written there. The partition was created and formatted by Gparted during the set up process, and was selected and chosen during the manual partition loading during the installation. All partitions were formatted to ext3. Right-clicking properties says that it can't determine permissions, but right-clicking anywhere in its window when opened says that the Owner and Group are "root".

Question #1: How do I easily make that partition accessible to all OS's and all users for data storage and retrieval by any on-board OS? 

Question #2: How do I set up the additional HDD so that this is also available to all on-board OS's & all users as well, in a simple fashion?

Many thanks in advance!
[COLOR="White"]-[/COLOR]

---

### Post by cygnus-X1 on 2010-02-28
Kind bump and plea for help. [-o<

---

### Post by oldfred on 2010-02-28
Are you mounting the partitions with fstab and giving correct ownership and permissions?

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)


With multiple operating system you want the separate data partitions. This site has info on setting them up and usiing them, which basically I followed.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

i have explained how I did it like painless (and comments) above:
oldfred's versions
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
[http://ubuntuforums.org/showthread.php?t=1411482](http://ubuntuforums.org/showthread.php?t=1411482)
[http://ubuntuforums.org/showthread.php?t=1410256](http://ubuntuforums.org/showthread.php?t=1410256)

---

### Post by cygnus-X1 on 2010-03-01
Wow! Looks like I have some more reading to do!

I just stumbled across the fstab thread earlier today and wondered if that had anything to do with it.  #-o

I'm not real sure, with all of the various things I've read so far, but I think either bodhi.zazen, herman546, or somewhere else said that the /media/data could be used like an "additional HDD" that could be accessed by all OS's. (I've been all over the place in order to get this running! :biggrin: )

BTW - I do have a physical HDD (320GB) I am putting in so that all OS's can access that as well. I figure the thorough info you gave covers that, too. After I get done reading and implementing. I'll post results and go from there. 

Thanks for the help!
[COLOR="White"]-[/COLOR]

---

### Post by oldfred on 2010-03-01
I did as much as I could from the command line so I could save my history. Then I plan on converting my history to a bash file so for Lucid all I will have to do is run the bash file to link everything in. If you have a lot of operating systems I would suggest the same thing.

---

