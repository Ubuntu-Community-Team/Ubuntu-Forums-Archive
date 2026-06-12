---
title: "Migrating to New Machine"
date: 2022-01-28
forum: Installation &amp; Upgrades
---

### Post by cobras on 2022-01-28
Greetings,

I know this topic has been covered many times, because I've done research before posting, but it seems that each instance requires a unique solution.

I have a Toshiba Satellite C55-A running on Ubuntu 20.04 alongside Windows and just purchased a used Asus VivoBook-X510QA.  I've managed to install Ubuntu 20 alongside Windows on the Asus, and am now posting from the "new" machine.

Ideally, I would now like to get all my data, programs and settings migrated from the old machine.  At the very least, I need all my folders.  I'm not totally ignorant or intimidated by computers but could use some help on this.

Thank you in advance.

---

### Post by oldfred on 2022-01-28
Do a new install & restore from your normal backup.
That also then is a good test that your backups include everything as you still have old system to get more data if needed.

You probably do not want system as its configuration may be different.
But you do want /home, a list of installed apps to make it easy to install them, and any other data partition(s) you have.
If you modified any system wide settings in /etc, you may want those, but new install may not need same settings. Best to review each.
And if you installed any server type apps like web, database or other, you have to include those from /. 

I use rsync to copy data, many do not consider that the best backup as it is just a copy and changes are not archived. But I rsync to multiple devies at different times and have copies in two states.

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 

If both connected locally, you can do an install, and rsync /home & data. And copy list of apps to use to reinstall.

---

### Post by cobras on 2022-01-29
> **oldfred said:**
> Do a new install & restore from your normal backup.
That also then is a good test that your backups include everything as you still have old system to get more data if needed.


I see the logic in this and certainly hope it really is this easy, but there's some blanks that need filling for me.

I have a recent backup done via deja dup.  What you suggest seems to imply that the backup is an executable file, which I would not have expected.  Is this so?  If so, how do I get it to my new machine?

Thanks so much for your time and consideration Fred.

---

### Post by oldfred on 2022-01-29
I have not used deja dup.
It looks like it is a front end for rsync, which I do use.
[https://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](https://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

You probably have to partition in advance, restore data and then reinstall kernel & grub.
Not sure what settings like in fstab for UUID of current system it will restore, if restoring /. But restoring /home should be relatively easy.
It does not look like it includes an export of installed apps. I normally do that just before running rsync, so my backup includes latest list of apps.

---

### Post by cobras on 2022-02-03
So I've given up on an easy solution and am just taking it one step at a time.  I've updated the system, installed media codecs, etc., and will customize the system to suit my needs as I go.  Now I need to transfer my files and folders and think FileZilla should work.

FileZilla Client is already on the old machine but can't get the Server installed on this new machine.  Wine is installed and FileZilla Client is downloaded.  The suggested command (sudo wine FileZilla_Server-*.exe) results in "Invalid Name".  I've tried spelling out the file name (FileZilla_Server_1.2.0_x86_64-linux-gnu.deb) in various configurations and get the same results.

Any suggestions?

---

### Post by rsteinmetz70112 on 2022-02-03
Just a thought. Is there a typo in the command FileZilla_Server-*.exe, should the "-" be a "_"? or should ".exe" be ".deb" if it is a deb then the .deb needs to be installed on Linux. If it really is a .deb then the install command would be sudo dpkg -i package_file.deb

---

### Post by cobras on 2022-02-03
> **rsteinmetz70112 said:**
> Just a thought. Is there a typo in he command FileZilla_Server-*.exe, should the "-" be a "_"? or should ".exe" be ".deb" if it is a deb then the .deb needs to be installed on Linux. If it really is a .deb then the install command would be sudo dpkg -i package_file.deb


The underscore instead of the dash was the first alternate I tried.  Also tried the .exe.  I'll see about installing .deb.  Thanks.

---

### Post by cobras on 2022-02-03
_*sudo dpkg -i FileZilla_Server_1.2.0_x86_64-linux-gnu.deb*_ seems to have worked.  But I can't find FileZilla on the machine even after rebooting.

I see no way to attach  screenshot of my terminal.

---

### Post by oldfred on 2022-02-03
I use rsync as once I get command correct, it is easy to put into a script.

Simple manual rsync & rdiff theFu
[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)
What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 

This was the one I started with, but over time have added details.
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 

Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) &

---

### Post by cobras on 2022-02-09
It took days but I did manage to hack it done.  I'm just about completely settled in my new machine with most of the apps I'll need and all my data.

And it was a hack.  UGLY what I did.  Not illeagal but definitely frowned upon and UGLY.

---

