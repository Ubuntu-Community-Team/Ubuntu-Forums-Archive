---
title: "Trying to install php5 on ubuntu 6.10"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by DMammone on 2010-01-13
I tried using apt-get install command, as stated in 6.10 documentation, but get the following:
 
[U][COLOR=#0000ff][EMAIL="root@mctvserver"][FONT=Courier New]root@mctvserver[/FONT][/EMAIL][FONT=Courier New]:~# sudo apt-get install php5-common php5 libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-mpm-worker
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-common apache2-mpm-prefork apache2-utils
Suggested packages:
  php-pear
The following packages will be REMOVED:
  apache2-mpm-worker
The following NEW packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5 php5 php5-common
The following packages will be upgraded:
  apache2 apache2-common apache2-utils
3 upgraded, 4 newly installed, 1 to remove and 130 not upgraded.
Need to get 3605kB of archives.
After unpacking 5677kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2 apache2-common apache2-utils apache2-mpm-prefork php5-common
  libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-common 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-utils 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-mpm-prefork 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main php5-common 5.1.6-1ubuntu2.7
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main libapache2-mod-php5 5.1.6-1ubuntu2.7
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main php5 5.1.6-1ubuntu2.7
  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.7_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.7_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.7_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.7_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.6-1ubuntu2.7_all.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.6-1ubuntu2.7_all.deb")[FONT=Courier New]  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/FONT][EMAIL="root@mctvserver"][FONT=Courier New]root@mctvserver[/FONT][/EMAIL][FONT=Courier New]:~#

[/FONT][/COLOR][/U] 
When I try apt-get update:
 
[U][COLOR=#0000ff][EMAIL="root@mctvserver"]root@mctvserver[/EMAIL]:~# sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

[/COLOR][/U] 
What do I need to do?

---

### Post by DMammone on 2010-01-13
Also, the original apt-get install command with --fix-missing:
 
[EMAIL="root@mctvserver"][FONT=Courier New]root@mctvserver[/FONT][/EMAIL][FONT=Courier New]:~# sudo apt-get install php5-common php5 libapache2-mod-php5 --fix-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-mpm-worker
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2 apache2-common apache2-mpm-prefork apache2-utils
Suggested packages:
  php-pear
The following packages will be REMOVED:
  apache2-mpm-worker
The following NEW packages will be installed:
  apache2-mpm-prefork libapache2-mod-php5 php5 php5-common
The following packages will be upgraded:
  apache2 apache2-common apache2-utils
3 upgraded, 4 newly installed, 1 to remove and 130 not upgraded.
Need to get 3605kB of archives.
After unpacking 5677kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache2 apache2-common apache2-utils apache2-mpm-prefork php5-common
  libapache2-mod-php5 php5
Install these packages without verification [y/N]? y
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-common 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-utils 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main apache2-mpm-prefork 2.0.55-4ubuntu4.2
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main php5-common 5.1.6-1ubuntu2.7
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main libapache2-mod-php5 5.1.6-1ubuntu2.7
  404 Not Found
Err [/FONT][[FONT=Courier New]http://security.ubuntu.com[/FONT]]("http://security.ubuntu.com")[FONT=Courier New] edgy-security/main php5 5.1.6-1ubuntu2.7
  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.0.55-4ubuntu4.2_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.0.55-4ubuntu4.2_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.7_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.7_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.7_i386.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.1.6-1ubuntu2.7_i386.deb")[FONT=Courier New]  404 Not Found
Failed to fetch [/FONT][[FONT=Courier New]http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.6-1ubuntu2.7_all.deb[/FONT]]("http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5_5.1.6-1ubuntu2.7_all.deb")[FONT=Courier New]  404 Not Found
Unable to correct missing packages.
E: Aborting install.
[/FONT][EMAIL="root@mctvserver"][FONT=Courier New]root@mctvserver[/FONT][/EMAIL][FONT=Courier New]:~#
[/FONT]

---

### Post by Cheesemill on 2010-01-13
6.10 reached end-of-life nearly 2 years ago, it's no longer supported so the repos aren't there anymore.

It is possible to install the software you're after by editing your /etc/apt/sources.list and changing all instances of security.ubuntu.com to old-releases.ubuntu.com and running 'apt-get update' again.

Please bear in mind that it is not recommended to run an EOL version of Ubuntu, 6.10 hasn't had any security updates or bug fixes since April 2008 so could well have unpatched vulnerabilities.

---

### Post by Tralce on 2010-01-13
> **Cheesemill said:**
> 6.10 reached end-of-life nearly 2 years ago, it's no longer supported so the repos aren't there anymore.

It is possible to install the software you're after by editing your /etc/apt/sources.list and changing all instances of security.ubuntu.com to old-releases.ubuntu.com and running 'apt-get update' again.

Please bear in mind that it is not recommended to run an EOL version of Ubuntu, 6.10 hasn't had any security updates or bug fixes since April 2008 so could well have unpatched vulnerabilities.

Would it be possible to use the do-release-upgrade script on such an old release?

---

### Post by Cheesemill on 2010-01-13
> **Tralce said:**
> Would it be possible to use the do-release-upgrade script on such an old release?

I really wouldn't recommend it, you would probably have to edit your sources.list after each upgrade, you would also have to go through 3 separate updates to get to a supported version:

6.10 > 7.04
7.04 > 7.10
7.10 > 8.04

I'd say the chances of something breaking during all of this are incredibly high, even if it did work you'd have so much left over crud in the system troubleshooting any future problems would be a nightmare.

Far better off with a clean install. If you can wait until Lucid in April then you'll get 5 years of server support before having to upgrade again, that's the whole idea behind LTS releases.

---

### Post by DMammone on 2010-01-13
> **Cheesemill said:**
> 6.10 reached end-of-life nearly 2 years ago, it's no longer supported so the repos aren't there anymore.
 
It is possible to install the software you're after by editing your /etc/apt/sources.list and changing all instances of security.ubuntu.com to old-releases.ubuntu.com and running 'apt-get update' again.
 
Please bear in mind that it is not recommended to run an EOL version of Ubuntu, 6.10 hasn't had any security updates or bug fixes since April 2008 so could well have unpatched vulnerabilities.
 
The old-release repos worked! Thank you!
 
I think I will wait to do a clean install until the next release.

---

