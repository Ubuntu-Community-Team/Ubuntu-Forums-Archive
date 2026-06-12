---
title: "Ubuntu Crashing and programs close automatically."
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by David2569 on 2007-08-15
I installed some packages but something went wrong, every time i open a program it sometimes closes without warning and ubuntu is crashing a lot. i went in terminal to fix the problem as i was told to do. I type "sudo apt-get -f install" and i got this error:
--------------------------------------------------------------------------------------------------------------------------------
david@david-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  python2.4
Suggested packages:
  python2.4-doc python-profiler
The following NEW packages will be installed
  python2.4
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B/2797kB of archives.
After unpacking 9519kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 25610 package `xserver-xorg-input-mouse':
 `Replaces' field, invalid package name `xs%rver-xorg': character `%' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
david@david-desktop:~$ 
--------------------------------------------------------------------------------------------------------------------------------

How do i fix this? Any help will be appreciated.

---

### Post by heimo on 2007-08-15
> **David2569 said:**
> dpkg: parse error, in file `/var/lib/dpkg/status' near line 25610 package `xserver-xorg-input-mouse':
 `Replaces' field, invalid package name `xs%rver-xorg': character `%' not allowed (only letters, digits and characters `-+._')

Open /var/lib/dpkg/status file in gedit
```
gksudo gedit /var/lib/dpkg/status
```

and change xs%rver-xorg to xserver-xorg (search for it, file may be quite large). Save and run "sudo apt-get -f install" again.

---

### Post by David2569 on 2007-08-15
I did as you said and when i typed " apt-get -f install" again i got this:

------------------------------------------------------------------------------------------------------------------------------------
root@david-desktop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  openoffice.org-help-pt-br python2.4
Suggested packages:
  python2.4-doc python-profiler
The following NEW packages will be installed
  python2.4
The following packages will be upgraded:
  openoffice.org-help-pt-br
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/13.2MB of archives.
After unpacking 9519kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 6606 package `sound-juicer':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@david-desktop:~# 
-------------------------------------------------------------------------------------------------------------------------------

---

### Post by heimo on 2007-08-15
> **David2569 said:**
> I did as you said and when i typed " apt-get -f install" again i got this:

Ok, that's bad. But luckily, there's backup file of status. Next you should try to use it. Run these commands:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get -f install

```

---

### Post by David2569 on 2007-08-15
Did as you said and got this:

-----------------------------------------------------------------------------------------------------------------------------------
root@david-desktop:~# mv /var/lib/dpkg/status /var/lib/dpkg/status_broken
root@david-desktop:~# mv /var/lib/dpkg/status-old /var/lib/dpkg/status
root@david-desktop:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  python2.4
Suggested packages:
  python2.4-doc python-profiler
The following NEW packages will be installed
  python2.4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/2797kB of archives.
After unpacking 9519kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 131349 files and directories currently installed.)
Unpacking python2.4 (from .../python2.4_2.4.4-2ubuntu7_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python2.4_2.4.4-2ubuntu7_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4_2.4.4-2ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@david-desktop:~# 
-------------------------------------------------------------------------------------------------------------------------------

---

### Post by heimo on 2007-08-15
> **David2569 said:**
> /var/cache/apt/archives/python2.4_2.4.4-2ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@david-desktop:~# 


There's still some hope. :-) That's actually a bit better than status file being broken. This is what I'd suggest you to run - but be aware, I haven't tested this and if the remove part suggest to remove half of your system, do not accept it. In that case there may be better way to do it (perhaps with apt-get --reinstall python2.4, without first purging it).
```
cd
mkdir broken_files
mv /var/lib/dpkg/info/python2.4.* broken_files
apt-get --purge remove python2.4
apt-get install python2.4

```

---

### Post by David2569 on 2007-08-15
did what u said and i got this, Not sure if i did something wrong though.:

-----------------------------------------------------------------------------------------------------------------------------------
root@david-desktop:~# cd
root@david-desktop:~# mkdir broken_files
root@david-desktop:~# mv /var/lib/dpkg/info/python2.4.* broken_files
mv: cannot stat `/var/lib/dpkg/info/python2.4.*': No such file or directory
root@david-desktop:~# apt-get --purge remove python2.4
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
root@david-desktop:~# apt-get install python2.4
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
root@david-desktop:~# 
-----------------------------------------------------------------------------------------------------------------------------------

---

### Post by heimo on 2007-08-15
It's possible I made a mistake with that python* part, but the error about missing status file isn't too promising. You should run
```
ls -l /var/lib/dpkg/status*
```

How many files do you see? We should've copied instead of moving in that other step earlier, so that we could now have a backup of the status file. But ... where did it go? I hope it's still there.

---

### Post by heimo on 2007-08-15
If the status file no longer exists, I'd try:
```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
```

And then the -f install thingy.

---

### Post by David2569 on 2007-08-15
I did this command "ls -l /var/lib/dpkg/status*" and i got this

-------------------------------------------------------------------
root@david-desktop:~# ls -l /var/lib/dpkg/status*
-rw-r--r-- 1 root root 1334490 2007-08-14 21:40 /var/lib/dpkg/status~
-rw-r--r-- 1 root root 1334453 2007-08-15 14:08 /var/lib/dpkg/status_broken
-rw-r--r-- 1 root root 1334453 2007-08-14 21:39 /var/lib/dpkg/status-old
root@david-desktop:~# 
-----------------------------------------------------------------------

I'm not sure if you still want to run this last command though
 "sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status"

---

### Post by heimo on 2007-08-15
> **David2569 said:**
> I'm not sure if you still want to run this last command though
 "sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status"

Yeah, but before that - you could also take a backup of the ~ ending file.
```
sudo cp /var/lib/dpkg/status~ /var/lib/dpkg/status_lostone
```

I believe it's a backup made by text editor - of the one we just lost for some reason. But you could now try to copy status file from /var/backups, and then run the "-f install" stuff to see how broken your system still is. :-) Let's hope it's a good copy. If not, and you run into errors about status file, you could copy "lostone" to your current status file and try again. 

If you get errors about python2.4, try reinstalling it. It's not so much about the actual python files, but the debian package managament / package database and install / uninstall scripts which seem to have corrupted.
```
sudo apt-get --reinstall install python2.4
```

---

