---
title: "installing mcrypt for php7 ubuntu 16.04"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by ebitdj on 2016-10-21
my server is digitalocean ubuntu 16.04 LAMP php7
need to install mcrypt but always failed
i tried

[COLOR=#676767][FONT=proxima-nova]sudo apt-get update[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo apt-get install mcrypt[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]add the mcrypt.ini file on the folder[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo phpenmod mcrypt[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo service apache2 restart

also being desperate tried anything on google like

[/FONT][/COLOR][COLOR=#676767][FONT=proxima-nova]sudo apt-get install php5-mcrypt[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo ln -s /etc/php5/conf.d/mcrypt.ini /etc/php5/mods-available[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo php5enmod mcrypt [/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo service apache2 restart

but failed from the first line saying
[/FONT][/COLOR]E: Package 'php5-mcrypt' has no installation candidate

why is this happening?
digitalocean support still hasn't reply for 6H+

---

### Post by SeijiSensei on 2016-10-21
According to [https://launchpad.net/ubuntu/+source/php7.0](https://launchpad.net/ubuntu/+source/php7.0), the package for mcrypt is called php7.0-mcrypt.  Did you try that?

---

