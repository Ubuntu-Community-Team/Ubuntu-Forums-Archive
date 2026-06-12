---
title: "Sphinx search"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Hemakumar.S on 2010-10-28
Hai,

I am trying to install wordpress sphinx search engine 0.4 version [http://wordpress.org/extend/plugins/wordpress-sphinx-plugin](http://wordpress.org/extend/plugins/wordpress-sphinx-plugin) for the wordpress domain[http://opengov.in]("http://opengov.in/")  through ubuntu 10.0.4, I followed the steps by installing apt-get  install libmysql++-dev,mysql-client-5.1 in /usr/bin and created sphinx  directory in /opt/lampp and gave full permission but still once i try to  install sphinx and configure error coming in the form of make make  install.

These are the error showing link [http://farm2.static.flickr.com/1090/5112871415_95ee630e26.jpg](http://farm2.static.flickr.com/1090/5112871415_95ee630e26.jpg)
 
Further more,Could anybody tell  what are the  requirements to successfully implement the sphinx search plug-in 0.4 in  the hosting webserver.

Our wordpress domains all hosted by justhost.com. they are saying that  the pay packages has to be changed for the wordpress sphinx plug-in 0.4  version to be installed in the webserver.

Did you know about the setting up procedures in the webserver where the website will benefit immensely? 

Do you have any successful mantra to do it in the webserver?


Thank's and regards

Hemakumar.S

---

### Post by Hemakumar.S on 2010-11-17
Could any one have the working example of Free open-source wordpress  sphinx-search 0.4 plug-in installed perfectly in the wordpress domain.



With regards

Hemakumar.S

---

### Post by Hemakumar.S on 2010-11-23
Hi,

Now i am trying debian way to install the sphinx search in the local host, sphinx conf modified with the database requirement and till indexer command in ubuntu 9.10 is done. once the indexer-all command given,data is showing zero.

If any expert knows the finishing touch of successful implementation of sphinx reply soon

Thanks and regards

Hemakumar.S

---

### Post by Hemakumar.S on 2010-11-24
This is the output showing after indexer -all command given


root@TP046:/usr/local/bin# indexer -all
Sphinx 0.9.9-release (r2117)
Copyright (c) 2001-2009, Andrew Aksyonoff
 using config file '/usr/local/etc/sphinx.conf'...
WARNING: no such index '-all', skipping.
total 0 reads, 0.000 sec, 0.0 kb/call avg, 0.0 msec/call avg
total 0 writes, 0.000 sec, 0.0 kb/call avg, 0.0 msec/call avg 





With regards


Hemakumar.S

---

### Post by Hemakumar.S on 2010-11-25
This is the wordpress sphinx search plug-in 0.4 version indexing

Sphinx 0.9.8-dev (r1112)
Copyright (c) 2001-2008, Andrew Aksyonoff

using config file '/opt/lampp/sphinx/etc/sphinx.conf'...
indexing index 'delta_wordpress'...
collected 0 docs, 0.0 MB
total 0 docs, 0 bytes
total 0.010 sec, 0.00 bytes/sec, 0.00 docs/sec
indexing index 'main_wordpress'...
collected 49 docs, 0.0 MB
sorted 0.0 Mhits, 88.2% done
total 49 docs, 20272 bytes
total 0.019 sec, 1048949.63 bytes/sec, 2535.44 docs/sec
rotating indices: succesfully sent SIGHUP to searchd (pid=511.

Tell me the solution to show the number of documents

With regards

Hemakumar.S

---

