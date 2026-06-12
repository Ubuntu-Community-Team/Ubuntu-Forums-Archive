---
title: "update-manager"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by jvillan555 on 2007-11-06
newbie to ubantu...........sorry about that.I should have jump the M.S. ship a long time ago.....my question is how would I resolve my update manager issue that keeps popping up every time i try to update ubuntu.The problem started when the update manager froze and  I rebooted the system.

please help thanks....This is the message i get every time i update .....       
 
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'http://packages.medibuntu.org/' is not known on line 81 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by rsambuca on 2007-11-06
You just have a typo in your sources.list file.  Open a terminal and post the output of```
cat /etc/apt/sources.list
```

---

### Post by Pumalite on 2007-11-06
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

Maybe you need the key. If not, you can edit your /etc/apt/sources.list and comment out the offending repository.

---

### Post by jvillan555 on 2007-11-06
i have tried both of your ideas........but to no avail......


what next? 

jaime@jaime-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://ftp.debian.org](http://ftp.debian.org) sarge maindeb
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

jaime@jaime-desktop:~$

---

### Post by rsambuca on 2007-11-06
Your Sources list is completely messed up.  I would just start fresh with a new list.  You can go to [this site to generate a new one]("http://www.ubuntu-nl.org/source-o-matic/").

---

### Post by Pumalite on 2007-11-06
+1

---

### Post by jvillan555 on 2007-11-06
this web site was useless ......the info is for older versions of ubantu........any other suggestions to get a new source list 


thanks for all your help

---

### Post by rsambuca on 2007-11-06
No, actually the site is not useless.  Perhaps you should be less hasty in your judgements.  Look at the attached picture.  You will see that you just have to click on a tab to select your version of Ubuntu.

---

### Post by jvillan555 on 2007-11-07
hello again I have tried to follow the directions to the tee in this website but to no avail.....

this is the message i get????

jaime@jaime-desktop:~$ # Automatically generated sources.list
jaime@jaime-desktop:~$ # [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
jaime@jaime-desktop:~$ #
jaime@jaime-desktop:~$ # If you get GPG errors with this sources.list, locate the GPG key in this file
jaime@jaime-desktop:~$ # and run these commands (where KEY is replaced with that key)
jaime@jaime-desktop:~$ #
jaime@jaime-desktop:~$ # gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
jaime@jaime-desktop:~$ # gpg --export --armor KEY | sudo apt-key add -
jaime@jaime-desktop:~$ #
jaime@jaime-desktop:~$ # If you don't know what to do with this file, read
jaime@jaime-desktop:~$ # [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
jaime@jaime-desktop:~$ 
jaime@jaime-desktop:~$ # Ubuntu supported packages
jaime@jaime-desktop:~$ # GPG key: 437D05B5
jaime@jaime-desktop:~$ deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted 
bash: deb: command not found
jaime@jaime-desktop:~$ deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
bash: deb: command not found
jaime@jaime-desktop:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
bash: deb: command not found
jaime@jaime-desktop:~$ 
jaime@jaime-desktop:~$ # Ubuntu community supported packages
jaime@jaime-desktop:~$ # GPG key: 437D05B5
jaime@jaime-desktop:~$ deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe multiverse 
bash: deb: command not found
jaime@jaime-desktop:~$ deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
bash: deb: command not found
jaime@jaime-desktop:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse
bash: deb: command not found
jaime@jaime-desktop:~$ 
jaime@jaime-desktop:~$ # Ubuntu backports project
jaime@jaime-desktop:~$ # GPG key: 437D05B5
jaime@jaime-desktop:~$ deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse 
bash: deb: command not found
jaime@jaime-desktop:~$ 
jaime@jaime-desktop:~$ # Upstream Opera
jaime@jaime-desktop:~$ # GPG key: 6A423791
jaime@jaime-desktop:~$ deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 
bash: deb: command not found

---

### Post by rsambuca on 2007-11-07
OK, it looks like you are having a bit of trouble here!  Don't worry, we can help you out.  I will create a sources.list for you and give you instructions on how to implement it.  I just need to know where abouts you live in order to get the best download site.

---

### Post by jvillan555 on 2007-11-07
texas.............ehhaaaaaaaaa

thanks 
jmv

---

### Post by rsambuca on 2007-11-07
Actually, what may be easiest is for you to use the Software Sources first.  

1.  Go to your top menu bar and select "System -> Administration -> Software Sources".  
2.  Once the Window opens, on the first tab called "Ubuntu Software", make sure all of the boxes are checked to activate all of your repository sources.
3.  Press the Button beside "Download from:" and select "Other..."
4.  A new Window will open called "Choose a Download Server".  Press "Select Best Server".  It will then test them all and pick the fastest current one to you.
5.  Once it is finished its test it will highlight a selection for you.  Press the button on the bottom that says:  "Choose Server".
6.  Close your software sources and Reload your sources when prompted.

Then come back here and let us know how it goes.  We can then add the medibuntu repo (since it looks like you already tried to add it previously, but one thing at a time!).

---

### Post by jvillan555 on 2007-11-07
I tried several servers  and i get the same error message......


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by rsambuca on 2007-11-07
Please re-read number 4.  I recommended that you do not pick a server on your own.  Press the button that says "Select Best Server"

---

### Post by jvillan555 on 2007-11-07
I did and still the same message.

---

### Post by jvillan555 on 2007-11-07
this message as well

E. Type 'http://packages.medibuntu.org/' is not known on line 78 in source list /etc/apt/sources.list
E: Unable to lock the list directory

---

### Post by rsambuca on 2007-11-07
Hmmm...  I am starting to think there may be something else wrong with your setup, like perhaps your internet connection.

---

### Post by rsambuca on 2007-11-07
OK, let's do this manually then.

Open a terminal and enter```
gksudo gedit /etc/apt/sources.list
```
Delete everything in the list.
Copy and paste this into your sources.list and save it.```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

```

---

### Post by jvillan555 on 2007-11-07
thank  you ......... that was very helpful......also thank you for your patience...I guess us newbies are very problematic ........by the way were is the link to donate?......can you donate thru paypal?  


thanks 

jmv

---

### Post by rsambuca on 2007-11-07
> **jvillan555 said:**
> thank  you ......... that was very helpful......also thank you for your patience...I guess us newbies are very problematic ........by the way were is the link to donate?......can you donate thru paypal?  


thanks 

jmv

Good to see you have it working!  

[http://www.ubuntu.com/community/donations](http://www.ubuntu.com/community/donations)

---

