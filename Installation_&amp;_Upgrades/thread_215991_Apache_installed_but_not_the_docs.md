---
title: "Apache installed but not the docs"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Hank Montgomery on 2006-07-14
I just got my first Linux box (this one) up and talking on the network with only a few minor problems getting MySQL and SAMBA configured.

Now - going to the default web page that installed with apache it provides a link titled "The Apache documentation has been included with this distribution."

Clicking this link results in "The requested URL /manual/ was not found on this server."

This message implies that the docs are supposed to be included in the install - WHICH IMLIES THAT SOMETHING WENT WRONG WITH MY INSTALL

I know I can see the doc online at [http://httpd.apache.org/docs](http://httpd.apache.org/docs)

But are the docs REALLY supposed to be on my desktop - and if yes then ???:confused:

---

### Post by reacocard on 2006-07-14
```
sudo apt-get install apache2-doc
```
will install the documentation.

---

### Post by Hank Montgomery on 2006-07-14
I still get 404 - The requested URL /manual/ was not found on this server.
Although the messages below look like it installed THIS TIME.
It also looks like it was not originally selected for install by Synaptic.
And I don't see anything that tells me where it put the doc file.


:~$sudo apt-get install apache2-doc
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  apache2-doc
0 upgraded, 1 newly installed, 0 to remove and 68 not upgraded.
Need to get 2124kB of archives.
After unpacking 11.6MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main apache2-doc 2.0.55-4ubuntu2 [2124kB]Fetched 2124kB in 5s (362kB/s)
Selecting previously deselected package apache2-doc.
(Reading database ... 72943 files and directories currently installed.)
Unpacking apache2-doc (from .../apache2-doc_2.0.55-4ubuntu2_all.deb) ...
Setting up apache2-doc (2.0.55-4ubuntu2) ...
:~$

---

### Post by Hank Montgomery on 2006-07-14
Ok,

I'll bet there is some setup required.  I don't think it knows where the base html is located.

Looking in Synaptic I now see it as installed.
The properties list a BUNCH of html files being put into /usr/share/doc/apache2-doc
A few went to other places but it looks like these are the doc pages.

However, the link on the default homepage points to:
http://<myservername>/manual/

I am starting by entering my server name as the url (as I do to access my ISS server).

This displays a page at:
http://<myservername>/   <<=   I'll bet this is the wrong place to be!
Firefox then shows an "Index of /" 
The only thing listed is "apache2-default/".
When I click that I get a page: 
"If you can see this, it means that the installation of the Apache web server software on this system was successful."
Ths page contains a link to the documentation "included with this distribution". I'll bet this is supposed to be the base directory.

I will work from the docs online to see if I can find any initial setup/configuration instructions.

---

### Post by byronical on 2006-11-16
Hi

I had the same issue but then discovered that a default configuration file apache-doc is created under /etc/apache2/conf.d when you install the apache-doc package. After installing apache-doc you need to restart the apache server to load the new configuration for the activate the link [http://localhost/manual/](http://localhost/manual/).

# /etc/init.d/apache2 restart

---

