---
title: "system upgrade error"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by BStrizzy on 2013-02-04
Hey guys, 

I recently tried to upgrade my ubuntu home server but I got this error code 

bstrizzy@nova:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  phpmyadmin: Depends: libapache2-mod-php5 but it is not installed or
                       php5-cgi but it is not installed or
                       php5 but it is not installed
              Depends: php5-mysql but it is not installed or
                       php5-mysqli but it is not installable
              Depends: php5-mcrypt but it is not installed
              Recommends: apache2 or
                          lighttpd but it is not installed or
                          httpd
              Recommends: php5-gd but it is not installed
              Recommends: mysql-client
E: Unmet dependencies. Try using -f.
bstrizzy@nova:~$ 

I also tried removing my lamp stack to start it over by using this code 

bstrizzy@nova:~$ sudo apt-get --purge remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

---

### Post by MAFoElffen on 2013-02-04
Could you please do this and post the results listed in that newly created file?
```

dpkg --get-selections > installed-software

```
Please post those results by using Code tags... You can do that easily by being in post "advanced mode," highlighting that file's text, then pressing the "**#**" icon in the post edit toolbar. that will add the code tags to the beginning and end of that highlighted text. 

The way I do this is from a connected desktop, open a terminal session and sh into my server. Then I can cat the file and cut and paste what is in it into my posts or bug reports... of course you could always upload it from the server using a text-based browser (I sometimes do that), but not as easy or as fast...

---

### Post by BStrizzy on 2013-02-05
> **MAFoElffen said:**
> Could you please do this and post the results listed in that newly created file?
```

dpkg --get-selections > installed-software

```Please post those results by using Code tags... You can do that easily by being in post "advanced mode," highlighting that file's text, then pressing the "**#**" icon in the post edit toolbar. that will add the code tags to the beginning and end of that highlighted text. 

The way I do this is from a connected desktop, open a terminal session and sh into my server. Then I can cat the file and cut and paste what is in it into my posts or bug reports... of course you could always upload it from the server using a text-based browser (I sometimes do that), but not as easy or as fast...

see attached

---

### Post by MAFoElffen on 2013-02-05
> 
linux-image-2.6.32-45-generic-pae

What version of Server are you running?

... Also, what server services are you actually "using?"

Did you try using aptitude to resolve and update the Lamp Packages? You could use it to dryrun it to see what packages it suggests to update... and if you have the dependencies installed to do that. That way you can use it as a diagnostics tool to see what the effect "would" be, without making the actual update changes.

You could also use aptitude to "reinstall" the LAMP packages, if needed.

I find that when I just start removing lower level packages, I end up orphaning the upper level packages that depend on them.

Claritiy- You are just doing update/upgrade right? Not a release upgrade?

---

### Post by BStrizzy on 2013-02-05
> **MAFoElffen said:**
> What version of Server are you running?

... Also, what server services are you "using?"

Did you try using aptitude to resolve and update the Lamp Packages? You could use it to dryrun it to see what packages it suggests to update... and if you have the dependencies installed to do that. That way you can use it as a diagnostics tool to see what the effect "would" be, without making the actual update changes.

You could also use aptitude to "reinstall" the LAMP packages, if needed.

I find that when I just start removing lower level packages, I end up orphaning the upper level packages that depend on them.

Claritiy- You are just doing update/upgrade right? Not a release upgrade?

I am running 10.04 ubuntu server edition, and I was using media tomb which is pretty much my only service I use, but ever since I purged lamp that was gone too.  

I am also trying to just update/upgrade not release upgrade. see attached again.

I think I solved my problem though. I just re installed LAMP and removed phpmyadmin before actually removing the LAMP stack its self =)

---

