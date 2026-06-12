---
title: "install partitioning problems"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by gympiebrowns on 2007-10-11
gday, well im trying to make the break from windows and have been  trying for days to install ubuntu 7.04 on to my old puter, everything goes fine except for when it gets to the partitioning section of the install, i let ubuntu do the partitioning (btw its a formated hd, clean install) and i get this message and it hangs at 5%:

failed to create a file system.
the ext3 file system creation in partition #1 of ide slave (Hdb) failed.

i would appreciate any advice to get this baby purring, the puter is a:

P4 2ghz 256mb ram (to be upgraded tday) 40gig hd (formated) 32mb nvidia tnt video card and an asus P4s533-x mb.

thanks again

---

### Post by phr0ze on 2007-10-11
Are you choosing the option to 'Use entire Disk'?

---

### Post by Pumalite on 2007-10-11
256 MB RAM or less> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
You could boot the Live CD, but you'd need 500 MB /swap ahead of time and if installed, system would be too slow in your system.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by gympiebrowns on 2007-10-11
> **phr0ze said:**
> Are you choosing the option to 'Use entire Disk'?

yes i was using whole disk, when i went to the manual option, just plain got all confused lol....

---

### Post by Pumalite on 2007-10-11
Now that you upgraded your memory.
If Vista, use Vista partitioner
If XP, use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to 'shrink' XP partition.
Then a good scheme is:
10 GB for '/'
1 gb for /swap
The rest for /home

---

### Post by gympiebrowns on 2007-10-11
> **Pumalite said:**
> Now that you upgraded your memory.
If Vista, use Vista partitioner
If XP, use Gparted:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to 'shrink' XP partition.
Then a good scheme is:
10 GB for '/'
1 gb for /swap
The rest for /home

the drive has no OS on it anymore, does that mean i should put xp back on and dual boot it???, using the manual setup of partitions in ubuntu is that where i type in: 

'/'
1 gb for [COLOR="Red"]/swap[/COLOR]
The rest for [COLOR="red"]/home[/COLOR][/QUOTE]

what gets typed in the /QUOTE SECTION AS ABOVE

---

### Post by phr0ze on 2007-10-12
Thats it. the '/' is root. Think of it as your OS and Programs. Think of /home like your My Documents.  The sizes look good considering the size of your HD.

Go for it.

---

### Post by gympiebrowns on 2007-10-12
> **phr0ze said:**
> Thats it. the '/' is root. Think of it as your OS and Programs. Think of /home like your My Documents.  The sizes look good considering the size of your HD.

Go for it.

guys really sorry about all the questions, let me get this right in that i type the above commands into the manual partition window???

anywho many many thanks for all the help and sorry about the probable n00b questions lol

---

### Post by Pumalite on 2007-10-12
Get Gparted as I told you before. Boot from it. Make partitions on your drive:
10 GB for '/' ('/' is the mount point)
2x RAM up 1 GB for /swap
The rest for /home
Then install and use the partitions you made.

---

