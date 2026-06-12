---
title: "Can't access the repositories"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aum11 on 2009-09-01
Just installed 9.10 yesterday and all is progressing well, except for one strange problem.

Although Synaptic initially worked well, it is no longer able to access the repositories. Even reload will not work.  I have changed the mirror back to main server...still the same.  The rest of the Internet access is fine, including sending in this email.

If have tried rebooting the laptop and the router, to no avail.

Is this a known bug?

Thanks

---

### Post by aum11 on 2009-09-01
This is a total show-stopper guys.

Have tried sudo apt-get update on terminal and it times out as well.

Any suggestions?

---

### Post by taavikko on 2009-09-02
Just did an "aptitude update etc." it worked as usual.

---

### Post by scheuri on 2009-09-02
Just for the sake of asking:
You do have a working internet connection, don't you?
Does your browser work?
Does a CLI-tool (such as wget) work as well?

Cheers
scheuri

---

### Post by aum11 on 2009-09-02
Still not working...and all other Internet is fine.

---

### Post by bacardiandwatermelon on 2009-09-02
You could blank the /etc/apt/sources.list file, do an apt-get update then go into Synaptic and the add the multi and universe repos again..

---

### Post by aum11 on 2009-09-02
> **bacardiandwatermelon said:**
> You could blank the /etc/apt/sources.list file, do an apt-get update then go into Synaptic and the add the multi and universe repos again..

Tried this, but still the same problem.

---

### Post by taavikko on 2009-09-02
You're using main server? 

What does the following print
```
tracepath 91.189.88.46
```

You can see that it's ubuntu's IP
```
devil@core7:~$ host archive.ubuntu.com
archive.ubuntu.com has address 91.189.88.46
archive.ubuntu.com has address 91.189.88.45
archive.ubuntu.com has address 91.189.88.40
archive.ubuntu.com has address 91.189.88.31
archive.ubuntu.com has address 91.189.88.140
```

---

### Post by aum11 on 2009-09-03
Will wait until the beta emerges.

Thanks for Your help

---

### Post by kansasnoob on 2009-09-03
If you're still reading I'd be curious to see your sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by aum11 on 2009-09-03
Here it is :

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090812.3)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main universe restricted multiverse

---

### Post by Shlomir on 2009-09-03
I'm having similar problems. My repos seemed to have braken, here is my sources.list file```
# added by the release upgrader
deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
# 
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```

---

### Post by taavikko on 2009-09-03
> **Shlomir said:**
> I'm having similar problems. My repos seemed to have braken, here is my sources.list file

this is for karmic discussion, you're running jaunty.

But replace your sources.list with this
```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ jaunty universe                      
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe                  
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe              
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

# deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```

---

### Post by aum11 on 2009-09-03
Just installed alpha 5 and it went well.  I was really impressed with the informative and friendly general knowledge messages coming up through the boot.  A very good idea...very new user friendly.

However, on rebooting all the other partitions did not show up."sudo update-grub" fixed that thank God.

But the big hangup for me is that synaptic and "sudo apt-get update" never get anywhere.  The same happened to me under alpha 4, and I could not resolve it.



[PHP]sudo apt-get update
Err http://archive.canonical.com karmic Release.gpg                            
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com karmic/partner Translation-en_AU              
  Unable to connect to archive.canonical.com http:
Err http://archive.ubuntu.com karmic Release.gpg                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com karmic/main Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic/restricted Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic/universe Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic/multiverse Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-updates Release.gpg
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-updates/main Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-updates/restricted Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-updates/universe Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-updates/multiverse Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-security Release.gpg
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-security/main Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-security/restricted Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-security/universe Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Err http://archive.ubuntu.com karmic-security/multiverse Translation-en_AU
  Unable to connect to archive.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_AU.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[/PHP]

[PHP]cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha amd64 (20090902.1)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
[/PHP]

---

### Post by crimsun on 2009-09-03
> **aum11 said:**
> [PHP]sudo apt-get update
Err http://archive.canonical.com karmic Release.gpg                            
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com karmic/partner Translation-en_AU              
  Unable to connect to archive.canonical.com http:
Err http://archive.ubuntu.com karmic Release.gpg                               
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[/PHP]

Do you have a proxy configured?

---

### Post by aum11 on 2009-09-04
Thanks for Your reply,and no proxy.

Basically, just installed and done nothing else.

---

### Post by Sub101 on 2009-09-04
Can you access other websites on the machine? Or is it just the apt-get update that fails?

Might be worth trying:

```
sudo aptitude update
```

though chances are will give the save response.

---

### Post by jonick on 2009-09-04
I had this same issue this morning whilst upgrading an install that had been "talking" to the repo's fine for two weeks. I swithched from the main server to the UK server (I normally use the UK server anyway, but it had a glitchy upload last week) As soon as I switched to the UK server the upgrade ran fine.

---

### Post by aum11 on 2009-09-04
I also changed the server from Main to the Australian one, and it also failed.... but now 7 hours later it is working.....weird.

Busy downloading packages right now.

Thanks guys.

---

