---
title: "Upgrading : Not enough Free Disk Space : how to make space?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by captain_conrad on 2010-03-22
Good day

I am still a noob and i am extremely useless with upgrading therefore please help. I followed the upgrade button on the update manager, and it spat me this message:

¨

Not enough free disk space

The upgrade is now aborted. The upgrade needs a total of 2022M free space on disk '/'. Please free at least an additional 673M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

¨


I tried typing that sudo apt-get clean thing into my terminal and it simply did nothing, it just carries on as it I just hit enter multiple times. Am I doing it wrong somehow?

Here is my situation with my hard drives. I have one hard drive which is split into three partitions:

...............................total.......free.......available
/..............................17.5Gb......2.1Gb.......1.3Gb
/TheGoodStuff.........110 Gb......4.8Gb.......4.8Gb
/Windows................14.6Gb......83 Mb.......83Mb

I know the obvious way to clean up disk space is to erase stuff like movies or music or video or pictures etc, by either deleting them or burning them to CD etc. I have already done that, all of my personal things are on the 110GB drive, which I clean up space on regularely.

Its the /  drive that I need to clean, and all thats on there is (for lack of understanding of what to call this) ¨ubuntu´s stuff¨.

I have a dual boot with windows vista and ubuntu, and the /windows drive consists of purely microsoft vista and its sesspool of useless data stuff just filling up the hard drive which annoys me endlessly because my AVG will not update itself because of this drive being full, and my iTunes keeps complaining the /windows drive is full, despite all my music being on my 110Gb partition.

Please can I get some advice as to how on earth to clean my /   drive and the /windows drive, because I have no idea what all these funny folders in there are and what they do and if I start deleting things I can just see it failing to epic proportions.

Once that is done, Im sure the upgrading will take care of itself?

Please help, any advice will do

---

### Post by kansasnoob on 2010-03-22
Boot into your Ubuntu and then post the output of the following two commands from Terminal (please copy-n-paste):

```
df -H
```

```
sudo du -sh /*
```

---

### Post by captain_conrad on 2010-04-10
conrad@Conrad:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               19G    17G   1.3G  93% /
tmpfs                  1.1G      0   1.1G   0% /lib/init/rw
varrun                 1.1G   111k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G   168k   1.1G   1% /dev
tmpfs                  1.1G   185k   1.1G   1% /dev/shm
lrm                    1.1G   2.3M   1.1G   1% /lib/modules/2.6.28-18-generic/volatile
/dev/sda2               16G    16G   265M  99% /media/Windows
/dev/sda3              119G   116G   2.4G  98% /media/TheGoodStuff
conrad@Conrad:~$

---

### Post by captain_conrad on 2010-04-10
conrad@Conrad:~$ sudo du -sh /*
[sudo] password for conrad: 
6.1M	/bin
51M	/boot
0	/cdrom
468K	/dev
15M	/etc
du: cannot access `/home/conrad/.gvfs': Permission denied
12G	/home
0	/initrd.img
0	/initrd.img.old
418M	/lib
16K	/lost+found
122G	/media
4.0K	/mnt
252M	/opt
du: cannot access `/proc/8035/task/8035/fd/4': No such file or directory
du: cannot access `/proc/8035/task/8035/fdinfo/4': No such file or directory
du: cannot access `/proc/8035/fd/4': No such file or directory
du: cannot access `/proc/8035/fdinfo/4': No such file or directory
0	/proc
7.7M	/root
7.3M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
88K	/tmp
2.9G	/usr
286M	/var
0	/vmlinuz
0	/vmlinuz.old
conrad@Conrad:~$

---

### Post by captain_conrad on 2010-04-15
Um, help? anybody? somebody?

---

### Post by srs5694 on 2010-04-15
You've got too many files (or a small number of too-big files) in /home. Try deleting or moving some of them. If this is a problem, your only solutions are to resize some of your partitions or to buy a new hard disk (either a newer replacement drive or a supplemental drive).

In the future, consider putting /home on its own partition. Doing so after you've installed is possible, but a bit tedious, so you may want to just keep this in mind for future installations. If you put your user files (in /home) on their own partition, then filling it up won't interfere with your ability to upgrade your OS, which should be on a 5-20GB partition (depending on how many programs you want to install).

---

### Post by captain_conrad on 2010-05-31
SOLVED!!!!

I removed one or two programmes that i was not using (or that i could download again once i have completed the upgrade) by using synaptic package manager. This did not free up much space.

however...

Going in to my home folder, I selected the VIEW drop down menu, and i ticked the box called ¨show hidden files¨

Now all of a sudden theres a ton of files in my home folder. I deleted the ones corresponding with the programmes I had just removed (K3B, audacity, Brasero, etc) and boom I freed up like 3 Gb of hard drive space!

Updated from  9.04  to  9.10  to  10.04  with no problems! :)

Thanks for the help guys :)

---

