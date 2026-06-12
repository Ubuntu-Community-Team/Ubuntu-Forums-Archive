---
title: "Dualboot Win10/Linux on SSD/HDD"
date: 2016-02-06
forum: Installation &amp; Upgrades
---

### Post by Frncio on 2016-02-06
Hello everyone, this is my first post! Very happy to be part of this community.

I've had a dualboot laptop Linux/Win7 for years, Win7 for most stuff and Linux for some programming tasks. I am planning on using Ubuntu for most stuff from now on (and Win10 for games =D) and I am having trouble making up my mind about the partition scheme.

My laptop has a 128GB SSD and a 750GB HDD. I want both systems to boot from the ssd and have most of my software installed in it for better performance. The HDD will hold all my personal documents/media and some extra software that may not fit on the ssd. 
I am very confused about all the different partitions ubuntu has and I would like some experienced opinion on what I am planning to do. I am also not sure about the best way to share the data between the OS.

128 gb SSD:
- 60GB partition for Win10 OS and some applications
- 20GB root partition (/) for ubuntu 14.04 system files 
- 30GB /home partition for extra applications on ubuntu
- 8GB /swap partition (I have 8GB of RAM)

750 gb HDD
- 50 GB extra partition for ubuntu extra applications that my not fit into the SSD
- 50 GB extra partition for Win10 software that may not fit into the SSD
- 650 GB shared data partition

Questions:
- How can I create the extra software partitions into the HDD for both OS?
- What is the best way to create the shared data partition between the OS? (Currently I use the Win data partition which ubuntu can see but Win can't).
- Can I make the /swap partition smaller?
- Any SSD related advice for ubuntu? I read something about "leave read-only files on ssd" [here]("https://help.ubuntu.com/community/PartitioningSchemes") but couldn't make any sense out of it.
- [I]Am I messing something up?

[/I]Thanks and please let me know what you think!

---

### Post by Dennis N on 2016-02-06
> 30GB /home partition for extra applications on ubuntu:
50 GB extra partition for ubuntu extra applications that my not fit into the SSD

As for Ubuntu, applications from the official repositories are installed to specific directories in your / partition. You can't select them to be installed to your home partition or elsewhere. 

> 8GB /swap partition (I have 8GB of RAM)

With that much RAM, I doubt you will be using much swap. I go no higher than 4 gB.

I have an SSD and a HDD. I put my own files (Documents, music, videos) in a separate partition on the HDD, mounted to my root file system through /mnt and automount that from fstab. This is to make new installs easier because all my files are undisturbed on that separate partition and I just have to set up the mounting again on a new install, and also make them available to any dual booted Linux.

---

### Post by oldfred on 2016-02-06
If you have 8GB of RAM, you may never use swap. But often best to have some, even though others have said it works without any.
I would then just have 2 or 4GB on HDD for swap and keep the space for Windows. Windows needs lots of space. And NTFS works best if you keep 30% free inside the NTFS partition.

With Ubuntu, I use a 25GB / (root) partition including /home. But all data is in my data partition on the HDD linked back like Dennis N's configuration.

I posted my partitions, just as one example. But I do not have Windows, but install two Ubuntu on SSD.
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

When I still had XP on old BIOS system I had a shared NTFS data partition. Now I just have a shared Linux partition so each install can use same data.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

With Windows 10 make sure fast start or always on hibernation is off.
      
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Lots more info on UEFI installs in link below in my signature.

---

### Post by Frncio on 2016-02-06
Thanks so much for your answers! Taking your input into and a conversation I had with a friend of mine into consideration I am planning on using the following partition scheme:

SSD (128gB)
- 100gB Win10
- 26gB for root /
- 2gB swap

HDD
- 15gB for /var
- 150gB for /home
- the rest on ntfs for shared data

My friend said that the /var could be placed on the hdd because it does not "deserves" the extra speed from the ssd. Any problems on doing that?

> **Dennis N said:**
> 
I have an SSD and a HDD. I put my own files (Documents, music, videos) in a separate partition on the HDD, mounted to my root file system through /mnt and automount that from fstab. This is to make new installs easier because all my files are undisturbed on that separate partition and I just have to set up the mounting again on a new install, and also make them available to any dual booted Linux.

If I place my /home into the hdd my personal files will be undisturbed by new installs also, right?

---

### Post by Frncio on 2016-02-06
> **oldfred said:**
> 

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

With Windows 10 make sure fast start or always on hibernation is off.
      
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Lots more info on UEFI installs in link below in my signature.

Ok, I see that there is an issue with placing /home at the hdd as well (config files for programs will be slowly accessed).

All I want is a /data on the hdd and a small /home directory at the ssd. I will keep reading on it because I am not sure I know how to do that so far.

Sorry for the double post, but the amount of info is a bit overwhelming.

---

### Post by oldfred on 2016-02-06
I keep all the default / folders on SSD for speed. But data files not used as much then on HDD.
My system with lots of programs, but not games uses about 12 or 13GB of the 25GB I allocate for /. And 2GB of that is /home which most of is the .wine, as I use the Windows version of Picasa.

---

