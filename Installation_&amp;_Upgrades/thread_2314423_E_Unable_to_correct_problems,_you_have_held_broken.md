---
title: "E: Unable to correct problems, you have held broken packages. while installing Ruby"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by Kiran_Shahi on 2016-02-21
Command used:

sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

Following error has be shown while installing Ruby. Can you help me to fix this issue :)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
curl is already the newest version.
curl set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
 libcurl4-openssl-dev : Depends: libcurl3 (= 7.35.0-1ubuntu2) but 7.35.0-1ubuntu2.5 is to be installed
                        Depends: libkrb5-dev but it is not going to be installed
                        Depends: libldap2-dev but it is not going to be installed
                        Depends: librtmp-dev but it is not going to be installed
 libsqlite3-dev : Depends: libsqlite3-0 (= 3.8.2-1ubuntu2) but 3.8.2-1ubuntu2.1 is to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1f-1ubuntu2) but 1.0.1f-1ubuntu2.15 is to be installed
              Recommends: libssl-doc but it is not going to be installed
 libxml2-dev : Depends: libxml2 (= 2.9.1+dfsg1-3ubuntu4) but 2.9.1+dfsg1-3ubuntu4.4 is to be installed
 sqlite3 : Depends: libsqlite3-0 (= 3.8.2-1ubuntu2) but 3.8.2-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by claracc on 2016-02-21
You can try to run the command:

```
sudo apt-get install -f
```

Please see this link: [http://askubuntu.com/questions/30993/fixing-software-center-catalog/183625#183625](http://askubuntu.com/questions/30993/fixing-software-center-catalog/183625#183625) to perform more actions if previous command don't fix the problem.

---

