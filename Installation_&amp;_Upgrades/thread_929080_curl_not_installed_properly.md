---
title: "curl not installed properly"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by Keeper337 on 2008-09-24
I just install the fog (imaging server). When I try to run a task it says Call to undefined function curl_init(). I created a php page containing phpinfo() and it has no reference to curl at all. I have tried running apt-get install php5-curl and it says the newest version all exists. Any help would be great.

Thanks

---

### Post by Keeper337 on 2008-09-26
I have tried apt-get install curl libcurl3-dev and number of other packages. Nothing was working. I tried apt-get remove the same packages and reinstall them. Still nothing! I then double checked the /etc/php5/apache2/php.ini file. I had misspelled extension=curl.so. Once I changed the spelling and restarted the apache server it started to work. Go figure!!!

---

