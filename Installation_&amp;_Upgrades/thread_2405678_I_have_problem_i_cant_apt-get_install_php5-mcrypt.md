---
title: "I have problem i cant apt-get install php5-mcrypt"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by tecno40 on 2018-11-09
Dear sir 
i need help i cant install 
apt-get install lsb-release nscd curl php5 php5-mysql php5-cli php5-curl unzip -y
apt-get install php5-mcrypt
php5enmod mcrypt
service apache2 restart
***********************************
the error is came when put this :    apt-get install lsb-release nscd curl php5 php5-mysql php5-cli php5-curl unzip -y 

E: Package 'php5' has no installation candidate
E: Package 'php5-mysql' has no installation candidate
E: Package 'php5-cli' has no installation candidate
E: Unable to locate package php5-curl

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

Please mention the Ubuntu release. Paste the output of following command.

```
~$ lsb_release -a
```

Here is a solution for the mentioned problem, assuming the release is 16.04 or above, but i am not sure how it will effect your current configuration. A backup is advised before any changes are made.

[https://askubuntu.com/questions/109404/how-do-i-install-different-upgrade-or-downgrade-php-version-in-still-supported](https://askubuntu.com/questions/109404/how-do-i-install-different-upgrade-or-downgrade-php-version-in-still-supported)

Regards,
Mitesh

---

### Post by tecno40 on 2018-11-09
Thanks to replay to me 

Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-138-generic x86_64)

----------------------------------------------------------------------
root@vps211752:~#  lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

---

### Post by tecno40 on 2018-11-09
i resolved the problem but now i have new problem 

what mean the error 

MySQL Extension is missing
i need to fix it please

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

I hope this will help you to solve the problem.
[URL="http://php.net/manual/en/set.mysqlinfo.php"]
[http://php.net/manual/en/set.mysqlinfo.php](http://php.net/manual/en/set.mysqlinfo.php)
[/URL]
If it helps, please summarize the steps which helped you to solve your issue and mark the thread as solved.

Regards,
Mitesh

---

### Post by tecno40 on 2018-11-09
Dear Mitesh
first problem i fix it from ([https://askubuntu.com/questions/1094...till-supported]("https://askubuntu.com/questions/109404/how-do-i-install-different-upgrade-or-downgrade-php-version-in-still-supported")) you was give me the link
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install php7.1   # for PHP 7.1
sudo apt-get install php7.0   # for PHP 7.0
sudo apt-get install php5.6   # for PHP 5.6
sudo update-alternatives --config php

sudo a2dismod php7.1         # unload the current version
sudo a2enmod  php5.6         # load the version you need
sudo service apache2 restart # restart webserver to apply

sudo add-apt-repository ppa:ondrej/php
sudo add-apt-repository ppa:ondrej/php5-compat
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install php5 # this will pull php5.6 package 

sudo apt-get install python-software-properties 

and then is fix it 
but come new problem i dont know what is it i put this ----->

php5enmod mcrypt 

but give me 
php5enmod: command not found

i don't know what can i do please any one can help me coz am here new in Ubuntu 

and many thnks for your support bro [**[COLOR=#000000]mitesh.agrwl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2111225")

---

### Post by tecno40 on 2018-11-09
[http://php.net/manual/en/set.mysqlinfo.php](http://php.net/manual/en/set.mysqlinfo.php) i dont understand this link

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

My previous link was related to the query > i resolved the problem but now i have new problem 

what mean the error 

MySQL Extension is missing
i need to fix it please

I thought you have some problem with MySQL DB server. PHP is often used with this server and that link could help you to sort out the problem related to MySQL.

Anyways, the query related to your current problem here is a solution 
[URL="https://stackoverflow.com/questions/50354696/howto-ubuntu-18-04-install-activate-php-extension-ext-mcrypt"]
[/URL]> [https://stackoverflow.com/questions/50354696/howto-ubuntu-18-04-install-activate-php-extension-ext-mcrypt](https://stackoverflow.com/questions/50354696/howto-ubuntu-18-04-install-activate-php-extension-ext-mcrypt)

But before proceeding, read the warning given by [GordonM]("https://stackoverflow.com/users/477127/gordonm").

Regards,
Mitesh

---

