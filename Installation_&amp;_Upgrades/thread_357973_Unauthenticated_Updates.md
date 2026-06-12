---
title: "Unauthenticated Updates"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by wacole on 2007-02-10
Just clicked on my update icon (6.10) and find that some of today's updates are "unauthenticated" and come with a nice warning that, effectively, says don't use these.  The updates are:

linux-image-2.6.15-28-386
linux-image-386
linux-restricted modules-2.6.15-28-386
linux-restricted-modules-386

What's going on here?  I'm not risking my kernal on unauthenticated modules.  Why is Ubuntu distributing these if they are flagging them as not safe?

Just curious.

Thanks much.

---

### Post by shane2peru on 2007-02-10
> **wacole said:**
> Just clicked on my update icon (6.10) and find that some of today's updates are "unauthenticated" and come with a nice warning that, effectively, says don't use these.  The updates are:

linux-image-2.6.15-28-386
linux-image-386
linux-restricted modules-2.6.15-28-386
linux-restricted-modules-386

What's going on here?  I'm not risking my kernal on unauthenticated modules.  Why is Ubuntu distributing these if they are flagging them as not safe?

Just curious.

Thanks much.

If they are 'unauthenticated' the probably means you have repositories in your sources.list that are not official sources.  That could very well be backports.   It is hard to tell without seeing your sources.list.  In the terminal type:  ```
cat /etc/apt/sources.list
``` and paste the output here.  That will probably answer the question.

Shane

---

### Post by wacole on 2007-02-11
One learns something daily about this environment.  Here is the output of the cat command:
============================================ Start
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted univers e multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted univer se multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

# deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/


# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

# deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe m ultiverse

## created by arnielistenadded
=========================================End

Looks like I have some Automatix material in the mix.  

Thanks very much for your gracious help.

---

### Post by shane2peru on 2007-02-11
> **wacole said:**
> One learns something daily about this environment.  Here is the output of the cat command:
============================================ Start
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted univers e multiverse
[COLOR="Red"]deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted univer se multiverse[/COLOR]

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse

# deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/


# deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

# deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

[COLOR="Red"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe m ultiverse[/COLOR]

## created by arnielistenadded
=========================================End

Looks like I have some Automatix material in the mix.  

Thanks very much for your gracious help.


Bill,  

I have highlighted in the quote the lines that IMHO I would comment out.  The way we are going to comment them out is in the terminal type or paste
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_Backup
```
This will backup your sources.list, next we are going to open and edit it.
```
sudo gedit /etc/apt/sources.list
```
This will open it with gedit, if you are using Kubuntu, you will need to replace gedit with kate.  Find the two lines that I highlighted above and put a '#' in front of the line (without the qoutes)  This will make it a comment instead of an active line.  Now save it and close the editor.
Next:
```
sudo apt-get clean
```
```
sudo apt-get update
```
It is my understanding that backports is for unstable or unsupported software.  
Now you shouldn't have those updates appearing any more.  Hope that helps.  If you need more info, just post back!  

Shane

---

