---
title: "virtualbox update manager fails"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by Wye Knott on 2010-12-09
Just installed 10.10 under Oracle VM VirtualBox and then installed VBOX additions to clear up monitor issues.  Mozilla Firefox works and so does Evolution mail client (needs work though).  

Everything seems to work EXCEPT Update Manager.  I consistently get Failure message: "Failed to download package files"
Here are the details:

[I][INDENT]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1023.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1023.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.3_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23_2.6.35-23.40_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23_2.6.35-23.40_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23-generic_2.6.35-23.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23-generic_2.6.35-23.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80][/INDENT][/I]

I don't understand what's going on here.

Help,
Wye

---

### Post by plucky on 2010-12-10
> **Wye Knott said:**
> Just installed 10.10 under Oracle VM VirtualBox and then installed VBOX additions to clear up monitor issues.  Mozilla Firefox works and so does Evolution mail client (needs work though).  

Everything seems to work EXCEPT Update Manager.  I consistently get Failure message: "Failed to download package files"
Here are the details:

[I][INDENT]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1023.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.35-1023.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-23-generic_2.6.35-23.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8o-1ubuntu4.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.23-0ubuntu3.3_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.32.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/utouch-grail/libutouch-grail1_1.0.15-0ubuntu1_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23_2.6.35-23.40_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23_2.6.35-23.40_all.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23-generic_2.6.35-23.40_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-23-generic_2.6.35-23.40_i386.deb) 404  Not Found [IP: 91.189.92.170 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8o-1ubuntu4.2_i386.deb) 404  Not Found [IP: 91.189.92.166 80][/INDENT][/I]

I don't understand what's going on here.

Help,
Wye

Open a terminal (**Applications > Accessories > Terminal**) and post output of ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by Wye Knott on 2010-12-10
> **plucky said:**
> Open a terminal (**Applications > Accessories > Terminal**) and post output of ```
cat /etc/apt/sources.list
sudo apt-get update
```

Thanks for the reply.
I think this is what you wanted me to do.

wlp@wlp-VirtualBox:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
wlp@wlp-VirtualBox:~$ 
wlp@wlp-VirtualBox:~$ sudo apt-get update
[sudo] password for wlp: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [65B]
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [57.3kB]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [27.2kB]    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release        
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]           
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [14B]                     
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [14B]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [16.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [48.6kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [4,985B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [649B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [52.6kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [14B]  
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [19.3kB] 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [1,068B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages [129kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [20.8kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,655B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages [14B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages [65.3kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2,522B]
Fetched 422kB in 3s (117kB/s)                       
Reading package lists... Done
wlp@wlp-VirtualBox:~$ 

I hope this is what you wanted.
Thanks.
Wye

---

### Post by plucky on 2010-12-10
There are no errors showing.Can you now run **update-manager** and see if the errors are still the same.

If there are errors try running from a terminal ```
sudo apt-get upgrade
``` to install any upgrade packages.

Good Luck

---

### Post by Wye Knott on 2010-12-10
> **plucky said:**
> There are no errors showing.Can you now run **update-manager** and see if the errors are still the same.

If there are errors try running from a terminal ```
sudo apt-get upgrade
``` to install any upgrade packages.

Good Luck

I don't know what you did but update-manager ran normally for the first time and all would appear to be well.

I don't know how to mark this as a solved problem on the forum but you fixed it.

Thanks
Wye

---

