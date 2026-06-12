---
title: "DownGrading php 5.3 to php 5.2"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by jaya28inside on 2010-09-02
Ok guys!

I made this thread for solving out previous cases, for all common ubuntu users who have already installed their php 5.3. 

I assume that you all in these condition:

[B]1) Your Repository is still default
2) You have LAMP already installed
3) You have Internet Access
4) You have root privileges[/B]

:p

OK. Let's start!

**1) Ensuring that you do have php 5.3.x installed**
How to check that we have php installed?
simple. Execute this command;

```

$> dpkg -l | grep php

```

You'll get the output pretty similar with this;
> 

ii  libapache2-mod-php5              5.3.2-1ubuntu4.2                  server-side, HTML-embedded scripting languag
ii  php5-common                      5.3.2-1ubuntu4.2                  Common files for packages built from the php
ii  php5-curl                        5.3.2-1ubuntu4.2                  CURL module for php5
ii  php5-gd                          5.3.2-1ubuntu4.2                  GD module for php5
ii  php5-imap                        5.3.2-0ubuntu2                    IMAP module for php5
ii  php5-mysql                       5.3.2-1ubuntu4.2                  MySQL module for php5


OK. Now it means you are in a OK' condition. Continuing next step.

**2) Downgrading Php 5.3 to 5.2**

Once you're already sure that you do have php 5.3 installed. Then now, 
What you will do now is copy and paste this source code below
save it within a file named **downGradeNRemove.sh**
Just save it anywhere you wanted. 

```

php_installed=`dpkg -l | grep php| awk '{print $2}' |tr "\n" " "`

# remove all php packge
sudo aptitude purge $php_installed

# use karmic for php pakage
# pin-params:  a (archive), c (components), v (version), o (origin) and l (label).
echo -e "Package: php5\nPin: release a=karmic\nPin-Priority: 991\n"  | sudo tee /etc/apt/preferences.d/php > /dev/null
apt-cache search php5-|grep php5-|awk '{print "Package:", $1,"\nPin: release a=karmic\nPin-Priority: 991\n"}'|sudo tee -a /etc/apt/preferences.d/php > /dev/null
apt-cache search -n libapache2-mod-php5 |awk '{print "Package:", $1,"\nPin: release a=karmic\nPin-Priority: 991\n"}'| sudo tee -a /etc/apt/preferences.d/php > /dev/null
echo -e "Package: php-pear\nPin: release a=karmic\nPin-Priority: 991\n"  | sudo tee -a /etc/apt/preferences.d/php > /dev/null

# add karmic to source list
egrep '(main restricted|universe|multiverse)' /etc/apt/sources.list|grep -v "#"| sed s/lucid/karmic/g | sudo tee /etc/apt/sources.list.d/karmic.list > /dev/null

# update package database (use apt-get if aptitude crash)
sudo apt-get update

# install php
sudo apt-get install $php_installed
# or sudo aptitude install -t karmic php5-cli php5-cgi //for fcgi
# or  sudo apt-get install -t karmic  libapache2-mod-php5 //for apache module

sudo aptitude hold `dpkg -l | grep php5| awk '{print $2}' |tr "\n" " "`
#done

```

And now, please use Sudo or any root privilege enabled, and execute this file. 
How to execute this file anyway?
Pretty funny.
To execute the file, You just need to change the mode of this file to be executable.
Here is the command;

```

$> chmod u+rx **downGradeNRemove.sh**

```

Then, execute it!
```

$> ./**downGradeNRemove.sh**

```

Ok!
Now, let's ensuring that you do now have php 5.2,
execute the previous command;

```

$> dpkg -l | grep php

```

You'll obviously got output saying the php. 5.2. I'm sure.

Ok! done!
Now just restart your apache2 by executing this command

```

$> /etc/init.d/apache2 restart

```


Boing! Done.

If you ask me which resource I got?
Here; You may read it along;

**From indonesian article;**
> [http://muhammad.zamroni.net/downgrade-php-53x-ke-52x-di-ubuntu-10-04-lucid-lynx.html](http://muhammad.zamroni.net/downgrade-php-53x-ke-52x-di-ubuntu-10-04-lucid-lynx.html)
**From russian article;**
> [http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/](http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/)
**From english article;**
> [http://www.nickveenhof.be/blog/reverting-or-downgrading-php-53-52-ubuntu-lucid-lynx-1004](http://www.nickveenhof.be/blog/reverting-or-downgrading-php-53-52-ubuntu-lucid-lynx-1004)

):P

---

### Post by chopp3r on 2011-02-28
Thanks for scripting the creation of aptitude settings for a PHP5 package downgrade. 

I made a change to the first line in your script so that it doesn't include packages like "phpmyadmin" or "webmin-phpini" that I have installed. Here's the ammended first line:

```
php_installed=`dpkg -l | grep php5 | awk '{print $2}' |tr "\n" " "`
```

---

### Post by jaya28inside on 2011-03-03
> I made a change to the first line in your script
ya, that's nice...!
great thanks, chopp3r. :D

---

### Post by BkkBonanza on 2011-04-22
This also works for Maverick if you edit the script and replace,

lucid -> maverick

Just had to do a downgrade on a system and this script made it easy.

Thanks!

---

### Post by dsoprea on 2011-06-15
Some additional notes on the process:

*Note: apt-cache will display currently installed packages AS WELL AS the packages available in the repository. If a package won't go away, it's probably installed locally.

o Double-check that new installations default to installing from the original repository. We're not sure of the order in which the various repositories are checked. If the order is not correct, try putting both .list files in the same directory, along with a numbered prefix.

o To install a package from a specific repository, run apt-get or synaptic with the "-t" parameter along with the release's token that was set in the repository above. If a dependency is already installed but from the wrong repository, APT/DPKG will differentiate and fail. All dependencies that will be installed alongside the desired package will come from the same repository.

o If the older dependencies are in place and you move to install a package that has both old and new versions without specifying a repository, the old dependencies will be officially replaced (using Apt's atomic replace feature) with the new versions.


Dustin Oprea

---

### Post by Lentdawg on 2011-07-18
anyone have a working config for natty?

---

### Post by wavesailor on 2011-11-25
This no longer works as the Karmic archives no longer exist at archive.ubuntu.com

Does anyone have an idea or suggestion to get this downgrade to PHP 5.2.x working?

---

