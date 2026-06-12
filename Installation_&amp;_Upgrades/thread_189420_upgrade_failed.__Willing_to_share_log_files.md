---
title: "upgrade failed.  Willing to share log files"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by itismike on 2006-06-05
I attempted to upgrade from Breezy to Dapper using the Update Manager but it froze and stopped responding with about 30 minutes remaining.  During the download, I did open Evolution to check my email and this is when the system froze:  the mouse moved and keyboard caps light responded, but I could not focus any windows nor get to a new login using ctrl-alt-F1.  After waiting and not seeing any activity, I forced the PC off.

Upon reboot, it stops responding at "Loading pcmcia..."

I plan to start from a fresh install and delete my previous system (except for the /home folder).  Would any of these files (or others) be useful for debugging purposes?

-Mike

-rw-r-----  1 root adm      5486 2006-06-05 03:28 acpid
-rw-r-----  1 root root      145 2006-06-04 11:36 acpid.1.gz
drwxr-xr-x  2 root root     4096 2006-06-04 11:36 apache/
-rw-r-----  1 root adm      5806 2006-06-05 01:17 auth.log
-rw-r-----  1 root adm     62105 2006-06-04 11:37 auth.log.0
drwxr-xr-x  2 root root     4096 2006-06-04 11:36 cups/
-rw-r-----  1 root adm       110 2006-06-05 01:55 daemon.log
-rw-r-----  1 root adm         0 2006-06-04 11:40 debug
-rwxr-xr-x  1 root root    17619 2006-06-04 22:56 dist-upgrade-apt.log*
-rw-r--r--  1 root root    24914 2006-06-05 03:24 dist-upgrade.log
-rw-r--r--  1 root root   277775 2006-06-05 03:28 dist-upgrade-term.log
-rw-r-----  1 root adm    736886 2006-06-05 03:28 dpkg.log
-rw-r--r--  1 root root    16383 2006-06-04 23:39 evms-engine.1.log
-rw-r--r--  1 root root    16383 2006-06-04 23:37 evms-engine.2.log
-rw-r--r--  1 root root    16383 2006-06-04 23:35 evms-engine.3.log
-rw-r--r--  1 root root    16383 2006-06-04 23:41 evms-engine.log
drwxr-s---  2  114 adm      4096 2006-06-04 11:36 exim4/
-rw-r-----  1 root adm   8652418 2006-06-05 01:56 kern.log
-rw-r-----  1 root adm  14495897 2006-06-04 11:37 kern.log.0
-rw-r-----  1 root adm   8663234 2006-06-05 01:56 messages
-rw-r-----  1 root adm  14501602 2006-06-04 11:37 messages.0
drwxr-x---  2 root adm      4096 2006-06-04 11:36 samba/
-rw-r--r--  1 root root    55105 2006-06-05 03:28 scrollkeeper.log
-rw-r-----  1 root adm   8667036 2006-06-05 01:56 syslog
-rw-r-----  1 root adm  14509137 2006-06-04 11:37 syslog.0
-rw-r-----  1 root adm     10602 2006-06-05 01:56 user.log
-rw-r-----  1 root adm     13123 2006-06-04 11:37 user.log.0
-rw-rw-r--  1 root utmp     3072 2006-06-04 22:53 wtmp

---

### Post by ubuntu_demon on 2006-06-05
If you want to fix it instead go here :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Also make sure to take a look at the other stickies!

Report errors back here.

---

### Post by itismike on 2006-06-06
You guys don't even know how cool you are!!  My system is now restored 100%, thanks to the well-written instructions on the links you directed me to.  

It got worse before it got better, because in an effort to recover my /home folder, I was having difficulty copying the original files and I figured I could just make all the files ugo +rwx.  The problem was that I think I may have executed that at the root of my system, hence:

```
 sudo  chmod  -R  777  /mnt/logicalVolume/root/
 sudo  chown  -hR  root:root  /mnt/logicalVolume/root/ 
```
was NOT a very smart thing to do.  I couldn't log into my user account until I set things back to:
```
  sudo sudo  chmod  -R  700  /mnt/logicalVolume/root/home/michael/ 
```

and I couldn't use sudo until I repaired it allong with etc/sudoers:

```
  chmod  4111  /mnt/logicalVolume/root/usr/bin/sudo
  visudo  -f  /mnt/logicalVolume/root/etc/sudoers   [added myself]
  chown  root:root /mnt/logicalVolume/root/etc/sudoers 
```

But now I'm doing ok.  Thanks so much for the guidance!!
-Mike

---

### Post by ubuntu_demon on 2006-06-06
[QUOTE=itismike]You guys don't even know how cool you are!!  My system is now restored 100%, thanks to the well-written instructions on the links you directed me to.  

It got worse before it got better, because in an effort to recover my /home folder, I was having difficulty copying the original files and I figured I could just make all the files ugo +rwx.  The problem was that I think I may have executed that at the root of my system, hence:

```
 sudo  chmod  -R  777  /mnt/logicalVolume/root/
 sudo  chown  -hR  root:root  /mnt/logicalVolume/root/ 
```
[/QUOTE]

If you have done that **all** the files on your system have these permissions :
-rwxrwxrwx   1 root root 

This means that all users can edit all files on your system! This is insecure!

Please check the permissions. If they are **all** messed in some way : IMHO the easiest way to get your original permissions back is reinstalling. (unless you had installed some program which kept track of all the file permissions in your system then you might be able to do/script something in order to restore them)

[QUOTE=itismike]
was NOT a very smart thing to do.  I couldn't log into my user account until I set things back to:
```
  sudo sudo  chmod  -R  700  /mnt/logicalVolume/root/home/michael/ 
```

and I couldn't use sudo until I repaired it allong with etc/sudoers:

```
  chmod  4111  /mnt/logicalVolume/root/usr/bin/sudo
  visudo  -f  /mnt/logicalVolume/root/etc/sudoers   [added myself]
  chown  root:root /mnt/logicalVolume/root/etc/sudoers 
```

But now I'm doing ok.  Thanks so much for the guidance!!
-Mike[/QUOTE]

If all your permissions are 777 this probably wouldn't cause errors but it would be totally insecure.

It can't hurt to make sure there are no problems with broken dependencies :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by itismike on 2006-06-06
I was desperate to copy my /home folder and don't remember where exactly I modified my permissions.  I'm sure the permissions under my /home folder are wrong, and when I couldn't run sudo I assumed that I botched the permissions in the rest of the system as well.  I just checked and it appears that my other system files have standard permissions:```
drwxr-xr-x 126 michael michael   8192 2006-06-06 07:22 ./
drwxr-xr-x  23 root    root      4096 2006-06-05 18:13 ../
drwxr-xr-x   8 michael michael   4096 2006-06-04 23:28 acpi/
-rw-r--r--   1 michael michael   2149 2006-02-19 11:12 adduser.conf
-rw-r--r--   1 michael michael     47 2006-06-05 23:07 adjtime
-rw-r--r--   1 michael michael     68 2006-05-15 01:25 aliases
drwxr-xr-x   2 michael michael   4096 2006-06-06 07:22 alternatives/
-rw-r--r--   1 michael michael    364 2005-05-02 22:10 anacrontab
drwxr-xr-x   3 michael michael   4096 2006-06-05 18:09 apache/
drwxr-xr-x   7 michael michael   4096 2006-02-19 11:22 apm/
drwxr-xr-x   4 michael michael   4096 2006-06-05 13:44 apt/
-rw-r-----   1 michael michael    144 2005-08-04 10:47 at.deny
-rw-r--r--   1 michael michael   1351 2006-04-21 18:51 bash.bashrc
-rw-r--r--   1 michael michael 193377 2006-04-21 18:51 bash_completion
```
so maybe I'm ok.  I'll check for dependencies later - thanks for the tip.

-Mike

---

### Post by ubuntu_demon on 2006-06-07
If only the permissions of /home/username was messed up it wouldn't be a problem.

I think you just posted a part of /etc Almost all files under / should be owned by root. In your current situation they might all be owned by your user micheal which is a big security risk.

IMHO it's best to backup your personal files and reinstall to make sure everything is how it should be and you don't have some other permissions wrong somewhere. Uncertainty about whether permissions are as they should be is a security risk which IMHO isn't acceptable.

---

### Post by itismike on 2006-06-07
You are correct, and I am stubborn.  Obviously what I did is not easily trackable since I made the modifications from a bootable CD so there is no 'history' file to check, and my memory of what I did is not clear.  I attempted to check the modification times of the files, but apparently chown doesn't count as file access  (ls  -lu  does not show the time a file was chown'ed.  Is there another timestamp I can extract?)

But since the permissions on files outside of /home seem normal and the ownership does not, I think I can safely assume that I did the chown -hR * command as indicated earlier.  What would be the risk of doing the following?```
 sudo  chown  -hR  root:root  /
(excluding /home, of course)
```

---

### Post by itismike on 2006-06-15
I went ahead and did a complete reinstall.  The only problem I had was with Evolution.  Other programs 'just worked' when I copied the entire application folder from my old home account to the new account (Mozilla Firefox and Gaim), but Evolution didn't seem to recognize itself.

I ended up manually copying each individual file over from my backup to the new .evolution/ folder.  

Ubuntu_demon - thanks for steering me in the right direction.
Mike

---

### Post by ubuntu_demon on 2006-06-16
[QUOTE=itismike]I went ahead and did a complete reinstall.  The only problem I had was with Evolution.  Other programs 'just worked' when I copied the entire application folder from my old home account to the new account (Mozilla Firefox and Gaim), but Evolution didn't seem to recognize itself.

I ended up manually copying each individual file over from my backup to the new .evolution/ folder.  

Ubuntu_demon - thanks for steering me in the right direction.
Mike[/QUOTE]
No problem and glad to be of help :)

---

