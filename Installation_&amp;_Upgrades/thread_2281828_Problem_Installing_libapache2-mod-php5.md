---
title: "Problem Installing libapache2-mod-php5"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by stephen73 on 2015-06-09
I have been working on this over a couple of days and have not succeeded.

I recently upgraded from 12.04 to 14.04. Had some problems with apache2 going from 2.2 to 2.4 over config file naming and permissions, but got that resolved.

Now I am stuck and floundering installing php5.

I get this error for the install:

dpkg: error processing package libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

Using Google I see others have had this problem, but I have not found a solution. 

I have followed suggestions like these (using sudo):

apt-get -f install
apt-get clean all
 apt-get update

  apt-get -f install

Then try:

apt-get install libapache2-mod-php5

I get the error above.

Any and all help most appreciated!

Follows is the term.log:

```
Selecting previously unselected package php5-json. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 315763 files and directories currently installed.) 
Preparing to unpack .../php5-json_1.3.2-2build1_amd64.deb ... 
Unpacking php5-json (1.3.2-2build1) ... 
Selecting previously unselected package php5-common. 
Preparing to unpack .../php5-common_5.5.9+dfsg-1ubuntu4.9_amd64.deb ... 
Unpacking php5-common (5.5.9+dfsg-1ubuntu4.9) ... 
Selecting previously unselected package php5-cli. 
Preparing to unpack .../php5-cli_5.5.9+dfsg-1ubuntu4.9_amd64.deb ... 
Unpacking php5-cli (5.5.9+dfsg-1ubuntu4.9) ... 
Selecting previously unselected package php5-readline. 
Preparing to unpack .../php5-readline_5.5.9+dfsg-1ubuntu4.9_amd64.deb ... 
Unpacking php5-readline (5.5.9+dfsg-1ubuntu4.9) ... 
Selecting previously unselected package libapache2-mod-php5. 
Preparing to unpack .../libapache2-mod-php5_5.5.9+dfsg-1ubuntu4.9_amd64.deb ... 
Unpacking libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.9) ... 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
Setting up php5-json (1.3.2-2build1) ... 
php5_invoke: Enable module json for cli SAPI 
php5_invoke: Enable module json for apache2 SAPI 
Setting up php5-common (5.5.9+dfsg-1ubuntu4.9) ... 
php5_invoke: Enable module pdo for cli SAPI 
php5_invoke: Enable module pdo for apache2 SAPI 
php5_invoke: Enable module opcache for cli SAPI 
php5_invoke: Enable module opcache for apache2 SAPI 
Setting up php5-cli (5.5.9+dfsg-1ubuntu4.9) ... 
update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode 
php5_invoke opcache: already enabled for cli SAPI 
php5_invoke pdo: already enabled for cli SAPI 
php5_invoke json: already enabled for cli SAPI 
Setting up php5-readline (5.5.9+dfsg-1ubuntu4.9) ... 
php5_invoke: Enable module readline for cli SAPI 
php5_invoke: Enable module readline for apache2 SAPI 
Setting up libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.9) ... 
php5_invoke opcache: already enabled for apache2 SAPI 
php5_invoke readline: already enabled for apache2 SAPI 
php5_invoke pdo: already enabled for apache2 SAPI 
php5_invoke json: already enabled for apache2 SAPI 
dpkg: error processing package libapache2-mod-php5 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 libapache2-mod-php5
```

---

