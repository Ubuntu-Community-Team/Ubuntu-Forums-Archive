---
title: "Synaptic and apt broken?"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Biochem on 2007-05-28
I updated to the new kernel (2.6.20-16) this morning. Now I wanted to start synaptic it flashes and dissapear. I tried in the terminl and got:

```
$ sudo synaptic
Password:
Segmentation fault (core dumped)
```than I tried apt-get update and it worked but when I tried upgrade I get:

```
$ sudo apt-get upgrade
Reading package lists... Done
Segmentation fault (core dumped)
```So I have three question:[LIST=1]
[*]Am'i alone to have this problem?
[*]How can I fix this? (tired reboot but doesn't change anything)
[*]What is a core dump?[/LIST]In cases someone is interested, I Solved the problem by reinstalling the OS.

---

### Post by NZ-Wanderer on 2007-05-28
Try rebooting using 15, not 16...

There seems to be a growing list of problems with 16, check out this thread:

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

Although yours seems to be the first of what you described..

I booted using 15, and completly removed 16 using synaptic.

Sorry I can't be of more help...

---

### Post by Biochem on 2007-05-28
I Just booted the 15 kernel and still get the segmentation fault :(
I will try the recovery mode

---

### Post by taurus on 2007-05-28
Shouldn't be running synaptic with sudo.  Should have used gksudo instead.

```
gksudo synaptic
```
Otherwise, try

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Biochem on 2007-05-28
I did tried apt-get update and apt-get upgrade (also tried aptitude) in kernel 16 and 15 (normal and recovery mode) and I do get the segmentation fault (in recovery I get:

Segmentation faulty ...50%  If that can be any help.

As for gksu it simply doesn't work and since it is in the graphical environment it doesn't give any feed back. So IMO sudo is the best option for debugging and it does work for graphical app, when they are not broken of course.

---

### Post by taurus on 2007-05-28
Are you running x86 or x86_64 version of Feisty?  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

Also, read this about sudo and gksudo.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Biochem on 2007-05-28
I'm using the x86 version of Feisty (conky says i686 if that is of any use)
Here is my sources.list

```
$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```As for the sudo/gksu issue;

```
$ gksu synaptic
$ sudo synaptic
Segmentation fault (core dumped)
$
```Both command were made one after the other. Notice that gksu doesn't give any information as to what the problem is, whereas sudo tells me it's a segmentation fault. Now, I really no idea what it means but it could give someone else a clue as to what is happening. 

Normally, I would agree with you that gksu is better for graphical application, especially since it work with alt+F2 and therefore is faster and I did read the psychocats tutorial before. However, when a specific program doesn't start at all, I think that sudo as a net advantage in telling you what is wrong.

---

### Post by taurus on 2007-05-28
Have you tried to reboot your machine?

---

### Post by Biochem on 2007-05-28
I did. I also tried the previous kernel and the recovery mode and I always have the same problem.

---

