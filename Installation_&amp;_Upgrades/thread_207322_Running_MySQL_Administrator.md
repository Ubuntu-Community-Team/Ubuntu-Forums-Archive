---
title: "Running MySQL Administrator"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by matthorton on 2006-07-01
Hello everyone

I've just installed mySQL Administrator from a tar.gz file and i can seem to run the application.

i followed these instructions exactly...

"To install MySQL Administrator, run this command:

shell> tar --directory=/opt -xzvf mysql-administrator-version-linux.tar.gz

This installs the application binary in /opt/mysql-administrator/bin. Change into that directory and run mysql-administrator to start the application.

Distribution-specific packages will be available at some point."

...I have done this but it doesn't install to the path is says it should.

Mine installed to here "/opt/mysql-administrator-1.1.10" and a "bin" directory does not exist there.

Has anyone else experienced this problem or can anyone see what I'm doing wrong?

Thanks ever so much in advance. I'm having such trouble.

Matt.

---

### Post by userundefine on 2006-07-01
Hi Matt,

Is there a reason you're using a tar ?  MySQL administrator is available in the repositories.  [See here.]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-87ae4d301d99214a65ac4378488fcb578b859ce3")

```
$ sudo aptitude install mysql-admin
```
Is all you have to do.  Or apt-get instead of aptitude if you prefer.  I installed it this way.

---

### Post by userundefine on 2006-07-01
Please don't [post the same thread]("http://ubuntuforums.org/showthread.php?t=207323") in more than one place.

It wastes everyone's time, especially when you've already been answered.

---

