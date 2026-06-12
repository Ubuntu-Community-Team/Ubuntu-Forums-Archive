---
title: "unable to upgrade fro 6.06 to 6.10"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by HarmonicaGoldfish on 2007-03-24
Hello

I am trying to upgrade from 6.06 to 6.10. I have followed all of the instructions on ubuntu's official upgrade page and have tried the process 3 times. Each time it stops during the first part of the upgrade process (the 'preparing' part) as it tries to get repository 22 of 31 with this message:

[http://theli.free.fr/packages/dists/...6/Packages.gz:](http://theli.free.fr/packages/dists/...6/Packages.gz:) 301 Moved Permanently

What should I do?

thanks

part 2...

Just tried the process again and can not even get to the point where my update manager notifies me of the opportunity to upgrade to 6.10.

I get the same error as I previously mentioned with the added bonus of this warning:

W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) dapper-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3

---

### Post by bulldog on 2007-03-24
Comment all the not official repo's in your sources.list [put a # in front of the lines]
Then be sure you haven't a lot of applications installed which aren't from the official ubuntu repositories,because they give a fair chance of ruining your upgrade.

---

### Post by HarmonicaGoldfish on 2007-03-24
Bulldog, thanks for the reply - how do I do that? 

ie:
- how do I get to the sources list?
- how do I know what is not official?

I am a new linux user, learning as I go. Your help is very appreciated!

---

### Post by konungursvia on 2007-03-24
sudo gedit /etc/apt/sources.list

then put a # in front of all of them except the ones with ubuntu in the name of the url

---

### Post by konungursvia on 2007-03-24
However, Montreal friend, the Dapper install you have is probably the best lnux distro ever generated, why do you want to change to 6.10? I would stick with it unless there are specific apps you require that do not run on the slightly older kernel.

---

### Post by HarmonicaGoldfish on 2007-03-24
konungursvia, thanks.

A friend of mine recommended that I upgrade. Is 6.10 that bad according to you?

---

### Post by HarmonicaGoldfish on 2007-03-24
This is what I get with the command: sudo gedit /etc/apt/sources.list

(Not too sure what to comment...)



deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END
deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) dapper-darkmagez games

---

### Post by jackrobinson on 2007-03-24
comment the following lines:
> 
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen
deb [http://mirror.randumb.org/darkmagez/repo](http://mirror.randumb.org/darkmagez/repo) dapper-darkmagez games
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
by making them look as follows:
```

#deb http://theli.free.fr/packages/ dapper listen
#deb http://mirror.randumb.org/darkmagez/repo dapper-darkmagez games
#deb http://people.ubuntu.com/~seb128/deb ./
#deb http://www.getautomatix.com/apt dapper main
```
also change all instances of "**dapper**" to "**edgy**"

---

### Post by HarmonicaGoldfish on 2007-03-28
Thanks to all - I am now upgraded...though having camera import issues...see this thread:
[http://www.ubuntuforums.org/showthread.php?t=395464](http://www.ubuntuforums.org/showthread.php?t=395464)

---

### Post by Chappy7777 on 2007-03-28
FWIW, I am with the Fish on this one. I had unistalled 6.06, installed 6.10, and was so disappointed and even lost when trying to do an autodetect to find my modem. The upshod is that I then unistalled 6.10 and reinstalled 6.06. 

Just my opinion of course. Tho I did ask a question on the Networking Forum about the lack of Autodetect (for modem) in 6.10,  I got no replies, but lots of views. That makes me think no one knew where autodetect is in 6.10 

Stick w/6.06  If it ain't broke don' fix it. I am a noob, but I am finally getting enough of a grasp on 6.06 to at least be able to write this. Big move on my part!

Chap

---

