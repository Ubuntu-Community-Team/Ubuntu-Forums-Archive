---
title: "Need Help Installing dvdrip...."
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by jroskos on 2005-08-24
whenever i try to install this thru package manager, I get an error saying that "The following packages have unresovable dependencies. Make sure that all required repositories are added and enabled in the prefrences. "dvdrip: Depends: Transcode (>=2:0.6.14) but is not installable""

Here is a screenshot...
[IMG]http://img.photobucket.com/albums/v724/jroskos/Screenshot.png[/IMG]

---

### Post by adamk on 2005-08-27
Hi,

Did you ever solve this problem? I'm getting the same thing when trying to install dvdrip from command line:


adam@felix:~$ sudo apt-get install dvdrip
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not installable
E: Broken packages


Any ideas anyone?

---

### Post by jroskos on 2005-09-07
no i still havent been able to get it installed yet...

---

### Post by AM~FM on 2005-09-08
I have the same problem too.... haven't found any way to get around it.

---

### Post by [pl]ice on 2005-09-08
hi, i had huge problems installing transcode i think that was mainly to using unstable packages, there is quite a bit about transcode on this forum...

how about for dvdrip, you guys install decryptor ... ;) ??  works fine with me.

---

### Post by Emerzen on 2005-09-09
Hi all, I was having major problems installing DVDRip a month or so ago until I realized I didn't have the multiverse repository added to my list.  (It was the same transcode problem, which leads to libc6 dependency problems if you try to do a Marillat repo install.)  So, I made sure I had all the Ubuntu repo.'s available, main-universe-multiverse-backports, removed any 3rd parties (Marillat) and it installed fine.  I'm away from my home computer and it's been awhile now, but I think that was the solution.   Hope that works for everyone.

---

### Post by erbogasto on 2005-09-09
Hi guys ,today in Italy is sunny even if it still rains !!!
This is the very first post in this forum and I'm so happy because this morning i' ve succeeded in installing dvdrip and transcode via apt-synaptic in an easy way ,only by adding these lines to my /etc/apt/sources.list:
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted 
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted 
Dont' activate Marillat's repository !
This is my complete sources.list 
## Main archive
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse 

## Security
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse 

## Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted 
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted 

## Debian-Marillat
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 

I hope that this will help you too  \\:D/

---

### Post by Jenda on 2005-10-02
These repos seem to be down. A few people have complained:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

---

### Post by erbogasto on 2005-10-03
This morning they were up ....
Bye Andrea

---

### Post by tomski on 2005-10-03
they are down now ive had this problem for about a month or 2 same thing

does any one know of working alternative repositories

---

### Post by erbogasto on 2005-10-03
...very strange,because even this morning (5,45 AM in Italy)I've tried it and it was up (downloaded something .deb to try it), try with your browser reaching it and downloading something.Don't you have a firewall that stops ftp access ?
Bye Andrea  :-D

---

### Post by tomski on 2005-10-04
i use personal firewall and have all ports forwarded to me (live life dangerously and play with viri in vmware) but have not been able to use theese for ages its just anoying me coz when i try to convert these avis in windblows the software crashes

---

### Post by tomski on 2005-10-04
this is the problem  :

[http://www.ubuntuforums.org/showthread.php?t=69681](http://www.ubuntuforums.org/showthread.php?t=69681)

i was using the old sever name

---

