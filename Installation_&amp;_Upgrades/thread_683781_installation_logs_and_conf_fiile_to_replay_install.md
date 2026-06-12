---
title: "installation logs and conf fiile to replay installation"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by sudoyang on 2008-01-31
Does Ubuntu 7.10 save the installation logs somewhere on the disk?  Does it save a config file that can be used to replay an installation?  I'm a long time user of RedHat/CentOS which saves the installation log and the kickstart configuration file that can then be used to replay an installation.  I wonder if something similar exists for Ubuntu.

thanks

---

### Post by SunKing2 on 2008-01-31
look at  
/var/log/dpkg.log

recent installs.    

I know the dpkg command has a logfile option on it, but like me, you probably use
apt-get

so that's probably of no use to you.

---

