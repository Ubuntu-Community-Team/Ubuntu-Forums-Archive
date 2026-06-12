---
title: "Broken php5-cli?"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by sayakb on 2013-12-27
Recently, I was flooded with lots of unattended-upgrade crashes, so I decided to run apt manually. Here is what I see:

```

sayakb@FatalException:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic linux-image-extra-3.11.0-12-generic torsocks
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up php5-cli (5.5.3+dfsg-1ubuntu2.1) ...
ucfr: Attempt from package php5-cli  to take /etc/php5/cli/php.ini away from package libapache2-mod-php5
ucfr: Aborting.
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of php5-readline:
 php5-readline depends on php5-cli (= 5.5.3+dfsg-1ubuntu2.1); however:
  Package php5-cli is not configured yet.


dpkg: error processing php5-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-pear:
 php-pear depends on php5-cli; however:
  Package php5-cli is not configured yet.


dpkg: error processing php-pear (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-text-template:
 php-text-template depends on php-pear (>= 1.9.4); however:
  Package php-pear is not configured yet.


dpkg: error processing php-text-template (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-file-iterator:
 php-file-iterator depends on php-pear (>= 1.9.2); however:
  Package php-pear is not configured yet.


dpkg: error processing php-file-iterator (--cNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                       No apport report written because MaxReports is reached already
                                                                                                                                                     No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                                                                                                       No apport report written because MaxReports is reached already
                                                                                                                                                                     No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                                                                                                       No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                                                                                                       onfigure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-token-stream:
 php-token-stream depends on php-pear (>= 1.9.4); however:
  Package php-pear is not configured yet.


dpkg: error processing php-token-stream (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-codecoverage:
 php-codecoverage depends on php-text-template; however:
  Package php-text-template is not configured yet.
 php-codecoverage depends on php-file-iterator; however:
  Package php-file-iterator is not configured yet.
 php-codecoverage depends on php-token-stream; however:
  Package php-token-stream is not configured yet.


dpkg: error processing php-codecoverage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-timer:
 php-timer depends on php-pear (>= 1.9.2); however:
  Package php-pear is not configured yet.


dpkg: error processing php-timer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php-invoker:
 php-invoker depends on php-pear; however:
  Package php-pear is not configured yet.
 php-invoker depends on php-timer; however:
  Package php-timer is not configured yet.


dpkg: error processing php-invoker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpunit-story:
 phpunit-story depends on php-pear; however:
  Package php-pear is not configured yet.


dpkg: error processing phpunit-story (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpunit-mock-object:
 phpunit-mock-object depends on php-pear; however:
  Package php-pear is not configured yet.
 phpunit-mock-object depends on php-text-template; however:
  Package php-text-template is not configured yet.


dpkg: error processing phpunit-mock-object (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpunit:
 phpunit depends on php-pear; however:
  Package php-pear is not configured yet.
 phpunit depends on php5-cli; however:
  Package php5-cli is not configured yet.
 phpunit depends on php-file-iterator; however:
  Package php-file-iterator is not configured yet.
 phpunit depends on php-text-template; however:
  Package php-text-template is not configured yet.
 phpunit depends on php-codecoverage; however:
  Package php-codecoverage is not configured yet.
 phpunit depends on php-timer; however:
  Package php-timer is not configured yet.
 phpunit depends on phpunit-mock-object; however:
  Package phpunit-mock-object is not configured yet.


dpkg: error processing phpunit (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-cli
 php5-readline
 php-pear
 php-text-template
 php-file-iterator
 php-token-stream
 php-codecoverage
 php-timer
 php-invoker
 phpunit-story
 phpunit-mock-object
 phpunit
E: Sub-process /usr/bin/dpkg returned an error code (1)
sayakb@FatalException:~$ cat /etc/apt/sources.list




# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.lstn.net/ubuntu/ saucy main restricted
deb-src http://mirror.lstn.net/ubuntu/ saucy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.lstn.net/ubuntu/ saucy-updates main restricted
deb-src http://mirror.lstn.net/ubuntu/ saucy-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.lstn.net/ubuntu/ saucy universe
deb-src http://mirror.lstn.net/ubuntu/ saucy universe
deb http://mirror.lstn.net/ubuntu/ saucy-updates universe
deb-src http://mirror.lstn.net/ubuntu/ saucy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.lstn.net/ubuntu/ saucy multiverse
deb-src http://mirror.lstn.net/ubuntu/ saucy multiverse
deb http://mirror.lstn.net/ubuntu/ saucy-updates multiverse
deb-src http://mirror.lstn.net/ubuntu/ saucy-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://mirror.lstn.net/ubuntu/ saucy-security main restricted
deb-src http://mirror.lstn.net/ubuntu/ saucy-security main restricted
deb http://mirror.lstn.net/ubuntu/ saucy-security universe
deb-src http://mirror.lstn.net/ubuntu/ saucy-security universe
deb http://mirror.lstn.net/ubuntu/ saucy-security multiverse
deb-src http://mirror.lstn.net/ubuntu/ saucy-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
deb http://archive.canonical.com/ saucy partner
# deb-src http://archive.canonical.com/ raring partner


# My apps
deb http://deb.torproject.org/torproject.org saucy main
sayakb@FatalException:~$ 

```

Any pointers on how to resolve this issue?

---

### Post by Wolf-Ekkehard on 2014-03-06
I am having the identical issue - did you meanwhile figure out how to resolve it?

---

### Post by Kleenux on 2014-08-01
Me too... No official solution yet(?)
In my case [FONT=Courier New]/etc/php5/cli/php.ini[/FONT] is a symlink to [FONT=Courier New]../fpm/php.ini[/FONT] .
I made that symlink so that the CLI loads the same config and modules as the daemon - useful for tests.

And for some reason the package installer wants to remove that CLI php.ini, it fails to do so as it expects (I assume) a regular file and not a symlink.

FTTB I just renamed cli/php.ini to &.save, did the upgrade, then renamed back to php.ini.
No error.

---

### Post by apronouva2 on 2014-09-10
> **Kleenux said:**
> Me too... No official solution yet(?)
In my case [FONT=Courier New]/etc/php5/cli/php.ini[/FONT] is a symlink to [FONT=Courier New]../fpm/php.ini[/FONT] .
I made that symlink so that the CLI loads the same config and modules as the daemon - useful for tests.

And for some reason the package installer wants to remove that CLI php.ini, it fails to do so as it expects (I assume) a regular file and not a symlink.

FTTB I just renamed cli/php.ini to &.save, did the upgrade, then renamed back to php.ini.
No error.

Hello,

I got the identical situation here. I tried this suggestion to no avail. Another friend of mine suggests to reinstall php5 as php5-cli is a part of php5 metapackage. But now it shows this error :

```

dpkg: error processing package php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5-readline:
 php5-readline depends on php5-cli (= 5.5.9+dfsg-1ubuntu4.4); however:
  Package php5-cli is not configured yet.

dpkg: error processing package php5-readline (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.5.9+dfsg-1ubuntu4.4) | libapache2-mod-php5filter (>= 5.5.9+dfsg-1ubuntu4.4) | php5-cgi (>= 5.5.9+dfsg-1ubuntu4.4) | php5-fpm (>= 5.5.9+dfsg-1ubuntu4.4); however:
  Package libapache2-mod-php5 is not installed.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not configured yet.

dpkg: error processing package php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 php5-fpm
 php5-cli
 php5-readline
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

FYI, I'm using php with nginx server. Do I still need to install libapache2-mod* as I don't use apache2? or if someone already found a workaround that will be great. Thank you.

Edit : SOLVED

Here's what I did.
0. Make backup for all config (in my case, only /etc/php5/fpm/pool.d/*)
1. Completely remove php5 : apt-get remove php5* | apt-get autoremove
2. Purge : apt-get purge php5*
3. Reboot
4. Reinstall : apt-get install php5-cli php5-mcrypt php5-sqlite php5-mysql php5-intl php5-fpm php5-gd php5-curl
5. Restore /etc/php5/fpm/pool.d/*
6. Re-enable mcrypt : php5enmod mcrypt | php5enmod curl
7. Restart php-fpm and nginx services

Note: I don't know if reboot is really necessary but in my case, without rebooting, reinstall will stuck again at php5-cli. So far my server works fine, will report back if things go wild again.

---

### Post by Anatoliy_Kyrychenk on 2014-10-24
I was able to solve this in a bit simpler way:

1. Verify that /etc/php5/fpm/php.ini is a sym-link to "../apache2/php.ini"

2. Delete it:
# rm -f /etc/php5/fpm/php.ini

3. Complete the upgrade progress:
# apt-get upgrade -f

4. Re-create the link:
# cd /etc/php5/fpm/ && ln -s ../apache2/php.ini

---

