---
title: "Own Cloud"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by win0922 on 2011-08-27
I have just downloaded Owncloud. The site told me to do this:

Ubuntu 10.04 Lucid or older, Debian 6.0 Squeeze
 ownCloud isn‘t packaged, depencencies need to be installed manually: sudo apt-get install apache2 php5 php5-sqlite php5-json 
 optional dependencies sudo apt-get install mp3info curl libcurl3 libcurl3-dev php5-curl zip 
 Download ownCloud 
stable version 1.2 
latest experimental version 2.0, alternatively from repository: git clone git://anongit.kde.org/owncloud 
 Extract it: tar xfz owncloud-1.2.tar.gz 
 Copy it to Apache‘s server directory: sudo cp -r owncloud /var/www 
 Make ownCloud directory accessible to Apache: cd /var/www; sudo chown -R www-data:www-data owncloud 
 When sudo (chown) isn’t available: setfacl -Rm d:u:YOUR-USERNAME:rwx,u:www-data:rwx owncloud 
 Open the folder in a browser and complete the setup wizard

I have downloaded the file and extracted it but I don't know how or what to do next. Help

---

### Post by tgalati4 on 2011-08-27
Next step:

Open a terminal:

sudo apt-get install apache2 php5 php5-sqlite php5-json 

sudo apt-get install mp3info curl libcurl3 libcurl3-dev php5-curl zip

---

### Post by Old_Grey_Wolf on 2011-08-27
This link may be helpful [http://owncloud.org/index.php/Installation#Linux_distributions.2C_BSD.2C_other_Unixes](http://owncloud.org/index.php/Installation#Linux_distributions.2C_BSD.2C_other_Unixes). Not knowing what release of Ubuntu you are using, that is the best I can offer.

---

