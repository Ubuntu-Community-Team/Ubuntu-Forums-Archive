---
title: "Upgrading to Gutsy"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by PinkBullets9 on 2008-01-19
Hey Guys,
Its been a couple months since the Gutsy release and I have been really hesitant to upgrade. I saw at the beginning people were having a lot of problems so I thought I would just wait out the storm. I just recently got an Ipod Touch and I can figure out how to mount it in Feisty. So I thought that since there are not as many problems right now I'd try to upgrade. I am still fairly new to this so I do not know of any thing to do pre upgrade. I just hit the upgrade button and while it was upgrading it gave me this message, see attachment. I am not really sure what to do cause I am still nooby at this. Any help is appreciated. Thanks in advance!

---

### Post by linuxwizard on 2008-01-19
Remove or disable all extra Repos. you added to your source list. Than try upgrading again.

---

### Post by PinkBullets9 on 2008-01-19
I figured out how to get there but which ones are the ones that I have to delete?

---

### Post by PinkBullets9 on 2008-01-19
here is a list of my sources
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

#AUTOMATIX REPOS END

---

### Post by linuxwizard on 2008-01-19
I didn't know you had Automatix installed. That can cause enough issues by itself. I am not going to be able to help you. I don't want to give you wrong advice on handling your issues on upgrading.

---

### Post by PinkBullets9 on 2008-01-19
Now it is giving me a new message, what does this one mean, disregard the sources part i fixed that

---

### Post by PinkBullets9 on 2008-01-20
Now I decided that I am going to do a clean install after backing up all my data. So this morning I go on to turn on the computer and guess what X Server fails to start. I don't really know what to do because I am not very well learnt in command line. Any support would be appreciated, I don't want to lose my music:(

---

### Post by rosegarden78 on 2008-01-20
I've never had much luck with upgrading over the Internet.  In fact this almost always happens with a network upgrade.  I always download the newest CD at the slowest possible burn speed (4x) because high burn speeds produce errors and buffer overruns.  But don't let the X server crashing stop you.  Although usually a corrupted /etc/X11/xorg.conf by the user, the problem is solved by restoring the original file.  It took months before I realized that.  In fact you even have Internet access via Ethernet cable and FTP access from the command line but that is a different story.

Furthermore, the absence of X Server doesn't restrict the kernel, bash and shell command in any way.  From the command line you can mount and unmount any device.  If I were in your place, and I was, I would buy an external USB hard drive such as LACIE because memory sticks are too small.  You won't see it from the command line but the device should be seen in two possible places:

Type
nano /etc/fstab
nano /etc/mtab
to see the contents of these files

Each line represents a device - look for a newly-created entry such as /dev/sdb1 or /dev/sda2.  Check both files.  Once you think you have the line, turn off LACIE and press Ctrl + X to exit nano.  Now reload the file with nano to inspect the line in question.  You should see the newly-created sda or sdb entry is missing.  This line represents your LACIE or external hard drive or USB stick.  Specifically it must begin with /dev/sda# or /dev/sdb#

One moment please ...

Next you need only create a mount point.  Before you start type "man mount" and "man umount" to get your bearing.

cd /media
sudo mkdir Lacie
sudo mount /dev/sdb1 /media/Lacie 

To backup home folder:
cp /home/* -t /media/Lacie

sudo umount -a will automatically unmount all external drives

As far as the iPod is concerned, it should show up in the fstab or mtab as well (or possibly a related file) and mounting it should be similar to mounting a USB stick.  If you previously mounted the Touch with the mount command from the terminal then nothing will have changed.  And if you're using the GUI to mount the iPod, I'm positive an Ubuntu Gutsy system with KDE + XFCE environments installed is better equipped than a solo Ubuntu Feisty installation.

---

### Post by PinkBullets9 on 2008-01-20
yeah I also realized that the network was causing problems. But now that Xserves won't start how do backup all my music and school papers/assignments?

---

### Post by PinkBullets9 on 2008-01-20
Hey thanks for the tip but how do i restore my Xorg file, because I don't really have the time or money to buy a portable harddrive....

---

### Post by rosegarden78 on 2008-01-20
Sorry ... it took me three months to learn what I'm attempting to teach here.  Usually when you edit the file (if you did) a backup is created with a tilde or something like that.  To restore it (if you changed it or think it was) just navigate to the folder from the terminal:

cd /etc/X11
ls

You should see duplicate xorg file names perhaps with a tilde.  Just remove the tilde from the old one and put it on the new one.
Type man rename

sudo rename xorg.conf xorg.conf-bak
sudo rename ~xorg.conf xorg.conf

One moment please ...

Please read again my first solution.  To backup your stuff you need a USB device (stick or hard drive) and the device number (/dev/sda# or /dev/sdb#) located in either in /etc/fstab or /etc/mtab.  To get the device name you look for Johnny-Come-Lately by using nano commands on these files.  

nano /etc/fstab  ## FSTAB stands for File System Table
nano /etc/mtab ## MTAB stands for Memory Table

To mount this device you need to create a folder for it.  So type
cd /media 
and then type 
sudo mkdir Lacie

Finally type this to mount it
sudo mount /dev/sda# /media/Lacie
replacing sd?# part with your device letter and number from fstab or mtab.

Once mounted you can use simple commands like:  man man (Help on Help) cp (copy) rm (remove) mkdir (make directory) cd (change directory) ls (list directory)
So typing at the terminal

8) cp /home/* -t /media/Lacie 

would copy your entire home folder (Desktop too) to the Lacie or USB Stick you just mounted.  USB is the ONLY way -- I repeat  -- only way to backup a crashed X server from the command line that I'm aware of, short of restoring Xorg or using FTP.  And the only way to mount the device is manually.

---

### Post by rosegarden78 on 2008-01-20
Whatever is crashing X is probably not user-related.  Once you successfully backup your stuff, I strongly suggest a clean install with a slow-burnt CD as I described.  I remember how afraid I was when this happened in Edgy Eft.  It never happens to me anymore with the newest distro Gutsy.

Always install Ubuntu before adding KDM and XFCE and don't install or experiment with advanced graphics or eye candy because it's already included and even works on an Intel915 graphics card.

If you absolutely cannot burn a CD contact Ubuntu.org to order up to  5 free Gutsy discs.

As far as not being able to afford to buy an external hard drive, I paid $100 for a 250 GB one year ago and prices have dropped.  I don't know how you can afford NOT to own an external backup device.  Aren't your documents, pictures and music priceless to you?  Unless the edit to /etc/X11/xorg.conf was made by YOU, and caused the crash, there will NOT be a duplicate of that file.  I strongly suggest you buy or borrow a small hard drive like mine or use the biggest USB stick you can afford or find.

And check out the Ubuntu Guidebook from start to finish.  It's in the help section once you get X working again.  The problem is Feisty.  Backup.  Clean Install.

Don't forget to install Windows before Ubuntu if you want to dual boot ... there are plenty of threads on dual boot Windows with Ubuntu.

If you have to backup a FAT32 or NTFS partition, you need to learn advanced mounting techniques but it's possible as well.

If you cannot afford a drive, using the GParted program from a LiveCD should let you partition a virtual external hard drive partition.  Say 4 GB or the size of your home folder.  Make sure the partitions are all Primary and you can mount these the same way I described by checking the fstab and mtab.  Then when you clean install it only affects the original partitions.  The data in your new partition is safe.  Just be careful not to delete the partition by mistake!

---

### Post by PinkBullets9 on 2008-01-20
Alrite thanks I figured out how to reconfigure the Xorg and now I am up and running! I am going to back up my music and such then do a clean install. If anything goes wrong with that I will keep you guys posted

---

### Post by PinkBullets9 on 2008-01-20
I am now in Gutsy! Everything has gone smoothly and now I just want to install my nVidia drivers. Do I just go to restricted drivers manager and update cause it will not let me do that...I try to install the restriced driver and it says nvidia-glx-new is not enabled. Then i tried downloading Envy and installing the driver through that. No dice. It says that the dependency xserver-xorg-dev is not satisfied. Searched for that in synaptic and could not find it. At least I got wireless internet working......

---

### Post by PinkBullets9 on 2008-01-20
Sorry guys I guess I am just a little impatient...I just had to wait for software updates and then Envy installed no problem haha

---

### Post by rosegarden78 on 2008-01-20
[http://ubuntuforums.org/showthread.php?t=673614](http://ubuntuforums.org/showthread.php?t=673614)
I guess Ubuntu *does* make a backup of xorg after all.

---

### Post by PinkBullets9 on 2008-01-20
I know that you think it is absurd that I can not afford a portable hdd but it is true. I am a high school student and at the moment unemployed. All the pictures ony computer are my dad's. Of course I care about then too but not enough to spend my money on a portable hdd. Hope that clears that up. On another note my gutsy install is going smooth. I do not see any problems yet thankfully.

---

### Post by PinkBullets9 on 2008-01-21
One more question guys, I want my default screen resolution to be 1440x900 but for some reason I can not set it to that with the default screen resolution application. The Nvidia Settings that came with the driver is able to. When I click save to xorg config it says that it can not back it up. I am guessing I need to enter that program with root privileges, how am I supposed to about that?

**Never mind I figured it out**

---

