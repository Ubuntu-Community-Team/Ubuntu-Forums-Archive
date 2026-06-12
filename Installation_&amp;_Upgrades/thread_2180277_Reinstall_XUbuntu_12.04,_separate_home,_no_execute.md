---
title: "Reinstall XUbuntu 12.04, separate /home, no execute in home"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by mbogevik on 2013-10-12
After my system fails after SSD firmware upgrade, XUbuntu 12.04_64 needed to be reinstalled.  My /home is on a separate 3Tbyte drive, but after mounting this I no longer can execute programs in my /home/"user" folder.

My /etc/fstab contains /home mount :
UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home  ext4 auto,exec,users,rw,nodev,nosuid,noatime 0 2

I am sure I have sudo rights.  Also I have run "sudo chown -R ++ " and "sudo chmod -R 775 ++" to assure I have ownership of home and can execute files.
Finally I have verified executable flag on file I want to run

Opening terminal in program folder in my main home and trying to execute (sudo ./filename) does not work, no error message presented.

Any suggestions anyone ?

---

### Post by ajgreeny on 2013-10-12
My /home line in fstab is more simple than yours and was added during installation automatically.  I assume you have manually added yours after installing.
```
UUID=2a1a9b57-4d0a-4570-974f-d6114fb25ef1 /home           ext4    defaults        0       2
```
Perhaps that is the reason, though yours also seems to have all the options spelled out separately as needed.

Can we see the output of **ls -l** on a home folder which contains some of these executable files which won't execute, please.

Also you mention "after mounting", so I wonder how you mounted the /home folder; was it by rebooting or running **sudo mount -a** or some other way?

---

### Post by oldfred on 2013-10-12
I have seen this as correct settings for /home.

 chmod -R a+rwX,o-w /home/$USER
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

      
 .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.
 sudo service lightdm stop
sudo chown username:username ~/.Xauthority
sudo service lightdm start

---

### Post by mbogevik on 2013-10-12
Here is my ls -l  of Teamspeak folder and files in home :

motte2@motte3:~/teamspeak3-server_linux-amd64$ ls -l
total 16168
-rwxrwxr-x 1 motte2 motte2   40918 Aug  5 15:06 CHANGELOG
drwxrwxr-x 2 motte2 motte2    4096 Sep  9 22:28 doc
drwxrwxr-x 4 motte2 motte2    4096 Jul 15  2012 files
-rwxrwxr-x 1 motte2 motte2 4764140 Aug  5 15:06 libts3db_mysql.so
-rwxrwxr-x 1 motte2 motte2 5675839 Aug  5 15:06 libts3db_sqlite3.so
-rwxrwxr-x 1 motte2 motte2   23854 Aug  5 15:06 LICENSE
drwxrwxr-x 2 motte2 motte2   20480 Oct  4 00:18 logs
-rwxrwxr-x 1 motte2 motte2       1 Jul 15  2012 query_ip_blacklist.txt
-rwxrwxr-x 1 motte2 motte2      10 Jul 15  2012 query_ip_whitelist.txt
drwxrwxr-x 2 motte2 motte2    4096 Aug  5 15:06 redistributables
drwxrwxr-x 2 motte2 motte2    4096 Sep  9 22:27 serverquerydocs
drwxrwxr-x 4 motte2 motte2    4096 Sep  9 22:27 sql
-rwxrwxr-x 1 motte2 motte2       0 Oct 10 20:15 sudoers
-rwxrwxr-x 1 motte2 motte2 5760128 Aug  5 15:06 ts3server_linux_amd64
-rwxrwxr-x 1 motte2 motte2    1192 Aug  5 15:06 ts3server_minimal_runscript.sh
-rwxrwxr-x 1 motte2 motte2  216064 Oct  9 21:18 ts3server.sqlitedb
-rwxrwxr-x 1 motte2 motte2    3728 Aug  5 15:06 ts3server_startscript.sh
drwxrwxr-x 2 motte2 motte2    4096 Sep  9 22:25 tsdns

motte2@motte3:~$ ls -la .ICEauthority
-rw------- 1 motte2 motte2 26110 Oct 12 20:27 .ICEauthority

motte2@motte3:~$ ls -la .Xauthority
-rwxrwxr-x 1 motte2 motte2 161 Oct 12 20:27 .Xauthority


All suggestions is now tested/checked, but no change, still not able to execute files in home.
 What I think is the problem is that when the 3T HDD was mounted in old system it was a fresh install and home folder where copied over to a empty HDD.  Now when I installed a new XUbuntu I mount in the old home and something on a "higher level" stops me from executing files in home.

Is there any log somewhere where I can find the reason XUbuntu has for not executing files ?

---

### Post by mbogevik on 2013-10-13
Still trying to solve this...  As I have made a start script on boot for one of the two programs running in /home/user, I discovered this line in /var/log/dmesg.log :

[    6.460559] init: utorrent main process (835) terminated with status 126

As I found that this means I do not have execute permissions I assume my /home HDD mount allowing execute of files is overrided by something...

I have tried to run both my utorrent (32b)and Teamspeak 3 (64b) server in /usr/* and that seems to work, except for they do not function properly because configuration files point to wrong folder.  utorrent works "empty" but TS3 is not working.  I assume a clean install will solve this, but requires a lot of configuring, especially on TS3.

---

### Post by mbogevik on 2013-10-13
I now done a test without mounting HDD in /home by change line in /etc/fstab to comment.  I then copied one of the programs from HDD now mounted in /media into /home that now is on SSD.  Starting program now works fine.

Also I tried to copy some of the files on /home on SSD to my real /home now in /media, like .ICEauthority .Xauthority and some other .files in /home, no success...

I also tried to set permissions to my HDDs  /home when unmounted in /media (chown and chmod) but also this did not change anything.  (I assumed I would get access to change any file XUbuntu locked)

 Still looking for an answer, but the obvious solution seems closer, copy every file to my NAS storage, format the HDD and copy the SSD's /home on it from scratch with rsync...  But as HDD is 3T this really take some time...

---

### Post by mbogevik on 2013-10-13
I was wandering if anyone knows if XUbuntu does anything to /home folder that can get consequences for file execute if /home gets replaced with an old /home later.  Maybe I should have set this up during installation process (like this [http://ubuntuforums.org/showthread.php?t=1569675](http://ubuntuforums.org/showthread.php?t=1569675) ) instead of mounting my old /home in /etc/fstab after installation ?

---

### Post by mbogevik on 2013-10-13
Finally I found the solution.  I was thinking about the suggestion to use "defaults" when mounting in fstab.  I tested this and it works !  Thanks "ajgreeny" :)

This is wat I had :
UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home  ext4 auto,exec,users,rw,nodev,nosuid,noatime 0 2

First of all, reading carefully [https://help.ubuntu.com/community/Fstab#Options](https://help.ubuntu.com/community/Fstab#Options) again, first I discover I have used "users" as parameters, doc. says "user" is allowed.
I then thought through this as found that maybe mount as root-only was more logic, so I replaced it with "nouser".  This did the trick and I now have rights to execute files in /home.

Here is my working Fstab: 
UUID=bb6c7490-6333-494a-99bc-2b7005ec25c0 /home  ext4 auto,exec,nouser,rw,nodev,nosuid,noatime 0 2

This shows the importance of making a copy of Fstab file before doing a new installation when /home is on separate drive.

---

### Post by oldfred on 2013-10-13
Is this a timing issue? 
Or you are trying to run a script from /home before the system has mounted the file system.

---

### Post by mbogevik on 2013-10-16
I do not know what exact is happening here, but I have done tests to make sure of the difference.  When my Fstab-mount contains parameter "user" I am not able to execute anything in my /home (regardless of rights assigned to files and folders) but when mounting is done with "nouser" instead, I am allowed to execute files.  No file permission change was done between these test.
It may be a logic here that mounting a HDD as user many not be what I really wanted and limitations like this has some logic.

I guess I made myself a lot of extra work here as a result of me, sitting way too many hours in front of my computers, testing, over and over, even with XUbuntu 13.10 and Ubuntu server 13.10, and believed I have had tested suggestion from "ajgreeny" to mount with defaults.  It turned out I did not ...

---

