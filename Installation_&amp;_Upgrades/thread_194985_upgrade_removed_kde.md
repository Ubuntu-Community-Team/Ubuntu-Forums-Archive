---
title: "upgrade removed kde"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Latem on 2006-06-12
Hello,

I had Breezy, with KDE 3.5.1.  Yesturday I tried upgrading to dapper, and it didnt work as successfully as I had expected/hoped it would.  

First, here's my sources.list:

```
# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 


deb http://ca.archive.ubuntu.com/ubuntu dapper main restricted 
deb-src http://ca.archive.ubuntu.com/ubuntu dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted 
deb-src http://ca.archive.ubuntu.com/ubuntu dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse 
deb-src http://ca.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
# deb-src http://ca.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 

# deb http://security.ubuntu.com/ubuntu dapper-security universe 
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe 

deb http://kubuntu.org/packages/kde-latest dapper main 
#deb http://kubuntu.org/packages/amarok-1.3.8 dapper main 

```

Exact procedure that I did was:

1) backed up my original sources.list
2) Edited my sources.list and replaced all instances of "breezy" with "dapper", except for the first line for the Breezy CD, which is commented.  Also I commented the last line for amaroK 1.3.8, since that's just for breezy.  The kde-latest line was added there when I upgraded my KDE in breezy to 3.5.1.  Since 3.5.3 was recently released, I left it there because I thought I could kill 2 birds with one stone; that is, upgrade to dapper, and get the latest KDE.
3) I logged out. and did a console log in
4) did sudo apt-get update
5) did sudo apt-get dist-upgrade

Because I was in concole login, and couldnt read the whole big message about what was going to be upgraded, removed, and installed.  I trusted it, and just proceeded to press Yes.  There were like 400-something packages to be upgraded, 100-something to be removed, and 100-something to be added; totaling 480 MB.  This seemed reasonable enough I guess, at the time.  So I proceeded.  7 hours later, i watched it install everything, and as part of that, it removed all my kde stuff.  I think, it never got downloaded, and it definitly didnt get installed.  So I am not sure exactly what went wrong and why.  From looking around this forum now, this seems like it isn't too uncommon of a problem?  My system seems to work ok.  I have a new kernel, it boots up fine, and everyhing goes OK.  It just boots to console.  So I just want to know whats the best way of fixing this.  First, is my sources.list file OK? I compared it to this ( [http://www.ubuntuforums.org/showthread.php?p=1090438](http://www.ubuntuforums.org/showthread.php?p=1090438) ), and there are some minor differences except the kde-latest line, but overall it seems OK to me, but I am not sure.  Second, if it is OK, do I just do sudo apt-get kubuntu-deskop to get a working desktop system?  If possible I would like to get KDE 3.5.3.

Thanks,

Latem

---

### Post by rbalfour on 2006-06-12
You should just do

$ apt-get install kubuntu-desktop

To get back the proper settings.

---

