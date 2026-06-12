---
title: "Failed to install pakcages ''unmet dependencies&quot;"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Bastian83 on 2012-11-13
Hello,

I have one time added the precise-proposed repository to the package source list, I switched it off and now when I am trying to install skype I get following results:

> The following packages have unmet dependencies:
 apache2.2-bin : Depends: libapr1 (>= 1.4.2) but it is not going to be installed
                 Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-dbd-sqlite3 but it is not going to be installed or
                          libaprutil1-dbd-mysql but it is not going to be installed or
                          libaprutil1-dbd-odbc but it is not going to be installed or
                          libaprutil1-dbd-pgsql but it is not going to be installed or
                          libaprutil1-dbd-freetds but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libcap2 (>= 2.10) but it is not going to be installed
                 Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 apache2.2-common : Depends: apache2-utils but it is not going to be installed
                    Depends: procps
                    Depends: perl but it is not going to be installed
                    Recommends: ssl-cert but it is not going to be installed
 libatk-wrapper-java-jni : Depends: libatk1.0-0 (>= 1.18.0) but it is not going to be installed
                           Depends: libgtk2.0-0 (>= 2.12.0) but it is not going to be installed
 libcups2 : Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
 libnss3-1d : Depends: libnss3 (= 3.13.1.with.ckbi.1.88-1ubuntu6.1) but it is not going to be installed
 libpulse0 : Depends: libasyncns0 (>= 0.3) but it is not going to be installed
             Depends: libdbus-1-3 (>= 1.1.1) but it is not going to be installed
             Depends: libjson0 but it is not going to be installed
             Depends: libsndfile1 (>= 1.0.20) but it is not going to be installed
             Depends: libwrap0 (>= 7.6-4~) but it is not going to be installed
 skype : Depends: skype-bin


I have checked and tested multiple things from internet and irc but I still fail to repair it.

Could you please help me? Thank you.

---

### Post by zvacet on 2012-11-15
Be sure that you have partner repository enabled.

```
gksudo gedit /etc/apt/sources.list
```

and remove # sign in front of partner repo line.Save and close.

```
sudo apt-get update
sudo apt-get install skype
```

If that doesn´t work type 

```
uname -r
```

and post output here.

---

### Post by Bastian83 on 2012-11-17
Hello,

Thanks for your reply, the repos are enabled but the update did not change anything :(

The uname returns:

> 3.2.0-32-generic

---

### Post by zvacet on 2012-11-20
Sorry, it is 

```
uname -a
```

I want to know if you are running 64 bit Ubuntu,because I know it was problem with Skype and 64 bit.

---

