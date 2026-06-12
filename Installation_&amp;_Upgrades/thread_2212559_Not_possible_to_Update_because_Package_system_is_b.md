---
title: "Not possible to Update because Package system is broken"
date: 2014-03-21
forum: Installation &amp; Upgrades
---

### Post by Torbjrn_Ferdman on 2014-03-21
Dear Xubutu gurus,

I have lived in peace with Ubuntu 10.04 for some years and never had any major issues till a few weeks ago when I upgraded to Xubuntu 12.04. Note that I made a clean installation of Xuntunu 12.04 + added some software that I need. Now I get crash reports all the time and can not upgrade.

1) I start the Upgrade manager and find a large number of applications that need updates and I click Install updates.
2) Get an error message that says "The package system is broken. If you are using third party repositories then disables them, since they are a common source of problems. Now run the following command in a terminal: apt-get install -f"
3) When I click details I get the following log:
The following packages have unmet dependencies:
abiword: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
         Depends: libglib2.0-0 (>= 2.16.0) but 2.32.4-0ubuntu1 is installed
         Depends: libgnutls26 (>= 2.12.6.1-0) but 2.12.14-5ubuntu3.7 is installed
         Depends: libgtk-3-0 (>= 3.0.0) but 3.4.2-0ubuntu0.6 is installed
         Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is installed
         Depends: libreadline6 (>= 6.0) but 6.2-8 is installed
         Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is installed
         Depends: libtidy-0.99-0 but it is not installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
         Depends: abiword-common (>= 2.9.2+svn20120213-1) but 2.9.2+svn20120213-1 is installed
4) When I try to run" sudo apt-get install -f" in a terminal window I get the following response:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 dh-apparmor libgomp1:i386 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 html2text
  libmail-sendmail-perl language-pack-kde-en-base libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtidy-0.99-0
The following NEW packages will be installed
  libtidy-0.99-0
0 to upgrade, 1 to newly install, 0 to remove and 39 not to upgrade.
3 not fully installed or removed.
Need to get 0 B/146 kB of archives.
After this operation, 411 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 184022 files and directories currently installed.)
Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

5) I have tried to exclude all third party repositories through Ubuntu Software center, but there I get another error message: "Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?"
6) When I try to make a repair I get the following error message: "Package operation failed. The installation or removal of a software package failed." Under Details I get the following information:
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 184022 files and directories currently installed.) 
Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of abiword: 
 abiword depends on libtidy-0.99-0; however: 
  Package libtidy-0.99-0 is not installed. 
dpkg: error processing abiword (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of abiword-plugin-mathview: 
 abiword-plugin-mathview depends on abiword (= 2.9.2+svn20120213-1); however: 
  Package abiword is not configured yet. 
dpkg: error processing abiword-plugin-mathview (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of abiword-plugin-grammar: 
 abiword-plugin-grammar depends on abiword (= 2.9.2+svn20120213-1); however: 
  Package abiword is not configured yet. 
dpkg: error processing abiword-plugin-grammar (--configure): 
 dependency problems - leaving unconfigured

7) If I click cancel when suggested to repair I can deselect some suspected repositories. They are called jon-severinsson and forumnokia and are used for downloading streams from Swedish television pages. Not sure it has any effect to deselct them in the Software centre.

Everything works apart from that I can not upgrade and I can not add or remove any software.

Any ideas?
/Torbjörn

---

### Post by fantab on 2014-03-21
Try the following:

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Post back the errors, if any, from the 'apt-get update' output.

If there are no errors are reported then you are good to run:
```
sudo apt-get dist-upgrade
```
(The above command does NOT upgrade to next ubuntu version, it just does some smart upgrades to the present system).

---

### Post by Ubi_one_2014 on 2014-03-22
pls post
cat /etc/apt/sources.list

---

### Post by ian-weisser on 2014-03-22
Don't muck about with a lot of enabling/disabling repos and other found-it-on-the-internet wastes of time.
dpkg told you in the error message *exactly* what it thinks the problem is.


> **Torbjrn_Ferdman said:**
> ```

The following packages have unmet dependencies:
abiword: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
         Depends: libglib2.0-0 (>= 2.16.0) but 2.32.4-0ubuntu1 is installed
         Depends: libgnutls26 (>= 2.12.6.1-0) but 2.12.14-5ubuntu3.7 is installed
         Depends: libgtk-3-0 (>= 3.0.0) but 3.4.2-0ubuntu0.6 is installed
         Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is installed
         Depends: libreadline6 (>= 6.0) but 6.2-8 is installed
         Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is installed
         Depends: libtidy-0.99-0 but it is not installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
         Depends: abiword-common (>= 2.9.2+svn20120213-1) but 2.9.2+svn20120213-1 is installed
```

Translation: One of the dependencies of Abiword won't install. Therefore Abiword won't install either.
Look carefully, and you'll see the likely culprit is libtidy-0.99-0, the only package not installed.


> **Torbjrn_Ferdman said:**
> ```

Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Translation: The system is telling you that you're trying to install a package that overwrites files provided by another package. Two packages cannot provide the same file - that's a fail.

Let's look at the packages more closely:
The existing one is libtidy 20130211-git-1
The one you're trying to install is libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb

See how the version numbers are totally different (and not comparable)? That's part of the problem - your system cannot even tell that they are both libtidy, nor which one is the upgraded version. Since it doesn't realize they are both libtidy, it tries installing instead of upgrading, which causes the fail.

Now let's do 10 seconds of research using rmadison to figure out versions:
```
$ rmadison -u ubuntu libtidy-0.99-0
 libtidy-0.99-0 | 20091223cvs-1          | lucid   | amd64, armel, i386, ia64, powerpc, sparc
 libtidy-0.99-0 | 20091223cvs-1ubuntu2   | precise | amd64, armel, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2        | quantal | amd64, armel, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2        | saucy   | amd64, arm64, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2ubuntu1 | trusty  | amd64, arm64, armhf, i386, powerpc, ppc64el
```

Okay, so the existing version is not from the Ubuntu Repositories. You got it from somewhere else, like a PPA.
The version you're trying to install is from the Ubuntu Repositories. Little significant change from the PPA version.
The problem isn't libtidy itself. The problem is the unreadable version number of PPA libtidy. 

This is one reason I don't recommend most PPAs unless you know how to investigate, diagnose, and fix this kind of problem. Happens a lot in this forum.


You have three options:

1) (recommended) You can uninstall your PPA version of libtidy, and then the Ubuntu version of libtidy (and Abiword) will install properly. This may uninstall whatever PPA application used the PPA version of libtidy. The application can usually be re-installed easily...but occasionally not.

2) You can force dpkg to install Abiword by ignoring the broken-but-existing libtidy dependency. Every time Abiword updates, the same problem will recur.

3) You can choose not to install Abiword at all. If you ever decide to install another application requiring libtidy, the same problem will recur.

---

### Post by Torbjrn_Ferdman on 2014-03-23
Thanks Ubi_one!

pappa@Bubbis:~$ cat /etc/apt/sources.list 
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by Torbjrn_Ferdman on 2014-03-23
> **fantab said:**
> Try the following:

```
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Post back the errors, if any, from the 'apt-get update' output.

If there are no errors are reported then you are good to run:
```
sudo apt-get dist-upgrade
```
(The above command does NOT upgrade to next ubuntu version, it just does some smart upgrades to the present system).

Thanks!

As you can see I don't get further than to apt-get -f install before the system starts complaining on the libtidy conflict. My problem is that I am kind of locked up and can not install or deinstall anything without getting errors. Getting closer and closer to a major reinstall.

pappa@Bubbis:~$ sudo apt-get -f install
[sudo] password for pappa: 
Sorry, try again.
[sudo] password for pappa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 dh-apparmor libgomp1:i386 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 html2text
  libmail-sendmail-perl language-pack-kde-en-base libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtidy-0.99-0
The following NEW packages will be installed
  libtidy-0.99-0
0 to upgrade, 1 to newly install, 0 to remove and 39 not to upgrade.
3 not fully installed or removed.
Need to get 0 B/146 kB of archives.
After this operation, 411 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 184022 files and directories currently installed.)
Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Torbjrn_Ferdman on 2014-03-23
> **ian-weisser said:**
> Don't muck about with a lot of enabling/disabling repos and other found-it-on-the-internet wastes of time.
dpkg told you in the error message *exactly* what it thinks the problem is.




Translation: One of the dependencies of Abiword won't install. Therefore Abiword won't install either.
Look carefully, and you'll see the likely culprit is libtidy-0.99-0, the only package not installed.




Translation: The system is telling you that you're trying to install a package that overwrites files provided by another package. Two packages cannot provide the same file - that's a fail.

Let's look at the packages more closely:
The existing one is libtidy 20130211-git-1
The one you're trying to install is libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb

See how the version numbers are totally different (and not comparable)? That's part of the problem - your system cannot even tell that they are both libtidy, nor which one is the upgraded version. Since it doesn't realize they are both libtidy, it tries installing instead of upgrading, which causes the fail.

Now let's do 10 seconds of research using rmadison to figure out versions:
```
$ rmadison -u ubuntu libtidy-0.99-0
 libtidy-0.99-0 | 20091223cvs-1          | lucid   | amd64, armel, i386, ia64, powerpc, sparc
 libtidy-0.99-0 | 20091223cvs-1ubuntu2   | precise | amd64, armel, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2        | quantal | amd64, armel, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2        | saucy   | amd64, arm64, armhf, i386, powerpc
 libtidy-0.99-0 | 20091223cvs-1.2ubuntu1 | trusty  | amd64, arm64, armhf, i386, powerpc, ppc64el
```

Okay, so the existing version is not from the Ubuntu Repositories. You got it from somewhere else, like a PPA.
The version you're trying to install is from the Ubuntu Repositories. Little significant change from the PPA version.
The problem isn't libtidy itself. The problem is the unreadable version number of PPA libtidy. 

This is one reason I don't recommend most PPAs unless you know how to investigate, diagnose, and fix this kind of problem. Happens a lot in this forum.


You have three options:

1) (recommended) You can uninstall your PPA version of libtidy, and then the Ubuntu version of libtidy (and Abiword) will install properly. This may uninstall whatever PPA application used the PPA version of libtidy. The application can usually be re-installed easily...but occasionally not.

2) You can force dpkg to install Abiword by ignoring the broken-but-existing libtidy dependency. Every time Abiword updates, the same problem will recur.

3) You can choose not to install Abiword at all. If you ever decide to install another application requiring libtidy, the same problem will recur.

Thanks Ian!
Wooo, this is creepy. You are reading my mind, right? Yes, I admit I did make a direct install of a software called PiratePlayer. It is not as bad as it sounds. Just catching streams from Swedish TV, and the originally reason why I changed from good old 10.04 to 12.04. And yes, I did a manual installation of Libtidy 0.99 according to the instructions. Obviously that was a mistake. Now it seems like a catch 22 as I can't uninstall anything and thus I can't get rid of libtidy either. 

pappa@Bubbis:~$ apt-cache search libtidy
libtidy-0.99-0 - HTML syntax checker and reformatter - library
libtidy-dev - HTML syntax checker and reformatter - development
php5-tidy - tidy module for php5
libhtml-tidy-perl - module for (X)HTML validation
libtidy-ruby - Transitional package for ruby-tidy
libtidy-ruby1.8 - Transitional package for ruby-tidy
ruby-tidy - Ruby interface to HTML Tidy Library
libtidy - Package created with checkinstall 1.6.2

pappa@Bubbis:~$ sudo apt-get remove libtidy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 abiword : Depends: libtidy-0.99-0 but it is not going to be installed
 pirateplayer : Depends: libtidy but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

pappa@Bubbis:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 dh-apparmor libgomp1:i386 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 html2text
  libmail-sendmail-perl language-pack-kde-en-base libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libtidy-0.99-0
The following NEW packages will be installed
  libtidy-0.99-0
0 to upgrade, 1 to newly install, 0 to remove and 39 not to upgrade.
3 not fully installed or removed.
Need to get 0 B/146 kB of archives.
After this operation, 411 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 184022 files and directories currently installed.)
Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libtidy-0.99.so.0.0.0', which is also in package libtidy 20130211-git-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libtidy-0.99-0_20091223cvs-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Time to make a total reinstall of Xubuntu or is there a trick to kick out libtidy-0.99?

---

### Post by ian-weisser on 2014-03-23
Abiword keeps trying to install becasue it's marked should-be-installed in dpkg's database.
Two easy ways to fix.

1)  Unmark it using dpkg. 
```
$ sudo dpkg --set-selections <ENTER>
abiword <TAB> deinstall <ENTER>
<CTRL+d>

$ dpkg --get-selections | grep abiword
abiword                   deinstall
```

The first command set marks abiword as should-be-uninstalled.
The second command simply checks that the first worked.
After that, apt-get should work normally for you to uninstall PiratePlayer and it's private version of libtidy.
If you still want to install abiword, then test the package manager with an upgrade, then use *sudo apt-get install abiword* like usual.

2) Unmark it using apt-get
```
$ sudo apt-get autoremove pirateplayer abiword libtidy
   ...big list of stuff to remove, including all the abiword components...

$ sudo apt-get update && sudo apt-get upgrade

$ sudo apt-get install abiword 
```
The first command removes all of the offenders, and all of their not-otherwise-needed dependencies. It's a rather radical move, and read the list of packages-to-be-removed carefully to ensure something critical (like ubuntu-standard) isn't being removed also. The second command tests that the package manager is working again. The third command, of course, installs abiword...if you want it installed.

---

### Post by Torbjrn_Ferdman on 2014-03-24
Thanks again Ian!

Firstly I managed to change the status for abiword from install to deinstall, according to your instructions.
```

sudo dpkg --set-selections <ENTER>
abiword <TAB> deinstall <ENTER>
abiword-common<TAB> deinstall <ENTER>
abiword-plugin-grammar<TAB> deinstall <ENTER>
abiword-plugin-mathview<TAB> deinstall <ENTER>
<CTRL-d>

dpkg --get-selections | grep abiword
abiword                        deinstall
abiword-common                    deinstall
abiword-plugin-grammar                deinstall
abiword-plugin-mathview                deinstall
libabiword-2.9                    install

```

Did the same with libtidy
```

sudo dpkg --set-selections <ENTER>
libtidy <TAB> deinstall <ENTER>
libtidy-0.99-0<TAB> deinstall <ENTER>

dpkg --get-selections | grep libtidy
libtidy                        deinstall
libtidy-0.99-0                    deinstall

```

Secondarily, when I tried for instance apt-get remove or autoremove pirateplayer, similar to what I tried before, I got the same error message as before, but when I removed all dependecies at the same time as you suggested as
```

sudo apt-get autoremove pirateplayer abiword libtidy libtidy-0.99-0 abiword-plugin-grammar abiword-plugin-mathview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libtidy-0.99-0 is not installed, so not removed
The following packages will be REMOVED
  abiword abiword-plugin-grammar abiword-plugin-mathview dh-apparmor html2text
  kde-l10n-engb language-pack-kde-en language-pack-kde-en-base libcroco3:i386
  libgettextpo0:i386 libgomp1:i386 libmail-sendmail-perl
  libsys-hostname-long-perl libtidy libunistring0:i386 pirateplayer
0 to upgrade, 0 to newly install, 16 to remove and 42 not to upgrade.
3 not fully installed or removed.
After this operation, 15.4 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 184021 files and directories currently installed.)
Removing abiword-plugin-mathview ...
Removing abiword-plugin-grammar ...
Removing abiword ...
Removing dh-apparmor ...
Removing html2text ...
Removing kde-l10n-engb ...
Removing libgettextpo0:i386 ...
Removing libcroco3:i386 ...
Removing libgomp1:i386 ...
Removing libmail-sendmail-perl ...
Removing libsys-hostname-long-perl ...
Removing pirateplayer ...
Removing libtidy ...
Removing libunistring0:i386 ...
Removing language-pack-kde-en-base ...
Removing language-pack-kde-en ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:translation information in database is up-to-date

```

....and.........IT WORKED!!!!! Thanks Ian, you're a boss.  =d>  \\:D/

---

### Post by ian-weisser on 2014-03-24
Glad it worked for you.

-------------------------------------------------------------------------------------------

For posterity and all you future users who find this thread on the internet: DON'T DO THIS FIX.
Really. Don't. This was a special situation, and we looked at it really carefully before prescribing this specific fix to this one-time situation.

If you were directed to this thread by a search engine, your problem is likely different, and USING THIS FIX WILL ALMOST CERTAINLY MAKE YOUR PROBLEM WORSE!

Instead, please start a new thread with your problem.

---

