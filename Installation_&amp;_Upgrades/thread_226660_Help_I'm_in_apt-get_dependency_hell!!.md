---
title: "Help I'm in apt-get dependency hell!!"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by acolic on 2006-07-31
Help,

I've installed Ubuntu on a server that has been running fine for a couple of months. A couple of weeks ago I run the apt-get update/upgrade command and since then I have been in dependency hell.

I've tried all the various commands, hacks with apt-get aptitude and dpkg and no luck. I cannot install or remove any programs without apt-get trying to install mysql-server 5 and openoffice.

The only thing I can think of doing at this point is reinstall Ubuntu which would be very disapointing. I really like Ubuntu and Linux in general but this tight coupling of dependencies is a real pain. At least on a Windows box I could install/remove the broken apps.

Could somone knowledgable please have a look at the attached log and suggest a way for me to fix these problems.

Thanks alot.

 
acolic@Sirius:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
41 not fully installed or removed.
Need to get 0B/35.7MB of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
(Reading database ...
dpkg: serious warning: files list file for package `bittorrent' missing, assuming package has no files currently installed.
82416 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.21-3ubuntu1 (using .../mysql-server-5.0_5.0.21-3ubuntu1_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: line 10: /usr/share/debconf/confmodule: No such file or directory
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.21-3ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 3: /usr/share/debconf/confmodule: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace openoffice.org-base 2.0.2-2ubuntu12 (using .../openoffice.org-base_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-base ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-base_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace openoffice.org-calc 2.0.2-2ubuntu12 (using .../openoffice.org-calc_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-calc ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace openoffice.org-draw 2.0.2-2ubuntu12 (using .../openoffice.org-draw_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-draw_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace openoffice.org-impress 2.0.2-2ubuntu12 (using .../openoffice.org-impress_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-impress ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-impress_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace openoffice.org-math 2.0.2-2ubuntu12 (using .../openoffice.org-math_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-math ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-math_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Preparing to replace openoffice.org-writer 2.0.2-2ubuntu12 (using .../openoffice.org-writer_2.0.2-2ubuntu12_i386.deb) ...
Unpacking replacement openoffice.org-writer ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error processing /var/cache/apt/archives/openoffice.org-writer_2.0.2-2ubuntu12_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 2
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/File/Glob.pm line 3.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/File/Glob.pm line 3.
Compilation failed in require at /usr/sbin/update-mime line 51.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 51.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.21-3ubuntu1_i386.deb
 /var/cache/apt/archives/openoffice.org-base_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-calc_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-draw_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-impress_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-math_2.0.2-2ubuntu12_i386.deb
 /var/cache/apt/archives/openoffice.org-writer_2.0.2-2ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by az on 2006-07-31
Do you have mixed repositories?

What does 

sudo dpkg --clear-avail 
followed by

sudo apt-get update
do?

---

### Post by acolic on 2006-07-31
Hi,

thanks for the reply. 

I'm not in front of my machine right now but I did try those cmds. 

What I think happened was the clear executed ok then I ran the update and then the upgrade cmd. Update downloaded the new info from the repositories, upgrade then tried to download mysql and open office. Download was successfull but then I got errors similar to my first e-mail as Ubuntu tried to install the downloaded apps.

What do you mean by mixed repositories?

Thanks

Alex

---

### Post by az on 2006-07-31
> **acolic said:**
> Hi,

What do you mean by mixed repositories?



For example, using both breezy and Dapper repositories.  Or both Debian and Ubuntu repositories.

---

### Post by acolic on 2006-07-31
I don't think I've mixed repositories. The list is below. Good suggestion though. Maybe I'll try deleting the repositories one by one and see if that changes anything.

Alex


#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapp$

#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dappe$
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univ$ 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted $

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by acolic on 2006-07-31
Making a bit of headway. I removed all the repositories except for the CD-ROM. apt-get still tries to install mysql-server and open office. I tried aptitude.

First I tried to purge everything:

root@Sirius:/etc/apt# aptitude purge
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

Then I tried to remove openoffice:

root@Sirius:/etc/apt# aptitude remove openoffice.org-core
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-writer python-uno
The following packages will be REMOVED:
  openoffice.org-core
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 83.1MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-gnome: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-writer: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-gtk: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-evolution: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-common: Depends: openoffice.org-core (> 2.0.2) but it is not installable or
                                  openoffice.org-core-experimental (> 2.0.2) which is a virtual package.
  python-uno: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (> 2.0.2) but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-draw
openoffice.org-evolution
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-l10n-en-us
openoffice.org-math
openoffice.org-writer
python-uno

Score is -4513

Accept this solution? [Y/n/q/?] Y
The following packages will be automatically REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-uno
The following packages will be REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer python-uno
0 packages upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 186MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@Sirius:/etc/apt#
root@Sirius:/etc/apt# aptitude remove mysql-server
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@Sirius:/etc/apt#

Then I tried to remove openoffice
root@Sirius:/etc/apt#
root@Sirius:/etc/apt# aptitude remove openoffice.org-core
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-writer python-uno
The following packages will be REMOVED:
  openoffice.org-core
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 83.1MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-gnome: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-writer: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-gtk: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-evolution: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-common: Depends: openoffice.org-core (> 2.0.2) but it is not installable or
                                  openoffice.org-core-experimental (> 2.0.2) which is a virtual package.
  python-uno: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (> 2.0.2) but it is not installable
Resolving dependencies...
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
openoffice.org-base
openoffice.org-calc
openoffice.org-common
openoffice.org-draw
openoffice.org-evolution
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-java-common
openoffice.org-l10n-en-us
openoffice.org-math
openoffice.org-writer
python-uno

Score is -4513

Accept this solution? [Y/n/q/?] Y
The following packages will be automatically REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-uno
The following packages will be REMOVED:
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer python-uno
0 packages upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 186MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?


Same for mysql-server:

root@Sirius:/etc/apt# aptitude purge
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the mysql-server-5.0 package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?


What's this link between openoffice and mysql-server. 

Is there a way to make ubuntu think that they are not installed. If I tried to remove them aptitude says they are not installed and tries to install them and that fails

Alex

---

### Post by acolic on 2006-08-02
Hi,

I've downloaded the latest version of mysql server and open office.

Would manually installing these programs solve my problems or make them worse?

Alex

---

### Post by christhemonkey on 2006-08-02
Previously when you were running aptitude purge, you were running them as your normal user, yes?
If so you need to run them as root:
```
**sudo** aptitude purge 
```

---

### Post by acolic on 2006-08-02
Hi,

as root I ran aptitude purge, update, upgrade and this is the result I got. Should I install openoffice manually?

root@Sirius:/etc/apt# sudo aptitude purge
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the openoffice.org-base package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@Sirius:/etc/apt#
root@Sirius:/etc/apt# sudo aptitude update
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
root@Sirius:/etc/apt# sudo aptitude upgrade
E: Opening configuration file /usr/share/aptitude/aptitude-defaults - ifstream::ifstream (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the openoffice.org-base package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@Sirius:/etc/apt#

---

### Post by acolic on 2006-08-02
Well installing OO via RPMS didn't work out. I downloaded the tar ball and tried to run the alien cmd to convert them into  debs and I got this msg. I see this msg everytime I try to install/uninstall apps. Maybe this is my problem and someone can provide a bit of help.

root@Sirius:/tmp/OOC680_m7_native_packed-1_en-US.9044/RPMS# alien -i *.rpm
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/alien line 295.
BEGIN failed--compilation aborted at /usr/bin/alien line 295.
root@Sirius:/tmp/OOC680_m7_native_packed-1_en-US.9044/RPMS#

---

### Post by acolic on 2006-08-03
Well I did some more looking around and I found that I did not have the strict.pm library installed. I noticed that it was part of the perl-module package. But since I can't use apt-get to install it I downloaded it from the ubuntu web site and pulled that file out and put it in my /usr/local/lib/perl/5.8.7.

That got rid of some error msgs but when apt-get tries to install programs more perl libraries are missing. 

Can someone tell me or suggest a site that explains how to install perl from scratch without using apt-get.

Maybe if I reinstall perl I'll make some headway.

Thanks

Alex


root@Sirius:/tmp/OOC680_m7_native_packed-1_en-US.9044/RPMS# alien -i *.rpm
Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/bin/alien line 295.
BEGIN failed--compilation aborted at /usr/bin/alien line 295.
root@Sirius:/tmp/OOC680_m7_native_packed-1_en-US.9044/RPMS#

---

