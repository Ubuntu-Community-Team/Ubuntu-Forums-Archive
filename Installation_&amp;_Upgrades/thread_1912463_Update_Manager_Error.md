---
title: "Update Manager Error"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by mouse- on 2012-01-20
I began installing updates a week ago while I was in the airport, but I had to power down my computer before the updates finished as my flight began boarding.  When I attempt to update now, the update manager stops just before completion with an error message and installs no updates.  When I viewed the details of the error message, it said that the error occurred while it was reading the archive.  Does anyone know how to fix this?

---

### Post by Old_Grey_Wolf on 2012-01-20
You terminated the update; therefore, you probably have partial update files stored on your system. Try entering these commands to see if by eliminating the partial update files you are allowed to update. ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get upgrade
```

Post any errors you get between [ CODE] [ /CODE] tags (the # icon) when executing the commands.

---

### Post by mouse- on 2012-01-20
I ran the command through terminal once and it ran without error.  I then told Update Manager to check for updates so I could see if Update Manager was able to install updates again.  Update Manger found 9 updates and produced the same error message as before when I attempted to install them.  When I repeated the terminal commands, the terminal printed these lines at the end of the third command:
```
 The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
Thank you for your help.

---

### Post by Old_Grey_Wolf on 2012-01-20
What that is telling me is that you have a kernel upgrade available. sudo apt-get upgrade will not upgrade the kernel. To upgrade the kernel enter ```
sudo apt-get dist-upgrade
```

---

### Post by mouse- on 2012-01-21
I ran the command and got the following error message:
```
dpkg: error processing /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/mesg.1.gz', which is also in package sysvinit-utils 2.88dsf-13.10ubuntu4.1
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2012-01-21
you need to "force" the installation with dpkg

[http://www.debian-administration.org/articles/176](http://www.debian-administration.org/articles/176)

---

### Post by jerrrys on 2012-01-21
Give it a cleaning:

**Remove all the packages** 	from /var/cache/apt/archives and /var/cache/apt/archives/partial 	folders:  	  
[LIST]
[*]sudo apt-get clean
[/LIST]
 
[LIST]
[*]**Remove 	all expired packages** from /var/cache/apt/archives and 	/var/cache/apt/archives/partial that are no longer available for 	download:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoclean
[/LIST]
 "*Not available for download*" does not mean the user should save them - normally these files have been replaced or are no longer needed.  
 
[LIST]
[*]**Remove unneeded dependencies** 	which are no longer needed:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoremove
[/LIST]

---

### Post by mouse- on 2012-01-21
I ran these commands and still get an error when I try to upgrade.  Thank you for your help though.

---

### Post by mouse- on 2012-01-21
I attempted to force install the package and recieved the same error message as before, minus the last line.

---

### Post by Old_Grey_Wolf on 2012-01-21
Have you tried these commands?
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/sysvutils_2.86.ds1-14.1ubuntu45_i386.deb
sudo apt-get -f install
```

---

### Post by mouse- on 2012-01-21
I ran these commands and was able to finish upgrading.  Thanks!

---

### Post by Old_Grey_Wolf on 2012-01-21
Please mark thread as solved.

If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

Thank you.

---

