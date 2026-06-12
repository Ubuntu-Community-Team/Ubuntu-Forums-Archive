---
title: "Updates / software repos"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by cnkwocha on 2012-12-07
Hello ,

just started using ubuntu. installed the 12.04 on my notebook. a week later, i have over 500+ updates ready to be installed.

Problem is each time i ask to install, i get an error to check my internet connections and messages like below. 

i know it has to do with some settings but have not been able to figure this out. any assist will great.

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_6.5ubuntu6.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_6.5ubuntu6.4_i386.deb) Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_8.13-3ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_8.13-3ubuntu3.2_i386.deb) Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.1.4.2+svn3283-3ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/shadow/login_4.1.4.2+svn3283-3ubuntu5.1_i386.deb) Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.14.2-6ubuntu2.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.14.2-6ubuntu2.2_i386.deb) Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

---

### Post by ibjsb4 on 2012-12-07
Those seem to be bad addresses.  Go to your software sources and uncheck:

[http://archive.ubuntu.com/ubuntu/pool/main/s/shadow/](http://archive.ubuntu.com/ubuntu/pool/main/s/shadow/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

That should fix it.

And welcome to the forums  :)

---

