---
title: "upgrade has a problem"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by mj125 on 2013-03-26
[TABLE]
[TR]
[TD="class: votecell"]     

              [/TD]
              [TD="class: postcell"]               when I try to upgrade my ubuntu :

  and i type sudo apt-get upgrade
  I get this error:
Setting up rsyslog (5.8.6-1ubuntu9.1) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)



[/TD]
[/TR]
[/TABLE]

---

### Post by schragge on 2013-03-26
Try re-running the post-installation script for *rsyslog* manually to get more meaningful error message:
```

sudo sh -x /var/lib/dpkg/info/rsyslog.postinst configure

```

---

### Post by mj125 on 2013-03-26
No, it's not helping

Setting up rsyslog (5.8.6-1ubuntu9.1) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schragge on 2013-03-26
Sorry if I was not clear enough. The command I suggested was not supposed to solve the problem or change the dpkg output in any way. The purpose was to see what line in the postinst script generates the error. Can you please post the full output of the console command given above?

---

### Post by mj125 on 2013-03-26
now, I get this

+ set -e
+ user_conf=/etc/rsyslog.d/50-default.conf
+ default_conf=/usr/share/rsyslog/50-default.conf
+ ucf --three-way --debconf-ok /usr/share/rsyslog/50-default.conf /etc/rsyslog.d/50-default.con

---

### Post by schragge on 2013-03-26
Okey. So it seems like ucf is failing to put the new version of */etc/rsyslog.d/50-default.conf* in place. Let's troubleshoot it a step further. Run ucf by hand:
```
sudo ucf --verbose --debug=2 --three-way --debconf-ok /{usr/share/rsyslog,etc/rsyslog.d}/50-default.conf
``` and post the result.

---

### Post by mj125 on 2013-03-26
I do this and get:

ucf: The Debug value is 2
ucf: The new file is /usr/share/rsyslog/50-default.conf
ucf: The Destination file is /etc/rsyslog.d/50-default.conf
ucf: The Source directory is /usr/share/rsyslog
ucf: The State directory is /var/lib/ucf
The hash file exists
egrep [[:space:]]\/etc\/rsyslog\.d\/50\-default\.conf$ /var/lib/ucf/hashfile
80de10a8b9f13365de8cc4bbf8efec5e  /etc/rsyslog.d/50-default.conf
The new start file is      `/usr/share/rsyslog/50-default.conf\'
The destination is         `/etc/rsyslog.d/50-default.conf\' (`\/etc\/rsyslog\.d\/50\-default\.conf\')
The history is kept under  \'/usr/share/rsyslog\'
The file may be cached at \'/var/lib/ucf/cache/:etc:rsyslog.d:50-default.conf\'
The destination file exists, and has md5sum:
80de10a8b9f13365de8cc4bbf8efec5e  /etc/rsyslog.d/50-default.conf
The old md5sum exists, and is:
80de10a8b9f13365de8cc4bbf8efec5e
The new file exists, and has md5sum:
80de10a8b9f13365de8cc4bbf8efec5e  /usr/share/rsyslog/50-default.conf
Historical md5sums are not available
ucf: The Debug value is 2
ucf: The new file is /usr/share/rsyslog/50-default.conf
ucf: The Destination file is /etc/rsyslog.d/50-default.conf
ucf: The Source directory is /usr/share/rsyslog
ucf: The State directory is /var/lib/ucf
The hash file exists

then  I type:sudo apt-get upgrade -f

and get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up rsyslog (5.8.6-1ubuntu9.1) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schragge on 2013-03-26
A proper way to deal with it would be hunting down the ucf problem with commands like
```

ucfq -v rsyslog
grep '/etc/rsyslog\.d/50-default\.conf' /var/lib/ucf/hashfile
grep rsyslog /var/lib/ucf/registry

``` and so on, but I think I'll spare you the trouble as there is a simple workaround.

First, try to reinstall rsyslog:
```
sudo apt-get --reinstall install rsyslog
```
If this doesn't help, here is the workaround: just disable ucf in the post-install script:
```

sudo sed -i 's/\tucf/\t#ucf/' /var/lib/dpkg/info/rsyslog.postinst
sudo apt-get -f install

```

---

### Post by mj125 on 2013-03-27
thanks a lot, now every thing is right.

thank you

---

