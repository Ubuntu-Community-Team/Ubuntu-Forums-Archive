---
title: "PHP-mysqli"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by tanizakijunichiro on 2008-06-07
Hello, I ran my phpinfo() function and noticed that under the category for mysqli all the settings were set to none, causing me to suspect that it wasn't installed and that I should return to the command line and do so:  

Directive	Local Value	Master Value
mysqli.default_host	no value	no value
mysqli.default_port	3306	3306
mysqli.default_pw	no value	no value
mysqli.default_socket	no value	no value
mysqli.default_user	no value	no value
mysqli.max_links	Unlimited	Unlimited
mysqli.reconnect	Off	Off

Being somewhat new to linux, and somewhat inept when it comes to these sorts of installation matters, I went to the command line and tried the following:  

$ sudo apt-get install php5-mysqli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package php5-mysqli is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  php5-mysql

because I wasn't able to achieve any sort of success with this, I perhaps rather foolishly typed in the following command:  sudo apt-get --purge remove php5.  

Here are my questions in a nutshell:

1.)  How do I install Php-mysqli
2.)  has the php package been permanently removed from my OS?
3.)  If the package has been removed how can I reinstall it?

Thank you for you time, patience and support!

---

### Post by hydr0 on 2008-11-04
if you look closely to the phpinfo output it shows you

mysqli  << as headline
MysqlI Support	enabled

Client API library version 	5.0.67
Client API header version 	5.0.67
MYSQLI_SOCKET 	/var/run/mysqld/mysqld.sock

Directive	Local Value	Master Value
mysqli.default_host	no value	no value
mysqli.default_port	3306	3306
mysqli.default_pw	no value	no value
mysqli.default_socket	no value	no value
mysqli.default_user	no value	no value
mysqli.max_links	Unlimited	Unlimited
mysqli.reconnect	Off	Off


so these values are nothing to worry about, just keep in mind, to effectively use mysqli you need to adapt your php files

for example if you like to use phpmyadmin(for any reason) you could change your config.inc.php file located in /usr/share/phpmyadmin/

and add the little i like i did in this line

    if (!isset($cfg['Servers'][$i]['extension'])) {
        $cfg['Servers'][$i]['extension'] = 'mysqli';
    }

so 1. just reinstall: apt-get install php5-mysql
2. what is really permanent in life
3. see 1.

annotation: older ubuntu releases had a package called php5-myaqli in it, this seems to be removed or better say merged into the php5-mysql pakage, which i think is really great because why not start using the improved mysql where it is possible...

hope this text helps you or some others a little bit, even when it comes some month too late...

---

### Post by edysidea on 2012-06-18
php5-mysqli has been replaced by php5-mysql

So now:
1. Install your php5 again using apt-get install php5
2. Install php5-mysql using apt-get install php5-mysql

:popcorn:

---

### Post by lanceturnbull on 2013-03-13
@edysidea 
thx, dude, simple & efficient

---

### Post by lisati on 2013-03-13
We appreciate the feedback.

Things can change in the space of a year or more: some of the PHP web pages recommend using mysqli over mysql.

Old thread closed.

---

