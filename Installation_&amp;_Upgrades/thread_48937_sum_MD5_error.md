---
title: "sum MD5 error"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by vedro on 2005-07-14
ellow

I have updated extra repositories like it is written here: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
I have copied this example: [http://ubuntuguide.org/sample/sources.list_extrarepositories](http://ubuntuguide.org/sample/sources.list_extrarepositories)
just without the first line because I am using Kubuntu. Then I typed apt-get update which updated my sources. That went well. Then I typed apt-get upgrade to upgrade the system... Everything went ok untill it said that:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main kwifimanager 4:3.4.0-0ubuntu2.1 [183kB]
Got 183kB in 2s (83,9kB/s)
Couldnt get [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kwifimanager_3.4.0-0ubuntu2.1_i386.deb)  Nonmatching sum MD5
E: Some packageg were unable to get. try to use apt-get update or --fix-missing.
I have used this command and there are no errors..

I do not know what does MD5 mean.. What should I do? are there any other extra repositories servers that those that I have now?

have a nice day,
vedro

---

### Post by pixelnate on 2005-07-14
I have also been getting these nomatching MD5 messages when trying to upgrade/install firefox and/or cairo. Can you just ignore the MD5 #s.?

---

### Post by vedro on 2005-07-14
ellow

Have no idea what to do... I cannot install even xchat because libpango1.0-0 1.8.1-0ubuntu2 has a sum MD5 error....
I would be happy if it is possible to disable MD5, or anything to do with it...

Still, have any ideas what to do?

have a nice day,
vedro

---

### Post by radeon4 on 2005-07-14
Dis-ableing the MD5 chesum is not a good idea it is used to verify that the file is the same as one as you downloaded and not tamperd with.  I know that this is a small issue but it is a great security check.

---

### Post by vedro on 2005-07-14
ellow...

Yes, secutity is important... but what can I do now, that I will be able to install the packages?

 :???:

---

### Post by radeon4 on 2005-07-14
If you have gone to the unoffical userguide there should be a shortcut in the browser.  Make sure that you have made the the changes to your /etc/apt/source.list dont forget to make a bakup first.  Then run apt-get update in the consoule and you should be all set.   I had the same issues and this worked for me.

---

### Post by vedro on 2005-07-14
before first edit of my sources.list there was only written:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restrict$
and nothing else...
Then I copyed text from here: [http://ubuntuguide.org/sample/sources.list_extrarepositories](http://ubuntuguide.org/sample/sources.list_extrarepositories)

so my sources.list file contains:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restrict$

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

so this is it... what else I had to do? 

vedro

---

### Post by Seth on 2005-07-14
People, people. The US archive is having issues. All you need to do to fix it is:
```
sudo gedit /etc/apt/sources.list
```
And change each "http://us.archive..." to just "http://archive..."

---

### Post by vedro on 2005-07-14
so so.... 
tnx, so this is the only problem?

---

### Post by radeon4 on 2005-07-14
Hey I was just tring to help :) but seriously I changed mine to uk but if just removing the  us. will do the trick?  I learn more each day thanks.

---

### Post by radeon4 on 2005-07-14
Dont forget to run apt-get update just to make sure.

---

### Post by vedro on 2005-07-14
ellow...

I`ll try tomorow but I think it will work... No I am at my another apartment.. I have an exam tomorow :-)

wish me luck

tnx 4 the help

vedro

---

