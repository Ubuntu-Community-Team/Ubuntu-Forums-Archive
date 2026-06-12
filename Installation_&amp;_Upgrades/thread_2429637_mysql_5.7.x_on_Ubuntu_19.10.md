---
title: "mysql 5.7.x on Ubuntu 19.10"
date: 2019-10-21
forum: Installation &amp; Upgrades
---

### Post by julesou on 2019-10-21
Good afternoon,

When upgrading from 19.04 to 19.10 I had some issues with mysql hanging up the installer, eventually I completely removed mysql and reinstalled. Then I found out that I now have mysql 8.x, which is a problem, I need 5.7.x for an application I develop for (Liferay 7.0). I cannot find mysql 5.7.x with apt search, so I tried installing the debs I found on the oracle download page. This gives an issue with apparmour.

All together, a lot of hassle which I hopefully can avoid... So, the question is: how can I install mysql server (plus client) 5.7.x on Ubuntu 19.10? Is there a ppa somewhere?

TIA!

---

### Post by julesou on 2019-10-21
I tried this approach [https://dev.mysql.com/downloads/repo/apt/](https://dev.mysql.com/downloads/repo/apt/) but setting it to 5.7 but this gives

```
sudo apt-get update                                                                                                                                              &#57522; &#10004;
Hit:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) eoan InRelease
Hit:2 [http://repo.mysql.com/apt/ubuntu](http://repo.mysql.com/apt/ubuntu) eoan InRelease                                                                                       
Hit:3 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) eoan-updates InRelease                                                                            
Hit:4 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) eoan-backports InRelease                                          
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease                                             
Reading package lists... Done
W: Skipping acquire of configured file 'mysql-5.7/source/Sources' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/binary-amd64/Packages' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/binary-i386/Packages' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/i18n/Translation-en_US' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/i18n/Translation-en' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/dep11/Components-amd64.yml' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/dep11/icons-48x48.tar' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/dep11/icons-64x64.tar' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'mysql-5.7/cnf/Commands-amd64' as repository 'http://repo.mysql.com/apt/ubuntu eoan InRelease' doesn't have the component 'mysql-5.7' (component misspelt in sources.list?)
```

which makes sense because at mysql there are only 8.0 debs for Ubuntu 19.10 ... :( Ubuntu 19.04 had both mysql 5.7 and 8.0, I wonder why this was changed...

---

### Post by julesou on 2019-10-21
Next, try to install docker ce (to run any mysql in a container): rep [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) doesn't have anything for eoan

---

### Post by botris on 2019-10-23
Following

---

### Post by hatim010 on 2019-10-23
same problem

---

### Post by morhook on 2019-10-23
This is happening to me too. :(

---

### Post by Tadaen_Sylvermane on 2019-10-23
Unless you do this in docker complete with the sql that it needs staying on 5.7 is pointless. You can't expect users of your software to install old unsupported software to make yours work. Part of development is making it easy for the end user. The problem you are facing now, you do not want your users to have to deal with.

---

### Post by justjuned on 2019-10-24
Facing the same problem after upgrade

---

### Post by dietmar-ludmann on 2019-10-28
I'm having the same problem here.
Tried to replace mysql with mariadb which seems more compatible, but it complained about my ibdata1 file and did not start at all.
Any help would be appreciated.

---

### Post by p4nni on 2019-10-29
I ran into the same issue today and got it resolved (somehow). I can't tell if this is a stable setup, so you should probably not use it in production.
Furthermore your databases/tables may be broken due to using mysql 8. I had to load a backup of my /var/lib/mysql folder. You may get around this by dumping all databases at first, deleting them and re-importing them once you downgraded to 5.7. I can not guarantee that this approach works since I chose a different way (as mentioned before).

Here is how i resolved it:
[LIST=1]
[*]Dump all your databases (and users)
[*]Stop the mysql service: ```
sudo service mysql stop
```
[*]Remove the following mysql-8 related packages: ```
sudo apt remove mysql-server mysql-server-8.0 mysql-server-core-8.0 mysql-client-8.0 mysql-client-core-8.0
```
[*]Delete the ```
/var/lib/mysql
``` folder
[*]Download the following mysql packages (using the linked version is important):
[LIST=1]
[*][https://launchpad.net/ubuntu/eoan/amd64/mysql-server-core-5.7/5.7.26-1](https://launchpad.net/ubuntu/eoan/amd64/mysql-server-core-5.7/5.7.26-1)
[*][https://launchpad.net/ubuntu/eoan/amd64/mysql-client-core-5.7/5.7.27-0ubuntu2](https://launchpad.net/ubuntu/eoan/amd64/mysql-client-core-5.7/5.7.27-0ubuntu2)
[*][https://launchpad.net/ubuntu/eoan/amd64/mysql-client-5.7/5.7.27-0ubuntu2](https://launchpad.net/ubuntu/eoan/amd64/mysql-client-5.7/5.7.27-0ubuntu2)
[*][https://launchpad.net/ubuntu/eoan/amd64/mysql-server-5.7/5.7.26-1](https://launchpad.net/ubuntu/eoan/amd64/mysql-server-5.7/5.7.26-1)
[/LIST]

[*]Install them via ```
sudo dpkg -i
``` in the order listed above (the order is important!). Example: At first you run: ```
sudo dpkg -i /path/to/your/downloads/mysql-server-core-5.7_5.7.26-1_amd64.deb
``` and so on...
[*]After installing the last package your MySQL server should come right up. Check this via ```
sudo service mysql status
```
[*]Re-import your databases and users
[/LIST]


I hope this approach helps you as well.


PS: This is my first post here, so I'm sorry for a maybe ugly text-formatting

---

### Post by bill-wilken-wilkenmail on 2019-10-29
I  invested countless hours in attempting to get 5.7 to run on 19.10.  Once I figured out the proper order for installing the components, I invariably ran into problems starting the daemon.  Here's what I got:

Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: mysql.service: Service RestartSec=100ms expired, scheduling restart.
Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: Stopped MySQL Community Server.
Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: mysql.service: Start request repeated too quickly.
Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: mysql.service: Failed with result 'exit-code'.
Oct 29 07:01:11 Precision-Tower-3620 systemd[1]: Failed to start MySQL Community Server.

After a lot of searching, I finally found the fix:  It was as easy as "sudo apt-get install -f," which discovered that my system was missing libevent-core-2.1-6:amd64.  Now 5.7 seems to run without a hitch.  Will do further testing today.

---

### Post by morhook on 2019-10-29
I've tried to follow the pretty thorough guide of @p4nni but it uninstalled some base components on my ubuntu 19.10 (colord gnome gnome-color-manager gnome-control-center gnome-core hplip libhpmud0 libmailutils6 libmysqlclient-dev libmysqlclient21 libsane libsane-hpaio libsnmp30 mailutils mysql-common
  printer-driver-hpcups sane-utils simple-scan ubuntu-desktop ubuntu-desktop-minimal).

I'll try to compile from source MySQL 5.7, and get back to this thread (if I'm successful).

---

### Post by hatim010 on 2019-10-29
you can download and install MySQL 5.7 from MySQL download site:
[https://dev.mysql.com/downloads/mysql/5.7.html?os=2](https://dev.mysql.com/downloads/mysql/5.7.html?os=2)

Documentation:
[URL="https://dev.mysql.com/doc/refman/5.7/en/binary-installation.htmlAttention:"]https://dev.mysql.com/doc/refman/5.7/en/binary-installation.html
[/URL]
the only way to get your data back, is to export your database on MySQL 8 and than import on 5.7

good luck to all of you

---

### Post by darlysson on 2019-10-30
Hello, I present an easy solution to solve the problem.
My instagram for questions: @cleyssondarlysson
If you have mysql 8.0 installed, follow these steps:
1. Dump all your databases (and users)
2. Stop the mysql service with the command:
```
sudo service mysql stop
```
3. Remove the following mysql-8 related packages:
```
sudo apt remove mysql-server mysql-server-8.0 mysql-server-core-8.0 mysql-client-8.0 mysql-client-core-8.0
```
4. Delete the folder mysql:
```
sudo rm /var/lib/mysql
```
If you don't have mysql 8.0 installed start from this:
5. Download the mysql 5.7 packages for ubuntu 19.10:
Download Link: [https://drive.google.com/open?id=1zDMj2qweTActlQDdAjEZUybbyMqbW4OE](https://drive.google.com/open?id=1zDMj2qweTActlQDdAjEZUybbyMqbW4OE)
6. Extract the zip file to the same download directory
7. Open the terminal in the download directory (where the zip file was extracted) and run the following commands in their order:
```
sudo dpkg -i mysql-server-core-5.7_5.7.26-1_amd64.deb
```
```
sudo dpkg -i mysql-client-core-5.7_5.7.27-0ubuntu2_amd64.deb
```
```
sudo dpkg -i mysql-client-5.7_5.7.27-0ubuntu2_amd64.deb
```
```
sudo dpkg -i mysql-server-5.7_5.7.26-1_amd64.deb
```
```
sudo dpkg -i libmysqlclient20_5.7.27-0ubuntu2_amd64.deb
```
```
sudo dpkg -i libmysqlclient-dev_5.7.27-0ubuntu2_amd64.deb
```
8. Then run this command:
```
sudo apt-get install -f
```
9. Alright, your mysql server must be up, run the command to verify:
```
sudo service mysql status
```
10. Proceed with mysql configuration, run the following command:
```
sudo mysql_secure_installation
```
11. Finally, run the command below to access mysql:
```
sudo mysql
```

Edit: Updated on 11/08/2019 with the inclusion of packages for libmysqlclient-dev

All right! Hope this helps. I am available on instagram: [https://www.instagram.com/cleyssondarlysson/](https://www.instagram.com/cleyssondarlysson/)

Cleysson Darlysson
Senior PHP Developer, Software Engineer and Linux based systems administrator.

---

### Post by tw-willian on 2019-11-05
Hopefully I saw this problem before upgrading. Guess the best option will be to run a mysql-5.7 docker first.

Is there any chance to customize upgrade to not remove mysql 5.7 and do not install the version 8 ?

I think this should be more clear on ubuntu upgrades, after all we're basically developers working with stuffs like mysql.

---

### Post by justjuned on 2019-11-05
Thanks a ton! @[**[COLOR=#000000]darlysson[/COLOR]**]("https://ubuntuforums.org/member.php?u=2134814")  for bringing in all details for smooth installation the only thing that's missing right now is [libmysqlclient-dev]("https://packages.ubuntu.com/eoan/libdevel/libmysqlclient-dev") for 5.7.x which currently points to 8.0.17 in eoan(Been a RoR Engineer we need this package)

Again Thanks for helping out:)

---

### Post by justjuned on 2019-11-06
[SIZE=5]For installing libmysqlclient-dev 5.7.27 follow up below steps:[/SIZE]
[SIZE=3]
[LIST]
[*]libmysqlclient-dev 5.7.27 has dependence on *libmysqlclient20*. So we need to install that first from below link
[LIST]
[*][https://launchpad.net/ubuntu/eoan/amd64/libmysqlclient20/5.7.27-0ubuntu2](https://launchpad.net/ubuntu/eoan/amd64/libmysqlclient20/5.7.27-0ubuntu2) 
[/LIST]
  
[*]And  [SIZE=3]libmysqlclient-dev package from here: [https://launchpad.net/ubuntu/eoan/amd64/libmysqlclient-dev/5.7.27-0ubuntu2](https://launchpad.net/ubuntu/eoan/amd64/libmysqlclient-dev/5.7.27-0ubuntu2)[/SIZE] 
[/LIST]
[SIZE=3]
Then start installing [/SIZE][SIZE=3][SIZE=3]*libmysqlclient20(don't forgot to checkout the directory where you've downloaded the above packages in the terminal)*[/SIZE]

```
sudo dpkg -i libmysqlclient20_5.7.27-0ubuntu2_amd64.deb
```

Followed by:

```
sudo dpkg -i libmysqlclient-dev_5.7.27-0ubuntu2_amd64.deb
```

Cheers we're done with installing libmysqlclient-dev exclusive to mysql 5.7.27

Thanks[/SIZE]!

[/SIZE]

---

### Post by darlysson on 2019-11-08
Post updated with the inclusion of its package. Thanks!

---

### Post by ei-elaarabi on 2019-12-20
Thanks you saved my life.

---

### Post by seeusers on 2020-04-27
Thanks a lot!

---

### Post by prkos on 2020-05-10
Thank you @darlysson! 

This worked for me, although not without an additional step, I also had to remove mariadb package and KOrganizer (that doesn't work anyway because of Akonadi). 

After that had been removed the installation of packages in your order went through :)

---

