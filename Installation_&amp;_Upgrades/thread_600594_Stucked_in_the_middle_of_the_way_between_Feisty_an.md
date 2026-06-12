---
title: "Stucked in the middle of the way between Feisty and Gusty"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2007-11-02
I first performed all apps updates in 7.04
Then I 'version upgrade'.  Upgrade wizard -> 'Upgrading Kubuntu to Version 7.10'
1) Preparing the upgrade -> OK
2) Modifying the software channels -> OK (Notice: support for some apps ended)
3) Fetching the upgrades ->  I went to sleep (expecting 7 to 8 hours to download)
4) Early morning, no warning, no advice, no notice, just my regular desktop (KDE) in my screen.
Suspicious.
I restarted and found that xorg.conf was changed because couldn't start X.
I fixed it restoring a backup  (It is a problem of video output).
Well, now again on X, adept_updater is announcing new updates.
'Fetch list of updates' -> A large list of 'upgradeable' apps is displayed (install 138, upgrade 1037, remove 6)(download 876M, installation 626M)
I select 'upgrade' and get 'There was an error commiting changes. Possibly there was a problem downloading some packages or the commit packages would break packages'
After closing this window I get 'A new distribution version s available!  Click next if you wish to upgrade now.
So I click on 'Version Upgrade'
Then it starts again with the numbered steps above.
On the step 3) the fetching process takes only a minute and then nothing happens, just finish the upgrade.
I repeated this upgrade procedure and fetching process was not performed (or maybe finished)
My next look was to open the Adept Manager and 'Fetch Updates'.
The main difference is that all repositeries are searched in Gusty sites (like [http://archive.ubuntu.com/](http://archive.ubuntu.com/)[COLOR="Red"]gusty[/COLOR]-updates/main Sources)

On boot screen I see my regular kernels 2.6.20-16-generic (and 15) not the new one.
There are some apps that do not load (Gnview, Wine apps)
Well,  the title of this thread.
Thanks for any help in advance

---

### Post by Pumalite on 2007-11-02
Try to save your /home and data and do a clean install.

---

### Post by marciano#1 on 2007-11-06
I downloaded a Gutsy desktop CD and used the partition manager to create a new partition to store /home directory.
Gutsy was installed in sdb4.  Feisty and my old /home dir are placed at sdb2, the other partition.
So I suppose I do not need to move anything:  /home remains in sdb2 (old sys here has to be deleted) 
My first problem is to set that /home is located in sdb2 instead of sdb4 (have to search google)
(Storage Media displays sdb1(small XP partition), sdb4(Gutsy) and sda1(another HD)

The second one I am very worried is related about my first post.
"21 updates packages available" is the warning from Adept Updater
Then I "fetch list of Updates" and finally "Apply updates"
And...

 'There was an error commiting changes. Possibly there was a problem downloading some packages or the commit packages would break packages'
After closing this window I get 'A new distribution version s available! Click next if you wish to upgrade now.  !!!!!!!!!!

Was that clean enough or what woulb be the problem?
This is an INTEL mobo with a Core 2 Duo E4400 processor, EN7100 NVidia
Thank you,
Daniel

---

### Post by Pumalite on 2007-11-06
Check this link:
[http://ubuntuforums.org/showthread.php?t=600485](http://ubuntuforums.org/showthread.php?t=600485)
Also check to see that your apt-get is working. If not, post back with error message.
Also: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
In case it helps any.

---

### Post by marciano#1 on 2007-11-06
Thanks for your ultra quick reply.
I had done sudo aptitude update and
sudo apt-get install gparted 
successfully

---

### Post by marciano#1 on 2007-11-06
sudo aptitude update && sudo aptitude upgrade
did performed those 21 updates successfully.
So it is an Adept bug?
Thank you

---

### Post by Pumalite on 2007-11-06
Don't think so. Servers might have been stuck at the time.

---

### Post by marciano#1 on 2007-11-06
Okay.
Now I am in the way to mount sdb2.
I had performed diskmounter and only  got  mounted hda (the other HD) and sdb1 (the small XP partition)

fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=78a1b861-4617-46e8-8626-60aafdbc9c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=94c37bdf-519d-4dae-bd51-e4123c022612 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto,exec 0       0
/dev/sdd        /media/floppy2  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0

fdisk (sda omitted)
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=78a1b861-4617-46e8-8626-60aafdbc9c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=94c37bdf-519d-4dae-bd51-e4123c022612 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto,exec 0       0
/dev/sdd        /media/floppy2  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0
So
/dev/sdb2            1276       24375   185550750   83  Linux
Then I created 
$ sudo mkdir /media/sdb2       

Inserted to fstab:
/dev/sdb2 /media/sdb2 ext3 defaults,errors=remount-ro 0       1
Is this the best setting?

$sudo mount -a
$ ls /media/sdb2/home
displays my old /home content.  Dolphin is not displaying this new media at this time.

So my lasts steps are: setup sys to use my old /home directory as the regular one.
Is it correct to remove the rest of the dirs but /home in sdb2 where Feisty is installed or do you suggest a better procedure?

Thanks a lot

---

### Post by Pumalite on 2007-11-06
If you are going to reinstall you just need to save /home, don't format it and give it a mount point at appropriate time.

---

### Post by marciano#1 on 2007-11-06
I'm not sure to understand you.
I have splited an ext3 partition in two parts:  sdb2 and sdb4
sdb2 contains my old and prefered /home  It also contains Feisty installation and all my programs.
sdb4 contains a clean install of Gutsy
I need to change Gutsy settings to use /home of the other partition sdb2 instead of its recently created in sdb4.
Finally i want Gutsy in sbd4 and /home in sdb2
Would be enough to remove the rest of the Feisty dirs in sdb2 or do you suggest to move /homeOLD to sdb4, format sdb2, and then move again /homeOLD to sdb2?
How do I tell Gutsy to use the other /home dir ?

---

### Post by Pumalite on 2007-11-06
Old /home is supposed to be chosen at installation. Maybe there is a way to point your current installation of Gutsy to your old /home, but I'm not sure. One way that occurs to me is to edit your fstab after backup and replace the current Gutsy /home for your old /home. Better to wait for the opinion of somebody more adept at that than me. Somebody will jump in.

---

### Post by marciano#1 on 2007-11-06
I think it would be better to start a new post with this question that is not related to the title

---

### Post by Pumalite on 2007-11-06
Good idea.

---

### Post by luh3417 on 2007-11-09
I am running AMD 64 Kubuntu and upgraded using adept from feisty to gusty. All the package repositories are upgraded to gutsy but the kernel running is 2.6.20 not 2.6.22.  2.6.22 does not come up in grub loader. Should I wait for a bug fix or can you point me in the right direction to fix this,? thanks.

---

### Post by Pumalite on 2007-11-09
Save /home and data and do a clean install. I've heard the new kernel installs itself in a different drive sometimes. You might want to look for it.

---

