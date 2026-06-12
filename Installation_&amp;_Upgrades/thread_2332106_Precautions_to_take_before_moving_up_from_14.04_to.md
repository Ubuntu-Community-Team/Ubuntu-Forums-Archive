---
title: "Precautions to take before moving up from 14.04 to 16.04.1"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by Nosphky on 2016-07-28
I have a bootable usb version of 16.04.1 which seems to work ok so next step I want to do is make a clean install of 16.04.1 to replace my 14.04 [sole occupant of the hard drive].

I am looking for any advice on what I should backup to take with me from the old data to the new install.  I have backed up /home to a separate drive and I know that I have other data on /var/www/ so I shall back that up as well.

Currently my home stuff is /home/fred/  : for compatibility with a portable machine, I want the new home directory to be /home/frp/

Will the change of name cause ownership problems when I come to transferring my old home data files to the new 16.04.1 installation ?

Thanks.

---

### Post by oldfred on 2016-07-28
I would also export a list of installed applications to make it easy to reinstall all of them.
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/) 

If you manually edited any files in /etc, you should back those up, not not automatically restore them. New versions may not need edits, or edits may need to be different. But some may be needed so have the backups to make it easy to re-add edits if needed. I backup my /etc grub files as I edit those a lot.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[URL="http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997"]http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997
[/URL]
 Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/$USER/.dmrc
sudo chown $USER:$USER /home/$USER 

Or:
Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

I do not use a separate /home, but use a /mnt/data partition, so I can mount it in one of several installs on my system, but have all the same user data in all of them. I use same permissions & ownership as /home above and link all the typical user folders back into /home.

---

### Post by Nosphky on 2016-07-28
Thank you, oldfred.  You've given me more than I can chew straight off. I think you've just delayed my upgrade by a week :-)
I've noted down the possible extras to backup.

I read your link about dmrc errors but I don't have a  /home/user/.dmrc file initialisation file.  Does this mean I can't get those errors?

Maybe I should change my username on the present system (after making a precautionary backup) to what I want on the new system before upgrading ? That would make it possible to check for correct functioning before the upgrade.

---

### Post by oldfred on 2016-07-28
I have never changed a username, but have seen various posts where users had issues.
Not sure best way to do it.

I now always do a clean install and then get a new /home. But for the last ten years it has been /home/fred. But some of my data in my data partition like my Firefox & Thunderbird profiles are probably 10 years old and in my data partition, copied back & forth from laptop, used with XP, and copied to new system. With new install to a new system I normally reset ownership & permissions to be sure they are consistent in my data partition. And find sometimes downloads or changes get messed up and I just to the full reset to the defaults like I posted above. Rarely have had to do same on /home.

---

### Post by yoshii on 2016-07-29
I personally use the same username and password for the sake of sanity and convenience, but I was surprised recently that on one of my dual boot systems, the username and passwords are different but I can still access the data from both directions.  This is between v16.04 LTS and v14.04.x LTS ...that was a relief.  

Sometimes I still have to chmod or chown just a little bit, but it's easy, sometimes just using the graphical properties menu.  I don't know much else about this topic though, sorry.

---

### Post by Nosphky on 2016-07-29
Thanks oldfred and yoshii.  I'm going to have to take what precautions I can and then just go for it.  

I want to make a clean install of 16.04 because I tried and failed last year to use the ubuntu software updater upgrade option.  The upgrade started and did stuff for several minutes before stopping with an error message that I had a non-standard installation and the upgrade couldn't proceed further. I really had no idea what the error message was trying to tell me.

Wanting to change my username is just because I made the mistake of using a different username on my old laptop from the one on my desktop. In Firefox, I have made my own home page with customised links and when I sync between the 2 machines, one or the other can't find the home page because it's looking in /home/fred/ when it should be looking in /home/frp/ [or vice versa].

So fresh install of the latest version of UbuntuStudio + name change is called for.

---

### Post by oldfred on 2016-07-29
I like shared data partitions and separate system partitions, both for Windows & Ubuntu.
When I still booted XP my shared data was NTFS. I then started to experiment with more installs of Ubuntu and added a shared Linux formatted partition (then ext3, but now only ext4). Then when I shut XP down, moved all data into Linux shared data partition.

I found it easier to backup, copy between systems and install new systems with the shared data partition and I normally keep /home just as /home inside my / (root). But I always have used Fred as my user and reset owership & permissions on data partition. 

But internally it is user 1000 that is the default user, so name may not be as critical.
 Years ago Fedora used user 500 and I was cautioned that the shared data may not work unless you reset Fedora to use user 1000. But later Fedora changed to use 1000 as default. Do not know about all other distributions.

---

### Post by Nosphky on 2016-08-11
I've gathered everything together as backups that I think I'll need prior to a clean install of the new LTS.  In so doing, I discovered a 'nasty'.

I've got lots of collections of screenshots that I don't want to lose and I found that rsync that I used for my backups rejected all the screenshots for reason of bad filename.

All these screenshots had been saved using default settings by xfce4-screenshooter using rapid key pushes 'alt+print'.  Screenshooter saves each file with name such as 'Screenshot - 110816 - 12:10:30.png'.  On the face of it, this provides a unique filename and enables a rapid series of screenshots to be saved.

It is the use of colons ':' in the filename that rsync doesn't like and I had to rename several hundred files.
I find it a little strange that screenshooter produces by default a filename that doesn't permit rsync backup to another disk, nor even manual click and drag either.
I consider I was lucky to catch a glimpse of a 'failure' in the rapidly scrolling stuff in the terminal during the 30 minutes or so that it took rsync to back up my home directory.

---

### Post by oldfred on 2016-08-11
I just looked at my /backup.
It has screenshots & I have used rsync to create /backup. Same with my flash drive which has more backups.

So my rsync has copied files with the timestamp in the name. But I do now try to rename screenshots as later looking at a generic name and time is not very helpful.

But I do watch screen scroll by also. And use the n option to test what it is doing. Found a lot of sub-folders in Firefox, Thunderbird, & /home with thumbnails, caches and other stuff that does not need to be backed up. 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by Nosphky on 2016-08-11
Looking again at my post, I placed the emphasis in the wrong place.   rsync was what showed me the problem with the backups but it wasn't the  fault of rsync.  
When I've made a group of screenshots, I generally select them with the  mouse and click and slide them into another directory, appropriately  named.  This never gave me a problem as long as everything stays on the  same drive.
  
I made my backup onto an external SSD.  And when I rechecked the  problem, I can't click and slide any file with a colon in the name  across onto the SSD nor onto a simple usb stick.  The error says  'invalid filename'.

However, if I fire up a couple of old hard drives and connect them into  my usb hub, I have no problem sliding the file with a colon in its name  to those hard drives.

So my difficulty seems to be related to the use of SSD drive and/or usb  memory sticks.  It would be good to understand why that is so.  That's a question for another place.

---

### Post by oldfred on 2016-08-11
My rsync is run from my SSD, but actual files are on HDD linked into /home. But I also copy to flash drive. No issue with either.

I also backup most critical files to DVD. When almost everything fit on DVD, I did have some files that it gave me errors on, as file name was too long and it shortened them. They were some downloads of files that then I did not particularly worry about.

---

### Post by Nosphky on 2016-08-12
Just for the record :  I've done the clean install of 16.04.1 and loaded my data back from my backup copy.  I didn't do a restore or anything complicated - I just clicked and slid the stuff I wanted from by backup drive to my new installation.

On the matter of changing the username : I did the clean install with a new username (my initials instead of my firstname).  Sliding the old data files into the new installation automatically took care of the apparently different ownership. No remedial action was needed on my part and so my worries were for nothing.

---

### Post by oldfred on 2016-08-12
Great news.

---

