---
title: "Forced distribution upgrade"
date: 2007-03-21
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-03-21
I keep getting a notification, when either running the update manager manually, or when clicking on the update notification, indicating:

"Not all updates can be installed

"Run a distribution upgrade, to install as many updates as possible.

This can be caused by an uncompleted upgrade, unofficial software packages, or by running a development version.

[Distribution Upgrade] [Close]
"

Can anyone tell me how to approach fixing this?

---

### Post by JarG0n on 2007-03-21
I just noticed after closing the distribution upgrade in the update manager, that there exists a "Distribution update" that has not been installed.  It has been there for quite some time, before the forced Distribution Upgrade notices started occurring.

"Distribution updates"

libggi2
General Graphics interface runtime libraries
From version 1:2.0.5-1.1ubuntu2 to 1:2.2.1-4ubuntu1 (Size: 470 KB)"

I have never been able to even select/unselect this checkbox.  It won't go away.  There was an Mplayer upgrade that went along side this Distribution Update that appears to have disappeared from along side this seemingly permanent entry.

JarG0n

---

### Post by bapoumba on 2007-03-21
Hello,
please post your sources.list:
```
cat /etc/apt/sources.list
```

From the error message, you should run:
```
sudo aptitude dist-upgrade
```
make sure you have no non-ubuntu repos in your sources.list.

---

### Post by JarG0n on 2007-03-21
## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main multiverse restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main multiverse restricted
##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by JarG0n on 2007-03-21
I don't know exactly what you mean by "From the error message, you should run", but I ran this command from terminal and it seemed to install the update that didn't want to go through.

sudo aptitude dist-upgrade 

Does the sources.list look ok?  I'm not using any non-ubuntu sources that I can see.

---

### Post by JarG0n on 2007-03-21
Ok, after running sudo aptitude dist-upgrade, I started the Update Manager again, and it gave me the same message about running a distribution upgrade.

"Not all updates can be installed'

:(

---

### Post by bapoumba on 2007-03-21
Please open your file with nano (a small text editor)
```
sudo nano -B /etc/apt/sources.list
```

[COLOR="Red"]Remove[/COLOR] what is in red and [COLOR="Green"]add[/COLOR] what is in green

> **JarG0n said:**
> ## Major bug fix updates produced after the final release of the
## distribution.
[COLOR="Red"]deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main multiverse restricted [COLOR="Green"]universe[/COLOR]

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main multiverse restricted
##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main [COLOR="Green"]universe multiverse[/COLOR]
[COLOR="Green"]# [/COLOR]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
Save the file with CTRL-O (same name, hit <enter>)
Exit nano with CTRL-X

run:
```
sudo aptitude update
sudo aptitude dist-ugrade
```

edit : remove also the us. in the edgy-update repo (line below the cdrom in red)

---

### Post by JarG0n on 2007-03-21
Result from: sudo aptitude update

Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Result from: sudo aptitude dist-ugrade

asenn@asenn-desktop:~$ sudo aptitude dist-ugrade
Unknown command "dist-ugrade"

 This aptitude does not have Super Cow Powers.



lol !!

Thanks for your help!  We're not there yet, but getting close I think.

---

### Post by bapoumba on 2007-03-21
> **JarG0n said:**
> Result from: sudo aptitude update

Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Could you please paste your sources.list again ? The security repos for universe appears t be in duplicate from the error message, but I do not see it from the sources.list you've posted. 

> **JarG0n said:**
> 
Result from: sudo aptitude dist-ugrade

sudo aptitude dist-u**p**grade, sorry there was a typo i my previous post :/

---

### Post by etank on 2007-03-21
On the third line from the bottom
```

deb http://security.ubuntu.com/ubuntu/ edgy-security [COLOR="Red"]universe[/COLOR] main [COLOR="Red"]universe[/COLOR] multiverse

```
universe is listed twice (see the red). Remove one of them and then
```

sudo aptitude update
sudo aptitude dist-upgrade

```

---

### Post by JarG0n on 2007-03-22
It seems I'm no longer getting the duplicate, or forced distribution upgrade messages.  Thanks guys!

Where do I find the rules surrounding proper configuration of sources.list ?

Here's my sources.list after I removed the extra 'universe' that etank asked me to remove.

```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main multiverse restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

##deb http://security.ubuntu.com/ubuntu edgy-security main multiverse restricted
##deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://security.ubuntu.com/ubuntu/ edgy-security main universe multiverse
#deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

Here's the result of the upgrade.

```
asenn@asenn-desktop:~$ sudo nano -B /etc/apt/sources.list
Password:
asenn@asenn-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
asenn@asenn-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]                         
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                   
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US         
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy/main Translation-en_US            
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US      
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]   
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US        
Hit http://archive.ubuntu.com edgy Release     
Get:4 http://security.ubuntu.com edgy-security Release [50.9kB]
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://us.archive.ubuntu.com edgy-updates Release                   
Hit http://archive.ubuntu.com edgy/universe Packages                       
Hit http://us.archive.ubuntu.com edgy-updates/main Packages           
Get:5 http://security.ubuntu.com edgy-security/main Packages [67.2kB]
Hit http://archive.ubuntu.com edgy/main Packages                           
Hit http://archive.ubuntu.com edgy/multiverse Packages                      
Hit http://archive.ubuntu.com edgy/restricted Packages                      
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages           
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Get:6 http://security.ubuntu.com edgy-security/universe Packages [33.3kB]
Get:7 http://security.ubuntu.com edgy-security/multiverse Packages [3786B]
Fetched 155kB in 5s (28.4kB/s)   
Reading package lists... Done
asenn@asenn-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  file libmagic1 libmysqlclient15off mysql-client-5.0 mysql-common 
  mysql-server-5.0 
6 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.0MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://security.ubuntu.com edgy-security/main file 4.17-2ubuntu1.1 [31.3kB]
Get:2 http://security.ubuntu.com edgy-security/main libmagic1 4.17-2ubuntu1.1 [276kB]
Get:3 http://security.ubuntu.com edgy-security/main mysql-common 5.0.24a-9ubuntu0.1 [42.3kB]
Get:4 http://security.ubuntu.com edgy-security/main libmysqlclient15off 5.0.24a-9ubuntu0.1 [1760kB]
Get:5 http://security.ubuntu.com edgy-security/main mysql-client-5.0 5.0.24a-9ubuntu0.1 [6956kB]
Get:6 http://security.ubuntu.com edgy-security/main mysql-server-5.0 5.0.24a-9ubuntu0.1 [24.9MB]
Fetched 34.0MB in 1m43s (327kB/s)                                               
Preconfiguring packages ...
(Reading database ... 158515 files and directories currently installed.)
Preparing to replace file 4.17-2ubuntu1 (using .../file_4.17-2ubuntu1.1_i386.deb) ...
Unpacking replacement file ...
Preparing to replace libmagic1 4.17-2ubuntu1 (using .../libmagic1_4.17-2ubuntu1.1_i386.deb) ...
Unpacking replacement libmagic1 ...
Preparing to replace mysql-common 5.0.24a-9 (using .../mysql-common_5.0.24a-9ubuntu0.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient15off 5.0.24a-9 (using .../libmysqlclient15off_5.0.24a-9ubuntu0.1_i386.deb) ...
Unpacking replacement libmysqlclient15off ...
Preparing to replace mysql-client-5.0 5.0.24a-9 (using .../mysql-client-5.0_5.0.24a-9ubuntu0.1_i386.deb) ...
Unpacking replacement mysql-client-5.0 ...
Preparing to replace mysql-server-5.0 5.0.24a-9 (using .../mysql-server-5.0_5.0.24a-9ubuntu0.1_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Stopping MySQL database server mysqld                                 [ ok ] 
Unpacking replacement mysql-server-5.0 ...
Setting up libmagic1 (4.17-2ubuntu1.1) ...

Setting up file (4.17-2ubuntu1.1) ...
Setting up mysql-common (5.0.24a-9ubuntu0.1) ...
Setting up libmysqlclient15off (5.0.24a-9ubuntu0.1) ...

Setting up mysql-client-5.0 (5.0.24a-9ubuntu0.1) ...
Setting up mysql-server-5.0 (5.0.24a-9ubuntu0.1) ...
 * Stopping MySQL database server mysqld                                 [ ok ] 
 * Starting MySQL database server mysqld                                 [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

```

---

### Post by bapoumba on 2007-03-22
Here you can find complete sources.list:
[http://psychocats.net/ubuntu/sources]("http://psychocats.net/ubuntu/sources")

Installing packages:
[https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")
[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

