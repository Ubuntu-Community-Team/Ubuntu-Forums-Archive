---
title: "Server Update and Upgrade"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by vasdjs on 2012-11-05
hi
Although no expert, I have been running a LAMP Ubuntu 10.04 server for about 2 years to host my GLPI IT database.
I usually update it about once a month via ssh without any trouble, but a few months ago it started refusing saying that it was unable to get exclusive lock. I hadn't bothered doing much about it because I had no real problems. Today I started to look at it thinking it had gone on long enough...
I am now stuck with "99% [1 Translation-en_GB bzip2 0B]" errors during the execution of  sudo apt-get update. 
This morning I have tried to examine sources.list and edit it, but that didn't help. I have also cleared the /var/lib/apt/lists/partial directory and renamed the lists folder as .old.
cd /var/lib/apt...i.e 
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
In addition, I tried to upgrade to 12.04 precise in the hope that it might resolve the issue, but that aborted half way through.
There are  a lot of posts on this and similar issues, but my problem is that I don't really understand the update process well enough to pick the bones out of the problem and come up with a sensible diagnosis.
Your help much appreciated
KR's vasdjs

---

### Post by ibjsb4 on 2012-11-05
Have you checked for a dpkg/lock file?  I think that relates to exclusive lock.

[http://ubuntuforums.org/showthread.php?t=1501405](http://ubuntuforums.org/showthread.php?t=1501405)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=unable+to+get+exclusive+lock&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=unable+to+get+exclusive+lock&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by vasdjs on 2012-11-05
thanks, but I think the exclusive lock part of the problem has been resolved, but I still can't update. I have a lock file in /var/lib/apt/lists but that appears to be empty.
The update process has been sticking at different points all day. Currently it gets to...
Get: 40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources [14B]  
Get: 41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources [24.2kB] 
Get: 42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources [1,633B]
99% [1 Translation-en_GB bzip2 0B]      

KR's vasdjs

---

### Post by ibjsb4 on 2012-11-05
> **vasdjs said:**
> thanks, but I think the exclusive lock part of the problem has been resolved, but I still can't update. I have a lock file in /var/lib/apt/lists but that appears to be empty.
The update process has been sticking at different points all day. Currently it gets to...
Get: 40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources [14B]  
Get: 41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources [24.2kB] 
Get: 42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources [1,633B]
99% [1 Translation-en_GB bzip2 0B]      

KR's vasdjs

I believe a lock file would normally appear empty, but if your not getting a lock error then its good.

Those three URL's posted are for source.  Do you compile your own packages?  If not, then you shouldn't need them as far as I know.

---

### Post by vasdjs on 2012-11-06
Thanks for your reply ibjsb4.
No I don't compile packages, and am trying to keep it as simple as possible. Are you suggesting that I could hash these updates out of the sources.list file?
KR's vasdjs

---

### Post by ibjsb4 on 2012-11-06
#yes#

---

### Post by vasdjs on 2012-11-07
Interestingly, once I hashed out the backports, the lock reappeared..."sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory"

At the time I was doing this on my server via ssh whilst my desktop was updating, but I'm pretty certain this has nothing to do with the price of beans!

---

### Post by vasdjs on 2012-11-07
Whereas the error said "Unable to lock the list directory", when I go to /var/lib/apt/lists/lock: The message is "Not a directory" There is a lock file in the lists directory.
Am I missing something here? When I open the lists file there's nothing in it.

---

### Post by ibjsb4 on 2012-11-07
Yes the lock file has nothing in it, I believe that to be correct.  The first three links looks to be good, but different solutions to the same problem.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Flib%2Fapt%2Flists%2Flock&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Flib%2Fapt%2Flists%2Flock&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by vasdjs on 2012-11-07
Thanks
I ran sudo rm /var/lib/apt/lists/* -vf as suggested 
and then sudo apt-get update,but ran into the problem, 
as previously described.
Get: 35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages [280kB]                                                                        
Get: 36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources [104kB]                                                                         
Get: 37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]                                                                     
99% [19 Packages bzip2 0B]   
So, not really any further forward.

---

### Post by ibjsb4 on 2012-11-07
Those ULR's appear to be non-working.  Can you try a different mirror?

[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

---

### Post by vasdjs on 2012-11-19
Hi Still stuck on lock...
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory

I'll try to redirect to another mirror, but not sure how to do this from the command line.

---

### Post by vasdjs on 2012-11-19
Thought I'd cracked it....
Added the following (but edited to "lucid") to my sources.list
deb mirror://mirrors.ubuntu.com/mirrors.txt precise main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-updates main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-backports main restricted universe multiverse 
deb mirror://mirrors.ubuntu.com/mirrors.txt precise-security main restricted universe multiverse
Then ran 
sudo rm /var/lib/apt/lists/* -vf immediately followed by sudo apt-get update. It scrolled thru reams of updates before sticking on
Get: 71 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Packages [1,378B]
Get: 72 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/main Sources [9,423B]
Get: 73 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/restricted Sources [14B]
Get: 74 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/universe Sources [24.1kB]
Get: 75 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-backports/multiverse Sources [1,633B]
99% [10 Translation-en_GB bzip2 0B]           

This looks more like some kind of time out than anything else???

---

### Post by vasdjs on 2012-11-30
Seems like this has died a death and I'm no further forward....there must be a comprehensive guide to updating somewhere?:(

---

### Post by dino99 on 2012-11-30
why are you mixing lucid & precise ? Are you trying to break it ?

look at your sources and maybe do some cleaning

cat /etc/apt/sources.list

---

### Post by vasdjs on 2012-12-03
Hi Dino99
Many thanks for picking this up.
My sources list is all lucid. The reason you see precise in my earlier post is that I copied it from another post and tried it since it was supposed to work with lucid as well as precise (with editing).
My sources.list currently looks like this:- (the #V are the lines I currently have hashed out to try to resolve the problem)

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#vdeb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
#vdeb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse


Any assistance much appreciated.
KR's vasdjs

---

### Post by vasdjs on 2012-12-12
Last orders...can anybody help further?

There are way too many half baked posts on updating. When I get to the bottom of this I'm going to write a comprehensive guide. Honest. :(

---

