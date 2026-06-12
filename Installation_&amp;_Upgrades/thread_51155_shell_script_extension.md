---
title: "shell script extension??"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by chinabright on 2005-07-22
**hi ok how do i rename a program to the shell script extesion so i can get it to install thanks**   :mrgreen:  [COLOR=Teal]LOVE YOU!![/COLOR]

---

### Post by DJ_Max on 2005-07-22
Do you been .sh?

```

mv oldfile newfilename.sh
```

BTW, to excute it, you need to make it excutable.
```
chmod a+x newfile.sh
```

---

### Post by chinabright on 2005-07-22
**ok that does something ut it says:** 
mv: missing file argument more help please it is the java program form sun i am talking about
i renamed it to just java.bin but even that didtn help

---

### Post by DJ_Max on 2005-07-22
Wait, what are you trying to do? Install what?

---

### Post by chinabright on 2005-07-22
**just trying to get my java runtime running** LINUX kicks my butt!!! \\:D/

---

### Post by DJ_Max on 2005-07-22
So what did you download? Because changing the extension probably won't do anything. If you're trying to install Java.

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

You may need the extra repositories. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by chinabright on 2005-07-22
right thast unoffical guide is good for lots of things but in this case it doesnt work as it should i downloaded the jre-1_5_0_04-linux-i586-rpm.bin is the name on my desktop before i changed it.

---

### Post by chinabright on 2005-07-22
right thast unoffical guide is good for lots of things but in this case it doesnt work as it should i downloaded the jre-1_5_0_04-linux-i586-rpm.bin is the name on my desktop before i changed it.

---

### Post by chinabright on 2005-07-22
# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
 ](*,) 
thats all i get from the guide site

---

### Post by chinabright on 2005-07-22
[QUOTE=chinabright]# apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
 ](*,) 
thats all i get from the guide site[/QUOTE]
 # java -version
java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
in case you were wondering thank you for helping me

---

### Post by DJ_Max on 2005-07-22
You already have Java 1.4.1

Look here
[http://ubuntuforums.org/showthread.php?t=50923](http://ubuntuforums.org/showthread.php?t=50923)

---

### Post by chinabright on 2005-07-22
would someone patient enough with a newbie likw me help me pretty please   :razz:

---

### Post by chinabright on 2005-07-22
it says the updated repository doenst exist
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restric Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restric_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
chinabright@ip68-108-217-218:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
sheesh !!!

---

### Post by chinabright on 2005-07-22
: Some index files failed to download, they have been ignored, or old ones used instead.
chinabright@ip68-108-217-218:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restric Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restric_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
chinabright@ip68-108-217-218:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
now what hombre
almost there i hoping

---

### Post by chinabright on 2005-07-22
gosh i didnt mean to post htat twice i just didnt notice it went to page 2 sorry i really not trying ot be pushy i just feel like linux kicks my butt all day long. on the plus side today i learned how to uncoment a line what the shell extesion is in renameing a file and how to chomd a+x thanks dj for al your help

---

### Post by DJ_Max on 2005-07-22
It's
```
sudo apt-get update
```

---

### Post by chinabright on 2005-07-22
duh sudo right, ok this still happens when i sudo apt-get update
: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restric Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restric_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
chinabright@ip68-108-217-218:~$

---

### Post by DJ_Max on 2005-07-22
Hrmm,
Post your /etc/apt/sources.list

---

### Post by DJ_Max on 2005-07-22
This may also be your problem, as there seems to be an issue with the servers.
[http://ubuntuforums.org/showthread.php?t=46459&page=2&pp=10](http://ubuntuforums.org/showthread.php?t=46459&page=2&pp=10)

Go to [http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)
Try to replace the mirrormax URI with another one, such as [ftp://ftp2.caliu.info/backports](ftp://ftp2.caliu.info/backports)

---

### Post by chinabright on 2005-07-22
how do i pull up my list in comand lingo

---

### Post by DJ_Max on 2005-07-22
[QUOTE=chinabright]how do i pull up my list in comand lingo[/QUOTE]
 ```
nano -w /etc/apt/sources.list
```
That opens it up with the nano text editor

OR

```
cat /etc/apt/sources.list
```

---

### Post by chinabright on 2005-07-22
i had to go to the store but im back thanks more comands 
this is my list
# Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

---

### Post by DJ_Max on 2005-07-22
Try changing it to:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
```

---

### Post by DJ_Max on 2005-07-22
It seems you may be in trouble.
[http://ubuntuforums.org/showthread.php?p=267792](http://ubuntuforums.org/showthread.php?p=267792)

---

### Post by chinabright on 2005-07-22
how do i save the changes in nano

---

### Post by DJ_Max on 2005-07-23
[QUOTE=chinabright]how do i save the changes in nano[/QUOTE]
control + o

OR

control + x 

to exit, it will then prompt if you wanna save, type 'y' then hit enter

BTW, you needed root privleges to edit that file.
```
sudo nano -w /etc/apt/sources.list
```

---

