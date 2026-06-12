---
title: "Unable to find usb drives"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by David_Kroik on 2013-10-08
I recently installed ubunt 13.04 parallell with the windows. Now I notice problems with attaching a usb drive (a stick or an external hard drive). When I plug it in nothing happens, the drive won't show up among the other drives and partitions. However on my windows partitions the same usb drives in the same slots on the computer work just fine, leading me to the conclusion that there is something with my ubuntu partition and the usb drives not cooperating. I tried the 'lsusb' and indeed the drive pops up there (the specific line where the usb drive is located is in bold font):

david@david-To-be-filled-by-O-E-M:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
**Bus 002 Device 006: ID 0951:1643 Kingston Technology DataTraveler G3 4GB**
Bus 002 Device 004: ID 0e8f:0022 GreenAsia Inc. 
Bus 002 Device 005: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
david@david-To-be-filled-by-O-E-M:~$ 


Hope you can help me
David

---

### Post by heir4c on 2013-10-08
Boot back to windows and plug in the usb's you use. 
Before you remove them you must unmount the usb from Windows. In the Menubar (or whatever it's name is now, I don't know, I don't use Windows) you will find a usb icon. Click on it and safely remove the usb. Than you must not have any issue with them in Ubuntu. (I hope :))

---

### Post by sudodus on 2013-10-08
Welcome to the Ubuntu Forums :-)

There might be an issue with 13.04 and USB, that it will not automount unless you change the ownership and or permissions of the directory that will be host for the mount points. But it should be possible to mount the pendrive with superuser privileges. So we can try to solve the problem in steps. There might also be a problem 'with your ubuntu and the usb drives not cooperating'.

Please post the output of the following commands and put it within code tags (go advanced, mark the text and click on the # icon at the top of the editing window).

```
sudo parted -l
```
```
df
```
```
sudo ls -l /media
```

When I know the output of those commands, I can suggest how to try mounting with superuser privileges.

---

### Post by David_Kroik on 2013-10-09
Thank you!

I paste the code here:

```
david@david-To-be-filled-by-O-E-M:~$ sudo parted -l
[sudo] password for david: 
Modell: ATA KINGSTON SV300S3 (scsi)
Disk /dev/sda: 120GB
Sektorstorlek (logisk/fysisk): 512B/512B
Partitionstabell: msdos

Nummer  Början  ****    Storlek  Typ       Filsystem       Flaggor
 1      1049kB  106MB   105MB    primary   ntfs
 2      106MB   50,6GB  50,5GB   primary   ntfs            startbar
 3      50,6GB  120GB   69,4GB   extended
 6      50,6GB  116GB   65,3GB   logical   ext4
 5      116GB   120GB   4183MB   logical   linux-swap(v1)


Modell: ATA TOSHIBA DT01ACA0 (scsi)
Disk /dev/sdb: 500GB
Sektorstorlek (logisk/fysisk): 512B/4096B
Partitionstabell: msdos

Nummer  Början  ****   Storlek  Typ      Filsystem  Flaggor
 1      1049kB  157GB  157GB    primary  ntfs
 2      157GB   315GB  157GB    primary  ntfs
 3      315GB   500GB  186GB    primary  ntfs       startbar


david@david-To-be-filled-by-O-E-M:~$ 
```

next command:

```
david@david-To-be-filled-by-O-E-M:~$ df
Filsystem      1K-block   Använt Tillgängligt Anv% Monterat på
/dev/sda6      62603204 16883584     42532832  29% /
none                  4        0            4   0% /sys/fs/cgroup
udev            1961136        4      1961132   1% /dev
tmpfs            394136      904       393232   1% /run
none               5120        0         5120   0% /run/lock
none            1970672       80      1970592   1% /run/shm
none             102400       48       102352   1% /run/user
david@david-To-be-filled-by-O-E-M:~$ 

```

and the third one:

```
david@david-To-be-filled-by-O-E-M:~$ sudo ls -l /media
totalt 4
drwxr-x---+ 2 root root 4096 okt  9 20:05 david
```

I made sure the usb drive was attached when I did the commands.

Hope I got it all right with putting code in this post. 

Thank you again!

---

### Post by sudodus on 2013-10-10
Försök med det här kommandot, som gör monteringspunkten läsbar och exekverbar för alla användaridentiteter.

```
sudo chmod ugo+rx /media/david
```

Då bör det fungera med automatisk montering, och det ska gå att montera genom att välja enheten via den grafiska filutforskaren.

*Edit*: Toshiba USB-skivan (500 GB) syns på /dev/sdb men inte Kingston DataTraveler G3 (4GB). Var USB-stickan ansluten, när du körde kommandona?

---

### Post by David_Kroik on 2013-10-10
Ja, usb-stickan satt i när jag körde kommandona. Nu testade jag det senaste kommandot du skrev, men den hittar inte stickan. Jag provade att sätta i en extern hårddisk också, men den hittar inte den heller. Toshiba-disken är intern i datorn, ansluten via SATA om jag inte missminner mig.

*Edit* Det verkar som om usb-minnet hittas nu, men det tar väldigt lång tid. Efter att jag kom tillbaka till datorn efter cirka en halvtimme timme hade usb-minnet hittats.

---

### Post by ersatzsplatt on 2013-10-10
I'm very happy for you if you are able to understand better what is going on in (Dutch?) ... but it makes it difficult for me to try and help.  Could you translate, unless this issue is solved?  If it is solved, please mark it solved.

---

### Post by sudodus on 2013-10-11
> **ersatzsplatt said:**
> I'm very happy for you if you are able to understand better what is going on in (Dutch?) ... but it makes it difficult for me to try and help.  Could you translate, unless this issue is solved?  If it is solved, please mark it solved.

Sorry. I saw that the output of David's commands were in Swedish, so I replied in that language. I will continue this thread in English, but if you speak Platt, you should understand Swedish pretty well ;-)

---

### Post by sudodus on 2013-10-11
I know that some people have problems with 13.04 and some USB drives, that they are recognized extremely slowly. I think it is a bug, and I thought that it was fixed by an update (according to some other threads at the Ubuntu Forums). Is your system up to date?

```
 sudo apt-get update
```
```
 sudo apt-get dist-upgrade
```

Maybe that update solved the problem for some but not all USB drive models. I'll search for a thread describing similar issues...

---

### Post by sudodus on 2013-10-11
Look at this link in particular, describing a problem that was finally solved 'automatically' by an update. Post #12 contains a link to a bug report.
[http://ubuntuforums.org/showthread.php?t=2169702](http://ubuntuforums.org/showthread.php?t=2169702)

Maybe these links will also provide some help
[http://ubuntuforums.org/showthread.php?t=2174776](http://ubuntuforums.org/showthread.php?t=2174776)
[http://ubuntuforums.org/showthread.php?t=2173230](http://ubuntuforums.org/showthread.php?t=2173230)

---

