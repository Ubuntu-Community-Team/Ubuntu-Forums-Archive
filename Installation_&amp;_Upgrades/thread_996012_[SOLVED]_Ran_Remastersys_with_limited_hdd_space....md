---
title: "[SOLVED] Ran Remastersys with limited hdd space... now I've got none, help!"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by It_Was_Luck on 2008-11-28
A few weeks ago I wanted to clone my exact Ubuntu install over to a LiveCD so that I may install it on a new, larger HDD. Well I was pushed toward Remastersys. I ran it once, with 4GB left, and discovered I selected the wrong option. After that I only had 2GB left and decided I should probably delete the old back-up I accidentaly did. Well it wouldn't let me delete through my normal menu, so I had to open up nautilus, and from there, I deleted them, and they are not there anymore, but my 2GB of space never came back!!

To speed up this story... I'm in the same area I was a week ago with absolutely NO HDD space... and even after I delete these huge .ISO files, they are still taking up space on my HDD! 

Please help!

---

### Post by It_Was_Luck on 2008-11-28
Little bump...

I've been reading around the forums and apparently the command "df" can get you more info. If your the person that can help me, here is the outcome of my "df" command:
```
ben@ben-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             13043800  12919420         0 100% /
varrun                  257044       104    256940   1% /var/run
varlock                 257044         0    257044   0% /var/lock
udev                    257044        64    256980   1% /dev
devshm                  257044        48    256996   1% /dev/shm
lrm                     257044     39780    217264  16% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1                48052      7412     40640  16% /media/sda1
/dev/sda2             62918568  61709752   1208816  99% /media/sda2
overflow                  1024        48       976   5% /tmp

```

---

### Post by cariboo on 2008-11-28
If you run in a terminal:

```
sudo apt-get clean
```

and

```
sudo apt-get autoremove
```

THis will removed archived packages in var/cache/apt/archives and remove any dependencies that are no longer needed

If you use df -h you will get a more human readable output eg:

```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.2G   17G  12% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M  420K  249M   1% /var/run
varlock               249M  4.0K  249M   1% /var/lock
udev                  249M  2.8M  246M   2% /dev
tmpfs                 249M     0  249M   0% /dev/shm
/dev/sda3              94G   38G   57G  41% /home
/dev/mapper/nvidia_ifdejefh1
                      370G  260G   92G  74% /home/storage
/dev/sdb1              74G   33G   41G  45% /home/backups
```

instead of trying how figure the usage from the blocks used.

---

### Post by It_Was_Luck on 2008-11-28
Before clean commands:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              13G   13G     0 100% /
varrun                252M  104K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   64K  251M   1% /dev
devshm                252M   48K  251M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1              47M  7.3M   40M  16% /media/sda1
/dev/sda2              61G   59G  1.2G  99% /media/sda2
overflow              1.0M   48K  976K   5% /tmp

```

After:
```
ben@ben-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              13G   12G  248M  98% /
varrun                252M  104K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   64K  251M   1% /dev
devshm                252M   48K  251M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1              47M  7.3M   40M  16% /media/sda1
/dev/sda2              61G   59G  1.2G  99% /media/sda2
overflow              1.0M   48K  976K   5% /tmp

```

Thanks for that help, but the fact is that there should be over 5GB of random back-up files that nautilus said I deleted and they are not there but they are still taking up space.

---

### Post by VastOne on 2008-11-29
Have you tried using Disk Usage Analyzer under Accessories to help you see where your bulk files are held?

---

### Post by robert shearer on 2008-11-29
To find big files that you _may_ want to remove try..

```
sudo find / -type f -size +50000
```

and you can vary the size searched for by changing the number.
(This is just an example but should find some biggies)

Look for things you may have downloaded but no longer need such as large audio/video files and iso images and back them up to other media then delete them or delete them **only** if you are sure you do not want/need them. Post if unsure before deleting.

Then run the find code again to check they are gone.

Also this from the Remastersys website,,,

.

>   The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
  Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes.  Mine generally is just a bit over 1 gig. 
  Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.  

Also look for the following folder:  /var/cache/apt/archives.  That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system.  The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason.  You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more. 

---

### Post by It_Was_Luck on 2008-11-29
Robert... thank you for that execellent bit of help!!

Let me explain what happened... I ran the command and at least a dozen files with "remastersys" in there title popped up, sure enough I opened up nautilus and traced them back to my trash can (/root/.local/share/trash/files) and I found over 8GB of remastersys files...

**But heres the problem...**
When I select them all and click delete they all poof away, then one second later, they all appear again. Please advise.

---

### Post by It_Was_Luck on 2008-11-29
Bump...

Could this be a permission problem with my own trashcan?

---

### Post by robert shearer on 2008-11-29
Thats about my limit(just an observant user, not a guru:))

These links may be of help though....the first sounds something like your problem and the second is the Remastersys site where the developer often solves user query's   Hope this helps:)

  

[http://loscompanion.com/forums/index.php?PHPSESSID=c98373a3680c128be76d97dab7557e2d&topic=5606.0](http://loscompanion.com/forums/index.php?PHPSESSID=c98373a3680c128be76d97dab7557e2d&topic=5606.0)

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

EDIT.  more thoughts,  if Remastersys runs as root then there might be a permissions problem trying to empty trash as an ordinary user.
 Maybe you need to remove them using sudo.

If you are using Remastersys from the gui have you tried "clean-remove temporary files"? as this removes the build directory for previous Remastersys attempts.

---

### Post by It_Was_Luck on 2008-11-29
Using your brilliant help I sat down and thought... then I looked into a real, professional sudo command that could remove... well here's what I did.

**Problem:**
Files that have been deleted still remain in the the trash index. For example, if you have to open up nautilus to remove something, but the second you delete it poofs back.

**Solution:**
We need to run a delete command.
If you need to delete a directory and all the files inside:
```
sudo rm -rf dir 'drag and drop directory here and link will pop in'
```

Then to remove extra files:
```
sudo rm 'select all the files and drag them here'
```

Depending on how much space your deleting it can take a few extra seconds.

Thanks for the help guys, much, much appreciated.

---

### Post by Fragadelic on 2008-12-03
Remastersys has a clean function of its own so you shouldn't be manually deleting anything in the remastersys working area.

Either select the option to clean the working folder from the gui or run "sudo remastersys clean" from a terminal window.

BTW, I don't recommend trying to remaster unless you have plenty of free space.  There is no way for remastersys to figure out what the compression ratio is going to be beforehand and then you also need double the free space so the iso can be built.

I'm the remastersys author BTW.

[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

---

### Post by toreador on 2009-02-14
Awesome thread. You guys just helped me recover 10+ Gigs of free space from a couple or VERY careless mistakes!

Many thanks!

---

