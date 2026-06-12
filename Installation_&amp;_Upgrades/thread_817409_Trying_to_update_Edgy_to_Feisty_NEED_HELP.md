---
title: "Trying to update Edgy to Feisty NEED HELP"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by abazoskib on 2008-06-03
I've been using Edgy as a beginner to Linux because it was the only thing I could get my hands on. I now have tried to update to feisty because I want to eventually update to the latest version, however when I run update-manager I get this:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]

What should I do about this error? I've tried looking it up and it seems like a lot of people say it is because the server is busy. I doubt a lot of people are updating Edgy at the current time. Any thoughts on my situation?

---

### Post by Pumalite on 2008-06-03
Check your connection. Try changing Server. Remove all third parties from your /etc/apt/sources.list. Post your sources.list

---

### Post by Slim Odds on 2008-06-03
> **abazoskib said:**
> I doubt a lot of people are updating Edgy at the current time. Any thoughts on my situation?

No one is updating Edgy, Edgy has expired as of 2008-04-25

This is why you either have to stick with an LTS release, or be prepared to make sure you upgrade before the old release expires.

It might be possible to edit your source.lst to replace edgy with feisty and try to upgrade

---EDIT---
or dist-upgrade

---

### Post by Pumalite on 2008-06-03
You might want to try this:
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by abazoskib on 2008-06-11
awesome, it worked, thanks so much, but now i have a problem updating to gutsy. im gonna try to avoid starting a new thread and hopefully get an answer here.

i try using the update manager and upgrading to 7.10, everything goes fine until I get an error:

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/dists/feisty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]


any suggestions?

---

### Post by avtolle on 2008-06-11
To (hopefully) take care of the CD-ROM problem, go into Synaptic and uncheck the CD as a source, then reload your sources.

---

### Post by abazoskib on 2008-06-11
now i just get this:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]

---

### Post by avtolle on 2008-06-11
It still is looking for edgy. In your sources.list, comment it out, delete it, or if you don't have a corresponding entry for feisty, edit it from edgy to feisty.

---

### Post by abazoskib on 2008-06-11
thanks so much for the quick replies..im still a noob to linux. exactly how would i go about doing that?

---

### Post by avtolle on 2008-06-11
From the terminal```
cp /etc/apt/sources.list /etc/apt/sources.list.bak #make a backup, just in case
sudo nano /etc/apt/sources.list #opens file for editing
```
Then, scroll down to the offending line; let's do this first, in the line, delete edgy, replace with feisty.
Then, ^o to write, <return> to save file to name that appears, ^x to exit.
Then, while still in the terminal```
sudo aptitude update
``` to update the sources. If the line we just changed results in a duplicate, you will get an error message to that effect. If it no error message appears, then do, still in the terminal```
sudo aptitude safe-upgrade
``` to upgrade your feisty install.
If an error message complaining of a duplicate source appears, again in the terminal```
sudo nano /etc/apt/sources.list
``` and find the duplicate line. To comment it out, put # before it, then do the ^o, etc. to save and ^x to exit as before. Hope this helps.

---

### Post by abazoskib on 2008-06-11
```

#
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ feisty main restricted


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


deb http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu feisty-security universe
# deb-src http://security.ubuntu.com/ubuntu feisty-security universe

```

that is my sources file. i dont see anything about egdy except the top part. is that what needs to be edited?

---

### Post by avtolle on 2008-06-11
Looking over your sources list, I don't see the line complained about previously, so it looks like there's no editing to be done as far as I can see. Try updating again, and see how it goes.

---

### Post by abazoskib on 2008-06-11
same thing. i tried 

```
sudo apt-get update
```

and got this:

```
abazoskib@abazoskib:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy Release.gpg
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com edgy Release
Ign http://us.archive.ubuntu.com edgy/universe Packages
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Fetched 3B in 1s (2B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by avtolle on 2008-06-11
Somehow, someway, your edgy sources are still appearing even though you've edited the list. Failing any other reasonable way, do a restart of your computer and see if the edited sources list takes effect.

---

### Post by abazoskib on 2008-06-11
just restarted. same problem. this is really strange. could it have anything to do with me using apt-get to upgrade from edgy to feisty? the update manager was giving me problems then too.

edit: i just got it to work. under sources where i removed the cd rom, there was also somehting for edgy there. just unchecked it and now its updating. thanks a lot again for all your help avtolle. haha hopefully i can keep upgrading to the newest version without any more problems.

---

### Post by avtolle on 2008-06-11
Yes, it could be caused by that. I'll be right back.

---

### Post by avtolle on 2008-06-11
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion) Take a look at this and the links it contains.

---

### Post by avtolle on 2008-06-11
Just saw your edited post. Good luck from here on.

---

### Post by tmarthal on 2008-07-09
> **Pumalite said:**
> You might want to try this:
sudo sed -i 's/edgy/feisty/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade


I just wanted to add that I had an old 6.10 edgy box, and this worked for me. I wasn't sure about updating the repositories to Feisty would work, but it did. Everything is downloading now, and looks nominal.

I was getting 404 errors and found this post via the search term /ubuntu 6.10 404 update repository/ so hopefully google will index this result for other people that haven't been updating as regularly from the non LTS versions. :)

---

