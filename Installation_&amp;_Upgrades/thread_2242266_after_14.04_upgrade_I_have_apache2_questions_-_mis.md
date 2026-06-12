---
title: "after 14.04 upgrade I have apache2 questions - missing files and docs"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by btodd012 on 2014-08-31
Hi - I upgraded from 12.04 to 14.04. When I upgraded I picked the option **keep my configuration**. After the upgrade apache2 didn't work. I finally figured out that I had to move everything from /var/www to /var/www/html.

I tried (using other posts) to change my DocumentRoot first with no success. I found the Ububtu 14.04 server guide and the huge apache2 docs - but the Server guide said tha I should read such and such docs in /etc/apache2/... but I don't seem to have any of the files that should be there.

I don't know what packages I am missing. I did an apt-get update and apt-get-install for many packages with no results.

Also - I don't have any of the default files that come with apache2 2.47 ... all my configs are old..

I see other parts of my system where documentations says look in this driectory for docs and they never seem to be there.

I know this seems dumb - but I'm am really stumped as to how to update or find out where the docs should be????

thanks

---

### Post by yancek on 2014-08-31
> I tried (using other posts) to change my DocumentRoot first with no success

It would be a good idea to give us some specific as to what you tried and how you tried and what the results were.

 Try looking in:  /usr/share/doc, lots of documentation there.

---

### Post by btodd012 on 2014-09-01
> **yancek said:**
> It would be a good idea to give us some specific as to what you tried and how you tried and what the results were.

 Try looking in:  /usr/share/doc, lots of documentation there.
oops sorry...

I was looking at the Ubuntu 14.04 Server guide for info about error codes and messages in error.log. The guide says " Read /etc/apache2/conf.d/ localized-error-pages for detailed instructions for using ErrorDocument, including locations ofexample files."
The only file in /etc/apache2/conf.d is [B]phpmyadmin.conf. 

[/B]I know my config is old style and needs updating and I was going to look at error messages and start there. However, error.og has very little info.

Really I am looking for info to get error.log printing enough so I could start looking at apache2.conf.

I looked in /usr/share/doc/apache2 and this is what I see.
changelog.Debian.gz  migrate-sites.pl  README.backtrace
copyright            NEWS.Debian.gz    README.Debian.gz
examples             PACKAGING.gz      README.multiple-instances

todd@todd-GX270:/usr/share/doc/apache2$ ls examples
apache2.monit  secondary-init-script  setup-instance

hmmm after zcat the Debian README, I see
Documentation
=============


The full Apache 2 documentation can be found on the web at


http://httpd.apache.org/docs/2.4/


or, if you have installed the apache2-doc package, in


/usr/share/doc/apache2-doc/manual/

I think that's what I was looking for... how to install the docs....

Even better - after looking, I see the docs there..... I will forge ahead and do some reading!!!!
Thanks for enough info to get me going!!!

---

### Post by yancek on 2014-09-01
You're welcome and good luck with it.

---

