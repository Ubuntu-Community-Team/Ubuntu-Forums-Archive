---
title: "Unintalled apt!"
date: 2006-05-23
forum: Installation &amp; Upgrades
---

### Post by brianj774 on 2006-05-23
Hi all.

Well, I've managed to rather completely hose up my installation (breezy).  I was trying to install the VM player, following along with the directions nicely, when it mentions to me that I have 4.0x installed, and I need 3.4x installed.  I open up adept, and (stupid me) uninstall gcc 4.0, and try to install 3.4.  I only found out after the fact that they co-exist quite nicely.

Suddenly, I notice that I'm uninstalling quite a bit of stuff....I don't know what all got removed, but I saw some of it: Apt and Adept and gcc.

Fortunately, I still appear to have dpkg, so maybe its possible to get something going again quickly.

Can anyone offer some advice on how to get my installation back up?  I figure if I can get apt and adept working again, I can manage the rest easily enough.

Thanks.

Brian  ](*,)

---

### Post by aysiu on 2006-05-23
Paste these two commands back into a terminal: ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by brianj774 on 2006-05-23
Thanks for the response,  Here's what i'm getting...

brianj@tinas-ubuntu:~$ sudo apt-get update
sudo: apt-get: command not found
brianj@tinas-ubuntu:~$  

I think I need to do something to get apt installed again first.

---

### Post by aysiu on 2006-05-23
Oh, that's bad. If apt is gone, that's bad. Let me poke around Google and see if I can find something...

---

### Post by brianj774 on 2006-05-23
Thats what I'm doing too...

here's what I'm currently working on.

ttp://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt-utils_0.6.40.1ubuntu9_i386.deb&md5sum=150ac579b642b71a5454ea23a91d8b59&arch=i386&type=main

I've downloaded apt-utils from the above link, and I'm trying to dpkg it...its giving me errors:

dpkg: dependency problems prevent configuration of apt-utils:
 apt-utils depends on libapt-pkg-libc6.3-6-3.10; however:
  Package libapt-pkg-libc6.3-6-3.10 is not installed.
  Package apt which provides libapt-pkg-libc6.3-6-3.10 is not installed.
dpkg: error processing apt-utils (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt-utils
brianj@tinas-ubuntu:~/Desktop$   


So, if I can just get the actual 'apt' package, and dpkg THAT, maybe I'll be allright... :)

Or, maybe there's a better way.

Thanks

---

### Post by aysiu on 2006-05-23
I was going to suggest you do this: ```
wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.10ubuntu4.tar.gz
tar -zxf dpkg_1.13.10ubuntu4.tar.gz
cd dpkg-1.13.10ubuntu3
./configure
make
sudo make install
``` But then it occurred to me that you don't have *build-essential* and the easiest way to get *build-essential* is to *apt-get* it...

Let me think about this.

When you type ```
sudo dpkg -i blah.deb
``` Do you get that the command isn't found or the file isn't found?

**Edit**: I just read your last post. So *dpkg* works. That's good. I wonder why you're running into dependency problems, though.

---

### Post by brianj774 on 2006-05-23
Hi,

I was able to hunt down the actual 'apt' package from

[here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fa%2Fapt%2Fapt_0.6.40.1ubuntu9_i386.deb&md5sum=2c4292a43cda43291585d77edce5ea46&arch=i386&type=main")

and dpkg that.  I now have apt-get

WOO.

So, back to your earlier instructions.
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

update works, but kubuntu-desktop does not, for the simple fact that I can't locate my kubuntu 5.10 installer disk (I'm moving on saturday, its packed deep!)

any thoughts?

---

### Post by aysiu on 2006-05-23
[QUOTE=brianj774]
update works, but kubuntu-desktop does not, for the simple fact that I can't locate my kubuntu 5.10 installer disk (I'm moving on saturday, its packed deep!)[/QUOTE] You don't have online repositories enabled--only the CD-ROM repository? Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by brianj774 on 2006-05-23
```
brianj@tinas-ubuntu:/etc/apt$ cat /etc/apt/sources.list

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Source for Canon Pixma ip1500 drivers
## apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj
deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian ./
brianj@tinas-ubuntu:/etc/apt$                         
```

---

### Post by brianj774 on 2006-05-23
okay....easy enough...

I commented out the cdrom section, and re-ran...its going now....

I actually looked at that earlier, but didn't see the cdrom section until I'd posted it....

Thanks!

---

### Post by aysiu on 2006-05-23
Your sources.list looks okay to me. It really couldn't find Kubuntu in there? That's odd.

Try this, then: ```
wget -c http://www.psychocats.net/ubuntu/breezy.list
sudo mv /etc/apt/sources.list /etc/apt/sources_backup.list
sudo mv breezy.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo mv /etc/apt/sources_backup.list /etc/apt/sources.list
```

**Edit**: Once again, you solved it on your own. Good on you.

---

### Post by brianj774 on 2006-05-25
Thanks a bunch for all your help.  Even though I ultimately resolved the problem myself,,, you gave me the clues I needed to point me in the right direction.

Thanks again,

Brian

---

