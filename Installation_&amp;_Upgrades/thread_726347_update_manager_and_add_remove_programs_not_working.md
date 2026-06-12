---
title: "update manager and add remove programs not working"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by paulnewby on 2008-03-16
Hello Team, 

After installing the updates on 16th March i am now for some reason unable to use the add\remove programme function?

when i press on it it appears to start loading then nothing happens.

The same also happens when trying to run update manager?

Any ideas would be appreciated

Many thanks

---

### Post by scragar on 2008-03-16
try it from a command line, see what the error message is:
```
gksudo /usr/sbin/synaptic
```
and report any errors.

---

### Post by Pumalite on 2008-03-16
You probably have to comment out your 'deb' lines in your /etc/apt/sources.list.
You can go to System>Administration>Software Sources and make sure everything is on except CD and src

---

### Post by paulnewby on 2008-03-16
Thanks for the quick reply.

I have tried both suggestions and no success :-(

Software sources wont open as with update manager and add/remove software?

---

### Post by Pumalite on 2008-03-16
Go to the Terminal and try:
cat /etc/apt/sources.list
Post them here.

---

### Post by paulnewby on 2008-03-16
Here are the results cheers ;-)

paul@paul-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial

---

### Post by scragar on 2008-03-16
wtf?
```
deb http://archive.canonical.com/ubuntu dapper-commercial
```I'm guessing that should be```
deb http://archive.canonical.com/ubuntu dapper commercial
``` but why do you even have dapper repo's anyway?

---

### Post by paulnewby on 2008-03-16
I'm new to Ubuntu so i have no idea what should be in there really! :lolflag:

How can i change it?? to how it shold be ?

---

### Post by scragar on 2008-03-16
```
gksudo gedit /etc/apt/sources.list
```and make the edit.

---

### Post by paulnewby on 2008-03-16
Thank you for your help, sorry to be a pain

so all i need to do is change the on line from 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial

to 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper commercial

and that should sort it?

thanks

---

### Post by Pumalite on 2008-03-16
You can put this: # in front of it.
Before editing, make a backup.
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

---

### Post by scragar on 2008-03-16
gedit automaticly makes backups, and it's such a tiny edit it's not hard to replace.

oh, and you forgot the **cp** in your copy command :P

---

### Post by Pumalite on 2008-03-16
Corrected. Thanks.

---

### Post by paulnewby on 2008-03-17
I have tried to edit the file in text editor, but the file is read only! ;-(

Is there away i can chnge my access permissions?

---

### Post by zvacet on 2008-03-17
```
sudo gedit /etc/apt/sources.list
```

---

### Post by scragar on 2008-03-17
```
gksudo gedit /etc/apt/sources.list
```gksudo for graphical applications.

---

### Post by paulnewby on 2008-03-17
Will that correct the files for me, or will i need to go in and edit the lines?

i'm new to this and dont really know what i am doing :-(

---

### Post by scragar on 2008-03-17
that just launches the editor for you. All you have to do is scroll down to the end and comment out the line by putting a # infront of it.

---

### Post by paulnewby on 2008-03-17
I have read somewhere before about checkin gthe settings in the Software Sources. to fix the problem of the update manager and they add/remove programmes feature not working?

I'm thinking my only option after this is to re-install Ubuntu?

---

### Post by zvacet on 2008-03-19
**system>admin>software sources**>check all boxes under Ubuntu software and updates tab.Reload.

---

