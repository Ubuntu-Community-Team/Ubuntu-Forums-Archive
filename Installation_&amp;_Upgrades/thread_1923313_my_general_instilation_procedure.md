---
title: "my general instilation procedure"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2012-02-10
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i do all this from a live cd, or established linux system.

when setting up a server it is a good idea to run just a single server on the target machine.  it is advantageous to choose a fast stable file system.  it's also advantageous to partition the drive into separate blocks to wipe the file system of the OS upon upgrade and save personal files.  it is also useful to know how to check file systems for corruption.

first, thank IBM for JFS.  EXT takes a long time to go through its file system to check for errors, JFS does not.  hour and a half check disk at boot for ext3 vs 5 minute JFS check, over a TB.  i partition my disk for 20-30 gigs for OS, (a small partition for boot scripts is optional that i do.) then partition /home/$USER for another drive and this is a mass storage drive.  gparted from live ubuntu cd is an easy solution to do all of this.

in windows its akin to making a 30 gig c drive and a 970 gig d drive.  linux scripts are small compared to windows, 30 gigs of just os for linux is tons, fully loaded my machine was about 15 gigs in with kde and gnome and xfce and tons and tons of other garbage installed.

fsck.jfs is the only command i ask you to remember. think of it as "FileSystemChecK.jfs"  jfs utils might need instilation.  if your partition wont boot and has a corruption error upon next boot skip mounting the drive and fsck.jfs the drive.  /dev/sda /dev/sdb /dev/hda /dev/hdb = sata 1 sata 2 ide 1 ide 2

for servers its a good idea to get your OS as close to just bash and apt-get only...  i personally do SSH for the time being, but even that has flaws about brute force attacks, so i want to limit my SSH to local clinets only.  i dont have a good SSH security lock down tutorial up yet.  but i would run ssh and build the server up remotely to load its functions into it and configure them.

im doing this procedure on a farm of computers some reliable and some not so much.  the not so much machines are whittled down to only what they are needed for, and strategically located within the network topology.

if you plan on using xfs for storage performance make a separate /boot partition and have that be JFS


so i run jfs for /boot formatted
i run xfs for / formatted
and i run jfs for /home NOT FORMATTED

after i install from cd then i issue this command string to quickly load stuff

```

sudo apt-get install vlc audacious xfce4 cairo-dock fusion-icon apache2 fortune electricsheep xscreensaver xfce4-terminal xfce4-goodies thunderbird gimp chromium-browser pidgin firestarter

```

for ubuntu 11.10 since gnome and xfce and everything else is such a horrible mess temporarily install lxde and synaptic

```

sudo apt-get install lxde synaptic

```

general music stuff
```

sudo apt-get install qjackctl qsynth timidity solfege rakarrack

```

---

