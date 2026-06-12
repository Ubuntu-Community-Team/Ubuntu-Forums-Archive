---
title: "apt-get broken - unable to fix it"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by WesleyWex on 2007-01-08
After doing a bad dist-upgrade at home (I saw somewhere that doing this by the terminal wasn't a bad idea), I upgraded my work pc from ubuntu 6.06 to 6.10.

Although my home problem was solved by rebooting in "safe mode" and running some aptitude commands, my work pc that WAS UPGRADED THROUGH THE UPGRADE MANAGER had some fatal issues, described below.

1. Running apt-get -f install
```
root@prog01:/# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 courier-authdaemon
Aborted (core dumped)
```

2. apt-get -f remove
```
root@prog01:/# apt-get -f remove
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
root@prog01:/# Errors were encountered while processing:
 courier-authdaemon
```

3. dpkg --configure -a
```
dpkg --configure -a
dpkg: dependency problems prevent configuration of courier-authlib-userdb:
 courier-authlib-userdb depends on courier-authlib; however:
  Package courier-authlib is not installed.
 courier-authlib-userdb depends on courier-authlib (>= 0.58); however:
  Package courier-authlib is not installed.
dpkg: error processing courier-authlib-userdb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 courier-authlib-userdb
```


Another thing I did was try to use "aptitude":

1. aptitude -f remove (solution 1)
```
root@prog01:/# aptitude -f remove
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  courier-authlib-userdb courier-base 
The following packages have been kept back:
  avahi-daemon courier-authdaemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  courier-base: Depends: courier-authlib but it is not installable
  courier-authlib-userdb: Depends: courier-authlib but it is not installable
                          Depends: courier-authlib (>= 0.58) but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the courier-authdaemon package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Install the following packages:
courier-authlib [0.58-4ubuntu1 (edgy)]

Upgrade the following packages:
courier-authdaemon [0.47-13ubuntu5.1 (now) -> 0.58-4ubuntu1 (edgy)]

Score is -69

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  courier-authlib 
The following packages have been kept back:
  avahi-daemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
The following NEW packages will be installed:
  courier-authlib 
The following packages will be upgraded:
  courier-authdaemon 
1 packages upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/83.9kB of archives. After unpacking 164kB will be used.
Do you want to continue? [Y/n/?] y 
Writing extended state information... Done
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
root@prog01:/# Errors were encountered while processing:
 courier-authdaemon
```

2. aptitude -f remove (solution 2)
```
root@prog01:/# aptitude -f removeReading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  courier-authlib-userdb courier-base 
The following packages have been kept back:
  avahi-daemon courier-authdaemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  courier-base: Depends: courier-authlib but it is not installable
  courier-authlib-userdb: Depends: courier-authlib but it is not installable
                          Depends: courier-authlib (>= 0.58) but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the courier-authdaemon package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Install the following packages:
courier-authlib [0.58-4ubuntu1 (edgy)]

Upgrade the following packages:
courier-authdaemon [0.47-13ubuntu5.1 (now) -> 0.58-4ubuntu1 (edgy)]

Score is -69

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
courier-authdaemon
courier-base

Install the following packages:
courier-authlib [0.58-4ubuntu1 (edgy)]

Score is -721

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  courier-authlib 
The following packages will be automatically REMOVED:
  courier-authdaemon courier-base 
The following packages have been kept back:
  avahi-daemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
The following NEW packages will be installed:
  courier-authlib 
The following packages will be REMOVED:
  courier-authdaemon courier-base 
0 packages upgraded, 1 newly installed, 2 to remove and 10 not upgraded.
Need to get 0B/77.0kB of archives. After unpacking 426kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
(Reading database ... Aborted (core dumped)
root@prog01:/# 105802 files and directories currently installed.)
Removing courier-base ...
```

3. aptitude -f remove (solution 3)
```
root@prog01:/# aptitude -f remove
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  courier-authlib-userdb courier-base 
The following packages have been kept back:
  avahi-daemon courier-authdaemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 
  libavahi-core4 libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
0 packages upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  courier-base: Depends: courier-authlib but it is not installable
  courier-authlib-userdb: Depends: courier-authlib but it is not installable
                          Depends: courier-authlib (>= 0.58) but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the courier-authdaemon package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Install the following packages:
courier-authlib [0.58-4ubuntu1 (edgy)]

Upgrade the following packages:
courier-authdaemon [0.47-13ubuntu5.1 (now) -> 0.58-4ubuntu1 (edgy)]

Score is -69

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
courier-authdaemon
courier-base

Install the following packages:
courier-authlib [0.58-4ubuntu1 (edgy)]

Score is -721

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
courier-authdaemon
courier-authlib-userdb
courier-base

Score is -1003

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  courier-authdaemon courier-authlib-userdb courier-base 
The following packages have been kept back:
  avahi-daemon dbus dbus-1-utils libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libavahi-qt3-1 libdbus-1-3 
The following packages will be REMOVED:
  courier-authdaemon courier-authlib-userdb courier-base 
0 packages upgraded, 0 newly installed, 3 to remove and 10 not upgraded.
Need to get 0B of archives. After unpacking 827kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
(Reading database ... Aborted (core dumped)
root@prog01:/# 105802 files and directories currently installed.)
Removing courier-base ...
```

I've read many topics and nothing helps.

Please, I don't have any idea of what I should do now!

---

### Post by az on 2007-01-08
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.


reinstall courier-authdaemon and then try to remove everything again.

---

### Post by WesleyWex on 2007-01-08
I guess I forgot to mention that.

Just read:

```
root@prog01:/# apt-get install courier-authlib
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  courier-authdaemon
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
root@prog01:/# Errors were encountered while processing:
 courier-authdaemon
```

---

### Post by az on 2007-01-08
Try to manually install the version from Dapper....

---

### Post by WesleyWex on 2007-01-08
And how can I do this?

---

### Post by az on 2007-01-08
Ah!  I see.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=courier-authlib&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=courier-authlib&searchon=names&subword=1&version=all&release=all)

There is no Dapper version of the package.


What about downloading it and running

sudo dpkg -i courier-authlib*.deb

---

### Post by WesleyWex on 2007-01-08
Trying courier-authlib:

```
root@prog01:/home/wesley/Downloads# dpkg -i courier-authlib_0.58-4ubuntu1_i386.deb
dpkg: considering removing courier-authdaemon in favour of courier-authlib ...
courier-authdaemon is not properly installed - ignoring any dependencies on it.
dpkg: package courier-authdaemon requires reinstallation, will not remove.
dpkg: regarding courier-authlib_0.58-4ubuntu1_i386.deb containing courier-authlib:
 courier-authlib conflicts with courier-authdaemon (<< 0.58)
  courier-authdaemon (version 0.47-13ubuntu5.1) is broken due to postinst failure.
dpkg: error processing courier-authlib_0.58-4ubuntu1_i386.deb (--install):
 conflicting packages - not installing courier-authlib
Errors were encountered while processing:
 courier-authlib_0.58-4ubuntu1_i386.deb
```

I thougt the problem was on 'courier-authdaemon', so I did the same:
```
root@prog01:/home/wesley/Downloads# dpkg -i courier-authdaemon_0.58-4ubuntu1_i386.deb 
Selecting previously deselected package courier-authdaemon.
(Reading database ... 105803 files and directories currently installed.)
Preparing to replace courier-authdaemon 0.47-13ubuntu5.1 (using courier-authdaemon_0.58-4ubuntu1_i386.deb) ...
 * Stopping Courier authdaemon...                                                                                       exec: 31: /usr/sbin/courierlogger: not found
                                                                                                                [fail]
invoke-rc.d: initscript courier-authdaemon, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping Courier authdaemon...                                                                                       exec: 31: /usr/sbin/courierlogger: not found
                                                                                                                 [fail]
invoke-rc.d: initscript courier-authdaemon, action "stop" failed.
dpkg: error processing courier-authdaemon_0.58-4ubuntu1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 1
 * Starting Courier authdaemon...                                                                                       exec: 31: /usr/sbin/courierlogger: not found
                                                                                                                 [fail]
invoke-rc.d: initscript courier-authdaemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 courier-authdaemon_0.58-4ubuntu1_i386.deb
```

Isn't there a way I can manually remove this package from apt-get? I don't use courier, just installed as part of a test I was doing.

---

### Post by az on 2007-01-08
It's tied up in a knot.

I think one of the later packages overwrote the install/remove scripts from an earlier version of the package.  Try to find which package was there first (autlib or authdaemon) reinstall it and then try to force-remove it.  Them you may have to re-install the later version of it just to be able to remove that, too.

Yes, this is messy.  Had you changed your sources.list or just added the Edgy sources to Dapper?  

If you keep your sources pointing to one release at a time, you run less of a chance of your package manager bunching itself up like this.

---

### Post by WesleyWex on 2007-01-09
I didn't change anything, I did what [the big please topic]("http://www.ubuntuforums.org/showthread.php?t=286599") says.

The upgrade failed on the way they recommend (gksu "update-manager -c") and succeeded at home, where I upgraded xubuntu with minor issues (replacing the sources.list and executing apt-get dist-upgrade).

This is how my sources.list looks:
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## edgy-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
# deb http://archive.canonical.com/ubuntu edgy-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt edgy main
## deb-src http://wine.budgetdedicated.com/apt edgy main

## skype
## only uncomment it if you need it
deb http://archive.ubuntu.com/ubuntu/ edgy main
## deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

### Post by matrooswolf on 2007-01-10
Hi, 
don't really know what the problem is,
but could this be of any help?
> 1. backup /var/lib/dpkg/status to a safe location
2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w)
3. sudo apt-get upgrade
4. sudo apt-get install courier-imap
I got this from this page: (apparently it's a bug)

[https://launchpad.net/ubuntu/+source/apt/+bug/64615/comments/5](https://launchpad.net/ubuntu/+source/apt/+bug/64615/comments/5)

Good Luck!! 
(I still haven't upgraded, I'm too chicken, and seeing all the problems people have ...)

---

### Post by quartzeye on 2007-03-06
I too am having the same problem however I am far from knowing how to fix this.  The instructions that everyone says works might as well be in in Greek as I am not linux savvy.

I was following the instructions on HowToForge for the perfect 6.10 setup in an effort to get a LAMP server running.  I followed the instructions to the letter, with only a minor issue here and there until I hit section "13 Courier-IMAP/Courier-POP3".  Looks like I would be setting up a secure mail server and client but not sure.  The instructions say to do this so and I am no one to question it.

Now I am having the same problem others are having but I do not understand how to fix this problem.

The instructions say:

**1. backup /var/lib/dpkg/status to a safe location**
        Where might a safe location be?  I assume that I type in something like:
        [COLOR="Red"]**backup /var/lib/dpkg/status /etc/myfolder/backups**[/COLOR]
        Do I need to make a directory someplace to backup to?  Is /etc/... safe?

**2. remove all courier entries from /var/lib/dpkg/status (nano it, search=ctrl-w)**        
        How exactly do I remove all the entries?  Do I just do the Unix version of 
        del *.* in the folder?  Do I use apt-get to uninstall?  What exactly do I type in?  
        Also what does "nano it" mean?  Isn't nano a text editor?  Why would I want to edit
        files I should be deleting?  *"search=ctrl-w"*  is that a nano command to search for
        files in the folder?  Why not do the Unix equivilent of dir in the folder to list all the
        files?  I assume it should be empty once you delete or uninstall the entries.

**3. sudo apt-get upgrade**
        This I understand.

**4. sudo apt-get install courier-imap** 
        This I understand as well but won't this try to reinstall from the same location?  Isn't t
        that the root problem here, missing 6.10 files in the repositories???  If it works then
        great.  If someone can explain steps 1 and 2 for the Unix illiterate like my self then I
        good with steps 3 and 4.  Remember tal slowly and assume that I barely know where
        the power switch is for the PC.  That way nothing is left to question as no assumed
        knowledge is present on my part.

Thank in advance
Quartzeye

---

### Post by WesleyWex on 2007-03-19
This has been done a long time, but:

I gave up and reinstalled ubuntu from scratch.

I know, it was something extreme but I couldn't find any other way to solve this. And the above post was created after I did this.

---

### Post by NumPy on 2007-05-13
Ok I have been dealing with this issue for a while, and my solution was to open and edit 

/etc/init.d/courier-autdaemon 

and remove everyting from stop) down. This forced the script to NOT run the stop variable.. From what I see though this is only an issue for Dapper installs.

---

### Post by HGJ on 2008-01-17
Hi.

I had the exact same problem (what are the odds?!)

The above method works!

---

