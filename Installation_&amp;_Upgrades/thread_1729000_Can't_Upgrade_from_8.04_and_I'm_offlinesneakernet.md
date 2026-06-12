---
title: "Can't Upgrade from 8.04 and I'm offline/sneakernet"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by Elludium_Q-36 on 2011-04-14
Currently I'm running Kubuntu 8.04 "Hardy Heron".  I tried to upgrade directly to Kubuntu 10.04 LTS since both were said to be LTS releases and you are supposed to be able to go from LTS to LTS.

Unfortunately I couldn't get cdromupgrade to launch the distribution upgrade utility and the following errors were returned:

> 
kubuntu@Kubuntu1jc1:/media/cdrom1$ sh cdromupgrade
/usr/lib/python2.5/site1packages/apt/__init__.py:18: FutureWarning: apt API not
stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/tmp/tmp.xFtvfD6460/lucid", line 7, in <module>
    sys.exit(main())
  File "/tmp/tmp.xFtvfD6460/DistUpgradeMain.py", line 141, in main
    logdir = setup_logging(options, config)
  File "/tmp/tmp.xFtvfD6460/DistUpgradeMain.py", line 86, in setup_logging
    filemode='w')
  File "/usr/lib/python2.5/logging/__init__.py", line 1240, in basicConfig
    hdlr = FileHandler(filename, mode)
  File "/usr/lib/python2.5/logging/__init__.py", line 770, in __init__
    stream = open(filename, mode)
IOError: [Errno 13] Permission denied: '/var/log/dist1upgrade/main.log'
kubuntu@Kubuntu1jc1:/media/cdrom1$


Per the instructions in my last post [http://ubuntuforums.org/showpost.php?p=10672841&postcount=4](http://ubuntuforums.org/showpost.php?p=10672841&postcount=4) ; I dropped in the 9.10 alt CD and issued the cdromupgrade command
```

gksu sh /media/cdrom1/cdromupgrade

```
but got the following errors:

> 
Failed to fetch cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.39_i386.deb Wrong CD-ROM
Failed to fetch cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/pool/main/l/linux-meta/linux-headers-generic_2.6.32.24.25_i386.deb Wrong CD-ROM
Failed to fetch cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/pool/main/m/manpages/manpages-dev_3.23-1_all.deb Wrong CD-ROM


I decided to again try the 10.04.1 alt CD that I have.  This time cdromupgrade worked fine but I still got the following errors:

> 
Failed to fetch cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.39_i386.deb Wrong CD-ROM
Failed to fetch cdrom:[Kubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/pool/main/l/linux-meta/linux-headers-generic_2.6.32.24.25_i386.deb Wrong CD-ROM


Here's my kernel info:

```

kubuntu@Kubuntu-jc1:~$ uname -a
Linux Kubuntu-jc1 2.6.24-28-generic #1 SMP Wed Jan 12 21:17:05 UTC 2011 i686 GNU/Linux
kubuntu@Kubuntu-jc1:~$

```

I do remember updating a couple packages on 8.04 from a 10.04 desktop CD, which could be problematic.  Unfortunately I do not have any internet connectivity on this desktop box :-(

---

### Post by KegHead on 2011-04-14
Hi!

Are you able to create a USB image or cd of 10.04 from another computer?

KegHead

---

### Post by Elludium_Q-36 on 2011-04-19
Why, do you need a CD copy of 10.04 :-?

I checked the integrity of the CDs and also check the MD5 checksums.

Methinks it has to do with adding packages from the 10.04 desktop CD.  The system was compiled from a Kubuntu 8.04.2 desktop CD but I had also taken packages from a Ubuntu 8.04.4 desktop CD.

The 8.04.4 CD is Missing In Action but I've downloaded the ISO images and will try to downgrade the packages before running cdromupgrade with the 10.04 alternative CD again :-)

---

### Post by mörgæs on 2011-04-19
If you have a 10.04 alternate CD ready, I would go for a fresh install. One hour, problem solved.

---

### Post by Elludium_Q-36 on 2011-04-22
Right...

Yes, I know I can do a fresh install.  I've had to do that before.

The problem is that wipes out anything I added while the box was marginally online

There goes the Medibuntu repository, their package(s) that allow me to watch DVDs on Linux and the authentication keys.

There goes Firefox & Opera bookmarks, settings and session tab info.

Someone told me about Keryx but some Konsole terminal commands only execute while online.

Now I did try to downgrade the added 10.04 packages to 8.04 with Synaptic Package Manager's menu: Package > “Force Version” menu option but Synaptic won't recognize a CD.  When I try to use Edit > “Add CD-ROM...”, I get a “Failed to mount CD” error, even though CDs mount fine on the desktop and open in Dolphin, etc.

I have backed up the /home/ directory and thought to do a fresh install of Kubuntu 8.04.2, then replace backups of configuration, data, authentication key and package files, if the community could give me some pointers of what to back up.

Then from alt CDs, I can run the cdromupgrade script to 9.10 and finally to 10.04, as per the tutorials.

The reason I'd reinstall 8.04 is so that the config files, etc. match the version, then the upgrade scripts would alter the files normally.

I wouldn't have posted if the easiest answer was to just do a fresh install alone.  A big problem is that the desktop is OFFLINE and only on “sneakernet” :-(

I can't be the only one who has needed to reinstall but has wanted to save data, configurations and packages...

I found some of the answer in another post:  [http://ubuntuforums.org/showthread.php?t=1733570](http://ubuntuforums.org/showthread.php?t=1733570)

It's funny that it seems that some just chime in here to increase their post count :-|

---

