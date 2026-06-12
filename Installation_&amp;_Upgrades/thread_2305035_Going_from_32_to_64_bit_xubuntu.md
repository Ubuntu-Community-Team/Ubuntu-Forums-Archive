---
title: "Going from 32 to 64 bit xubuntu?"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by greg_s3 on 2015-12-02
I have 32 bit xubuntu on my PC  that someone installed and want to upgrade it to 64 bit to take advantage of more RAM I'm adding. My processor supports 64 bits so I know I should be able to do this. I'm having trouble finding a step by step guide on how to do this. I want to learn how to do things like this on my own instead of having to hire this out and having to turn my computer over to someone else for a time. I would appreciate any help on how to do this or where to go on the internet to learn this.

---

### Post by The Cog on 2015-12-02
I don't think it is an upgradeable thing to do. I think you need to do a fresh install of 64-bit.

If you have spare unused disk space, you can install there (choose "something else" in the partitioner, and add your own new partition into the unused space). Otherwise you will probably have to overwrite the original 32-bit install. If you already have windows on there, you may again need to choose somethign else to get full control of the partitioning. 

Back up all your documents first, whichever way you are going.  The best thing to do is to create a tar file of the /home directory on an external drive like this:
```
sudo tar cvf /media/myname/diskname/home.tar /home
```
where myname and diskname will be your user name and the name of the external disk
You can in-tar this into the /home folder of the new install later:
cd /
```
sduo tar xvf /media/myname/diskname/home.tar
```
which should restore all your documents and settings.
Be careful to create identical usernames in the new system in the same order as the last install, to retain the same nummerical user IDs.

If you're not sure of anything any step along the way, come back here and ask for more detail.

---

### Post by slickymaster on 2015-12-02
> **The Cog said:**
> I don't think it is an upgradeable thing to do. I think you need to do a fresh install of 64-bit.

<---snip--->
+1

---

### Post by oldfred on 2015-12-02
If you have installed lots of applications you can also export a list of installed apps and use list to reinstall.
If you have made various configuration changes, you want to backup /home including all the hidden files & folders where your user configurations are.

My backup procedure is so I can do a new install easily. I do not backup system as that is so easy to reinstall.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

I prefer to use rsync to another drive regularly and take copies of that to DVD and/or flash drives so if I delete or change something I have an older copy to go back to. I include in my rsync script some system documentation like the bootinfoscript and some other data.

       
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by greg_s3 on 2015-12-03
Will the above command save my emails and contacts in Thunderbird?

---

### Post by Bucky Ball on 2015-12-03
> **greg_s3 said:**
> Will the above command save my emails and contacts in Thunderbird?

Just [back them up]("https://duckduckgo.com/?q=back+up+thunderbird+profile+ubuntu+14") and plop them in the appropriate place on the new install. We can help you with that. Same with [Firefox profile]("https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles") (if you're using Firefox that is, the profile contains bookmarks, settings, etc) and some other things.

---

### Post by greg_s3 on 2015-12-03
I tried the above command in a terminal and it could do anything with it.

---

### Post by oldfred on 2015-12-03
Copy & paste terminal commands, so we know exactly what the issue is. Often typos or spelling of commands. Or missing sudo as you most often have to be at the administrative level to run many commands.

---

### Post by greg_s3 on 2015-12-03
Now I manged to make it so my computer won't shut of with the shut-off icon (I get a box saying I don't have the "session manager's" permission) - I have to do it manually - and when I restart it takes a long time after I log in to get anything on the screen; then if that isn't bad enough Thunderbird and Firefox don't come back on their own like they usually do and when I start Firefox manually I don't get any tabs back from my previous session. This is terribly frustrating: I try to do something that should be easy like backing up my files to a DVD so I can switch to a 64 bit operating system so I can use 4gB of RAM and I manage to screw up my whole computer because I can't figure out what I'm doing after spending literally hours reading the results to a bunch of web searches on "how to back-up files" and other ways to search that topic. (Seems like for every search I find a different way to do this.)

 I feel like people writing forum posts think newcomers to computer tinkering like me intuitively know how to do all this stuff, even though I know they just want to help (which I appreciate). I even went so far as to the library and checked out a book on Linux Administration to try to figure this out. I'm not the smartest person in the world, but I'm not stupid either (I managed to make it through college if that says anything) so I should be able to figure this out. I just have a hard time doing this by reading a bunch of forum posts - this just makes me more confused. After reading a dozen or so posts on the same topic I don't know which way of the computer is up.

You want me to copy my commands in the terminal so you can tell me what I did wrong: I don't even know how to do that. Another thing that is baffling is I can login to the little terminal emulator in "accessories" but I can't login to the big terminal I get from the keyboard shortcut. It says my password is incorrect.

---

### Post by oldfred on 2015-12-03
Knowing password is essential. It is the password you typed in twice during install.

       [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

Copy and paste is no different than anywhere else even Windows.
I open terminal, from my notes, since not good at remembering commands pasted into terminal and then copy & pasted here:

```
fred@trusy-ar:~$ uname -a
Linux trusy-ar 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
fred@trusy-ar:~$ 

```

---

### Post by greg_s3 on 2015-12-03
sudo tar cvf /media/greg/backup/home.tar /home is what I typed, and I got tar: /media/greg/backup/home.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by oldfred on 2015-12-03
I have not used tar.
Does /media/greg/backup exist?
Usually your flash drive or external drive is mounted in /media/greg using the label of the flash drive. 
ls /media/greg

More info on tar:
 [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)
HowTo: Full backup with tar (older but tar has not changed)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
/home with tar - matthew
[http://ubuntuforums.org/showthread.php?t=1964130](http://ubuntuforums.org/showthread.php?t=1964130)

---

### Post by kurt18947 on 2015-12-04
Depending on how paranoid you are about privacy, Firefox sync works pretty well. I don't back up passwords - there are tools to back those up locally - but everything else syncs & restores pretty faithfully. Thunderbird has an import-export addon that can back up &  entire profiles or just email.

---

### Post by greg_s3 on 2015-12-04
I used this command in the terminal: 
sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --one-file-system / 

I think finally I managed to create a tar file with this because a bunch of information ran down the terminal then I found the backup.tar.gz file in my home folder. After this I put a flash drive in the USB port of my computer and dragged the backup.tar.gz file into the window that came up which apparently copied it onto the flash drive so I closed thatwindow and pulled the flash drive out. Did I do this correctly?

---

### Post by Bucky Ball on 2015-12-04
Did you unmount the USB before pulling it out? If not, plug it back in and see if it mounts.

---

### Post by greg_s3 on 2015-12-04
I don't know what you mean by Unmount but I closed the window before pulling it out. I put the flash drive back in again just now and the tar file is still in the window that popped up.

---

