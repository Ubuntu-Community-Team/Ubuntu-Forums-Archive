---
title: "is security.ubuntu.com still down??"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by dj-toonz on 2006-08-03
hi all is the above still having problems or not, i've changed the sources.list to one i found what was working but for some reason the server what's been added for the security updates is so slow i.e about 130 kbs and when i did a update with the new sources.list it tock just over an hour to download & update the box (that's on a 16meg connection) normally it takes about 2 mins to download the updates and about 1 min or so to update the box. here's my sources list i'm writting this using the live cd as i cant download or update the machine if my downloads are either going to fail @ the secucity.com part of take like 10 kbs or the like to download, i've even tried changing the cc part to another one and still the same, even tried removing the cc complety and that's like omg failed 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

it only seems to be the security part what seems to be affected and i noticed the ubuntu forums were down a little eariler so does anybody know if the security problems been sorted or not?

---

### Post by dj-toonz on 2006-08-03
see'ing as nobody has replayed to the question, i'll take that as a no/yes or a maybe then & i thought the ubuntu communacity was helpfull, i must of been asleep when i heard that :-( doesnt help me much

---

### Post by Jc2k on 2006-08-03
Don't know if its still down but there were 78mb of updates, it's not normally that much! (New Gnome?). Plus, if all the Ubuntu community is updating, the servers would take some hammer?

---

### Post by emperor on 2006-08-03
The security repo is not working for me either. I also found the archive's down but worked when I added "us.".

---

### Post by Jasper Houtman on 2006-08-03
Just updated. 
I could connect without any problem.
So it seems to be fixed.

---

### Post by videodrome on 2006-08-03
Still down for me.

---

### Post by iXneonXi on 2007-07-11
Revived thread.
What seems to be the problem?
0% [Connecting to security.ubuntu.com (91.189.88.31)]

---

### Post by bhold on 2007-07-11
I had problems installing from security.ubuntu.com last night, same problem this morning. Are these threads the best way to report this problem? If not, how should this be reported? Obviously it is not good to let stuff like this go unattended for too long.

------------------------------
Error message...

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/](http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/)
libmagick9_6.2.4.5.dfsg1-0.14ubuntu0.1_i386.deb

---

### Post by iXneonXi on 2007-07-11
They probably know about it and are working on it but haven't posted any notice. I can say theres a big Open Office update that is trying to be pulled from security.ubuntu.com and I can't get the files. It could be so many are trying to download it starts timing out.

---

### Post by RedLine_by on 2007-07-11
[http://security.ubuntu.com/ubuntu/pool/universe/a/asterisk/asterisk_1.2.12.1.dfsg-1ubuntu1.4_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/a/asterisk/asterisk_1.2.12.1.dfsg-1ubuntu1.4_all.deb)

i can not download this package.. what problem with this server?

---

### Post by Panzor on 2007-07-11
```
0% [Connecting to security.ubuntu.com (91.189.88.31)] 

```
Same problem as everyone else. I'm guessing someone put it on the list before it was posted on the servers?

---

### Post by RedLine_by on 2007-07-11
and where we can write bug report about this ???

---

### Post by AJB2K3 on 2007-07-11
Im gettting issues with the current OOo update from security.ubuntu is there a way around this?

---

### Post by krazyenglishman on 2007-07-11
Down for me too, but i think there is alot of panic over nothing, Just wait till the servers are more free or it's been fixed. It's not like windows where if you don't grab the updates your pc will be hacked into and virused up to it's eyeballs within 10 seconds lol

Ubuntu is about freedom, chill :)

---

### Post by Mehster on 2007-07-11
I show security.ubuntu.com as down. It's buggin' me because I had to reinstall my system last night and I am just a couple packages away from being all done :(

---

### Post by RedLine_by on 2007-07-11
:(

---

### Post by ashz on 2007-07-11
lucky that u reinstalled yesterday i got a new hd today so am reinstalling on that...dear god its slow!!

all i want is my restricted drivers damn youuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu security.ubuntu!!!

---

### Post by azc on 2007-07-11
I was having the same problems this morning, and what cleared things up for me was to do this:

System > Administration > Software Sources > Download from: (and then I selected a nearby mirror.)

Anyway, OpenOffice is now updated and the Word Processor, Spreadsheet, etc. at least open and show the latest updated version.

---

