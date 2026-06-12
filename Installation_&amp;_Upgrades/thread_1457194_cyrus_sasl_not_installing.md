---
title: "cyrus sasl not installing"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by bluethundr on 2010-04-18
Hello,

I am attempting to enable secure authentication on my homebrew AWS based mail server, by following the very excellent flurdy how-to.

However I think the repositories I am attempting to use do not include this software. 

Oddly enough, an aptitude search finds the packages I want, however even if I copy-paste the name of the software into the install version of the command it turns up nothing. 

```

root@cloud1:~# aptitude search sasl2-bin
i   sasl2-bin                                           - Cyrus SASL - administration programs for SASL users database  
root@cloud1:~# aptitude install sasl2-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

```

root@cloud1:~# aptitude search libpam-mysql
i   libpam-mysql                                        - PAM module allowing authentication from a MySQL server        
root@cloud1:~# aptitude install libpam-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```


```

root@cloud1:~# aptitude search libsasl2-modules
i   libsasl2-modules                                    - Cyrus SASL - pluggable authentication modules                 
p   libsasl2-modules-gssapi-heimdal                     - Pluggable Authentication Modules for SASL (GSSAPI)            
p   libsasl2-modules-gssapi-mit                         - Cyrus SASL - pluggable authentication modules (GSSAPI)        
p   libsasl2-modules-ldap                               - Cyrus SASL - pluggable authentication modules (LDAP)          
p   libsasl2-modules-otp                                - Cyrus SASL - pluggable authentication modules (OTP)           
i   libsasl2-modules-sql                                - Cyrus SASL - pluggable authentication modules (SQL)           
root@cloud1:~# aptitude install libsasl2-modules*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Couldn't find any package matching "libsasl2-modules*".  However, the following
packages contain "libsasl2-modules*" in their description:
  libsasl2-2 
Couldn't find any package matching "libsasl2-modules*".  However, the following
packages contain "libsasl2-modules*" in their description:
  libsasl2-2 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

```

root@cloud1:~# aptitude search libsasl2-modules-sql
i   libsasl2-modules-sql                              - Cyrus SASL - pluggable authentication modules (SQL)        
root@cloud1:~# aptitude install libsasl2-modules-sql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

I am on Ubuntu Server 9.10 using a RightScale image on AWS. 

```

root@cloud1:~# vim /etc/apt/sources.list

deb http://mirror.rightscale.com/ubuntu karmic main restricted universe multiverse
#deb-src http://mirror.rightscale.com/ubuntu karmic main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://mirror.rightscale.com/ubuntu karmic-updates main restricted universe multiverse
#deb-src http://mirror.rightscale.com/ubuntu karmic-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://mirror.rightscale.com/ubuntu karmic-security main restricted universe multiverse
#deb-src http://mirror.rightscale.com/ubuntu karmic-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://mirror.rightscale.com/ubuntu karmic-backports main restricted universe multiverse
#deb-src http://mirror.rightscale.com/ubuntu karmic-backports main restricted universe multiverse
~                                                                                                  

```

---

