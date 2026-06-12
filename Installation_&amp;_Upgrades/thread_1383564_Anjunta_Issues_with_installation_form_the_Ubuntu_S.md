---
title: "Anjunta Issues with installation form the Ubuntu Software center."
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Tp2357 on 2010-01-17
I receive the following errors...

[quote="Ubuntu Software Center Error"] Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

anjuta anjuta-common autoconf autogen automake autotools-dev cvs devhelp-common exuberant-ctags gettext intltool libdevhelp-1-0 libgda-4.0-4 libgda-4.0-common libgdl-1-3 libgdl-1-common libgladeui-1-9 libltdl-dev libopts25 libopts25-dev libtool m4 patch
[/quote]

I get this with all other downloads as well... Can someone walk me through on how to fix/circumnavigate this problem?

Thanks!
Tp2357.

PS if it helps, I'm running Karmic... (9.10 I think) :P

---

### Post by chuina on 2010-01-17
if i understand you correctly then,
go to **Applications>Accessories>Terminal**

try to update your software source list first with
```
sudo apt-get update
```
this will require your user password
after completion try to install from software center or use synaptics in **System>Administration>Synaptics Package Manager**

thanks

---

### Post by Tp2357 on 2010-01-17
I get these errors:

E: The method driver /usr/lib/apt/methods/ppa could not be found.
E: The method driver /usr/lib/apt/methods/ppa could not be found.


:( Any other solutions?

---

### Post by chuina on 2010-01-18
Are u trying to install something from any ppa launchpad ?
in that case i'm out of my little resource.

and if not can u post contents of this file (by using any text editor, like gedit): /etc/apt/sources.list

---

### Post by Tp2357 on 2010-01-18
I am using the ubuntu software center....

Here is the file you are looking for:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main

*end of file* (i added this, not in file.)

---

### Post by Tp2357 on 2010-01-18
I am also trying to reinstall the software center...


I still can't get packages, same error as before.

---

### Post by chuina on 2010-01-18
At the bottom of the file there are two http link started with
ppa.

comment those 2 lines by putting a # infront each of them.

```
sudo gedit /etc/apt/sources.list
```
after commenting they should be look like this:

#deb [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main
#deb-src [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main

now, again 
```
sudo apt-get update
```
and 
try to install any soft
thnx

---

### Post by Tp2357 on 2010-01-19
(I changed the file first. :) )

[quote="sudo apt-get update"]
E: The method driver /usr/lib/apt/methods/ppa could not be found.
E: The method driver /usr/lib/apt/methods/ppa could not be found.
[/quote]

Hmm... Good try, but thanks. Here is my new /etc/apt/sources.list .

[quote="/ect/apt/sources.list"]
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
## deb [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main
## deb-src [http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu](http://ppa.launchpad.net/jhs.schmid/ppa/ubuntu) karmic main
[/quote]

Hope I did it correctly... (thanks for all the help... Believe it or not, I'm actually learning a little about linux... :) )

---

### Post by Tp2357 on 2010-01-22
bump.

---

### Post by Tp2357 on 2010-01-26
Is there any way to get some help??

---

### Post by hhlp on 2010-01-26
you have karmic and jaunty packege and this is not good :

change this section like this in your sources.list

sudo gedit /etc/apt/sources.list

after commenting they should be look like this:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb http://archive.canonical.com/ubuntu jaunty partner
#deb-src http://archive.canonical.com/ubuntu jaunty partner
```

now, again

```
sudo apt-get update
```

and
try to install any soft
thnx

---

### Post by eltama on 2010-01-29
As hhlp said, there is something wrong if you are using a jaunty repository on karmic. Try changing that.

I was having the same problem. Whenever I tried to update the repositories, I got:
> E: The method driver /usr/lib/apt/methods/ppa could not be found.
E: The method driver /usr/lib/apt/methods/ppa could not be found.


First I went to Software Sources and unticked all the third party repositories, and I didn't get the error any more. Then I added most of the repositories leaving out the ones I thought could be the problem (specially ppa's), until I found the one causing the problem.

In my case the problem was with the ppa for CoverGloobus, ppa:gloobus-dev/covergloobus. The problem was that I had pasted the ppa directly in the URI box, but it is not an URI address (most start with [http://)](http://)). That's why it complains saying that it cannot find the ppa method.

The easy way to solve it is to remove that repository and add it again from the command line:
```
sudo add-apt-repository ppa:<repository-name>
```

Good luck!

---

### Post by Tp2357 on 2010-02-12
Sorry for the long wait, buit the issue was a wine repository I forgot the encryption key for... /facepalm...

---

