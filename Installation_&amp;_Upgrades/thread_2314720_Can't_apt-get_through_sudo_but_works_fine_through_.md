---
title: "Can't apt-get through sudo but works fine through root"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by ant6 on 2016-02-23
folks,

ran a release upgrade to go from 12.04 LTS to 14.04.3 LTS, went well enough and in the midst of trying to reinstall a few things.

i've a number of users in the sudoers group and they can access sudo su etc fine.

but when running sudo apt-get update it'll just hang

> ant@server:/home/ant$ sudo apt-get update
0% [Connecting to gb.archive.ubuntu.com (91.189.88.149)] [Connecting to securit

running the same command while logged in as root is fine.

i've a load of installation scripts that fetch packages under different users so would rather get it working rather than amend those if anyone has any ideas

---

### Post by grahammechanical on 2016-02-23
So, sudo works with other commands but not with apt-get. Right? It seems like it does. It is the connection to gb.archive.ubuntu.com that is not happening. Were you prompted for a password? You must have been prompted. Was the password rejected? No. The command is running but it is waiting for the connection to gb.archive to be accepted.

So, what is the difference between running "sudo apt-get update" from /home/ant & running "apt-get update" as root? This is an example of the URLs in my sources.list produced after running sudo apt-get update

> Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease

Do you see the difference? Could that be it? Your URLs should be showing "trusty-security" and not (91.189.88.149). Maybe?

Regards

---

### Post by ant6 on 2016-02-23
ant@server:~$ sudo apt-get update
[sudo] password for ant:
0% [Connecting to gb.archive.ubuntu.com (91.189.88.149)] [Connecting to securit


never moves from that


ant@server:~$ sudo su
root@server:/home/ant# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease [65.9 kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [105 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources [260 kB]
etcetc

---

### Post by ant6 on 2016-02-23
i've also disabled ipv6 as i thought this might be the issue but seemingly not
likewise same issue running aptitude
ant@server:~$ sudo aptitude update
0% [Connecting to gb.archive.ubuntu.com (91.189.92.200)] [Connecting to security.ubuntu.com (91.189.88.152)] [Connecting to ppa.launchpad.net (91.189.95.83)]



 also just to be clear the other accounts can still access the internet and resolve hostnames it's purely through apt this issue happens

---

