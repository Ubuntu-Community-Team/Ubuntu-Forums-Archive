---
title: "New install vs upgrade"
date: 2018-07-02
forum: Installation &amp; Upgrades
---

### Post by shersk on 2018-07-02
I have Xubuntu 17.10 and want to upgrade it to version 18.04 LTS. Should I use the upgrade procedure, or do a completely new install?

I have made a backup of the entire / partition as well as the /home partition. What are the pros and cons of either procedure?

If I do a new install of 18.04 on / partition, I'll probably have to reinstall a lot of software and do a lot of configuration post-install. However, my computer has become very slow in recent years, and I have a feeling that if I do a new install on the / partition, the system will run more smoothly.

---

### Post by Autodave on 2018-07-02
New install. I have rarely had any luck doing upgrades: maybe works one out of 10 times (I have a bunch of machines).

---

### Post by oldfred on 2018-07-02
I did upgrades from 6.06 thru 9.04. But then changed to new install into a smaller / (root) of about 25GB. And I kept old install in case my backups did not have everything I wanted.
But most of your data is in /home, only some system wide settings are in /etc. I now try to remember to copy and manually edited /etc file into /home or my /mnt/data partition so I have it.
I also export a list of installed apps, so with higher speed Internet, it is easy to reinstall all of them.

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

### Post by shersk on 2018-07-02
Excellent. I'm going through the links now. For me, it's of special concern to keep my mysql databases intact, and they are located under /var  .

---

### Post by oldfred on 2018-07-02
If you have any server type applications like your mysql, then you have to pay attention to those separately. 
But you should have backup procedures for all of that anyway.

---

### Post by shersk on 2018-07-03
I understand. Well, my question was what the pros and cons are, and it seems to me that the pros and cons of doing a new install are that the system will work without problems but that it involves a lot of under-the-hood tinkering in order to set up the user applications with all their configurations. The pros and cons of an upgrade: that there is not so much tinkering with applications, most will just work, but that the ubuntu itself might need some adjustments. So far I have chosen to do upgrades, mainly because of "fear of the unknown" and since I don't like tinkering. I prefer to not have to manually edit configuration files. The problem I have now is that the computer seems to be much slower than it used to, and I think a new install might improve its performance.

---

### Post by oldfred on 2018-07-03
For desktops all the application data & settings are in /home. With server applications those may in somewhere in / (root). But with a new install, you do have to reinstall all the applications.

A new install also becomes a major houseclean. But I normally run a small script to run several command line tasks to update system, empty trash, purge some data, & delete old log files. But still find new install is a lot smaller that my main working install.

---

### Post by shersk on 2018-07-03
I have done the new install now, and it's working. But the problem I have now is typical of what I want to avoid: I can't log in as root in mysql (to restore from backup). I have tried two different procedures for resetting root password so far, and they didn't work. I'm sure I'll find out eventually how to reset the password, but it's this kind of tinkering that I'd like to avoid.

---

### Post by oldos2er on 2018-07-03
I haven't had any problem using do-release-upgrade on Xubuntu for the past several versions,  for what it's worth. If your data is backed up that's a plus.

---

