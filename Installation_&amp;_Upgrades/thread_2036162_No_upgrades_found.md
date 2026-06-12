---
title: "No upgrades found"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by pcarroll on 2012-08-01
Im running 10.04 LTS server install.  I have run apt-get update which completes successfully followed by apt-get upgrade, however it does not find any upgrades to perform.

I know this is wrong as the server is only running PHP version 5.2.10 and the latest package available according to [http://packages.ubuntu.com/lucid/php/](http://packages.ubuntu.com/lucid/php/) is 5.3.2-1.

My sources.list file is as follows:

```
  GNU nano 2.2.2                                          File: sources.list

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://uk.archive.ubuntu.com/ubuntu/ lucid main restricted

###### Ubuntu Update Repos
deb http://uk.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://uk.archive.ubuntu.com/ubuntu/ lucid-updates main restricted



```

Any help or starting points to look from would be greatly appreciated.

---

### Post by dino99 on 2012-08-01
Dont know if updates are available recently :confused:

[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.4](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.4)

but what are the expected updates you are waiting for ?

is it simple updates or moving to new LTS Precise ?

[https://help.ubuntu.com/10.04/serverguide/configuration.html](https://help.ubuntu.com/10.04/serverguide/configuration.html)

---

### Post by pcarroll on 2012-08-01
> **dino99 said:**
> Dont know if updates are available recently :confused:

[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.4](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.4)

but what are the expected updates you are waiting for ?

is it simple updates or moving to new LTS Precise ?

[https://help.ubuntu.com/10.04/serverguide/configuration.html](https://help.ubuntu.com/10.04/serverguide/configuration.html)

Well the main package I am looking to update is PHP.  The currently installed version according to PHP -v is 5.2.10-2ubuntu6.  It is my understanding that PHP 5.3.2-1 is available and I need to be running at least version 5.3.2 to run the latest edition of Moodle.

---

### Post by pcarroll on 2012-08-01
Ok just managed to solve this.  Seems the guy who ran the box before me wanted to use an older version of PHP so he created files in /etc/apt/preferences.d to make sure that PHP only ever used the karmic version of the PHP files.  Removed these and it now updates.

---

