---
title: "After adding Ubuntu Studio repos, update manager produces this error:"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by acelin on 2007-09-23
This is the first error:

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package usp needs to be reinstalled, but I can't find an archive for it.'

and this is the second one:

E: The package usp needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

W: Duplicate sources.list entry [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)


This is my list of sources:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main


What do I need to do to fix my update manager?

---

### Post by SpiritIsReality on 2007-09-24
howdy
I'm no rocket scientist, but I think I've got an answer for the 
> W: Duplicate sources.list entry [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubunt ustudio_dists_feisty_main_binary-i386_Packages)
there's a double entry here> #AUTOMATIX REPOS END
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
now the error is going to take a search or two or...
only funnin'. you've probably heard that one more than once.
trails

---

### Post by SpiritIsReality on 2007-09-24
I got this so far, maybe you've got a better plan, or you could help dig thru this.
we're lookin for something similar to these that helped, I reckon.
[http://www.google.ca/search?hl=en&q=%22E%3A+The+package+*+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22E%3A+The+package+*+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it%22&btnG=Search&meta=)

trails

---

### Post by SpiritIsReality on 2007-09-24
how about this one
[http://www.ubuntugeek.com/tag/package-installation-error/](http://www.ubuntugeek.com/tag/package-installation-error/)
think it's worth a try? you're in the saddle

I'm gonna go back to readin' about vi and emacs
then more command line stuff...oh well... a horse is nice to have
but you've got to clean out the barn...and make hay...haha!

trails

---

### Post by acelin on 2007-09-24
well i removed the double entry- but that isnt the same error.

---

### Post by SpiritIsReality on 2007-09-24
howdy
sorry about the wait
>removed the double entry
that's good
>but that isn't the same error
ok, pardon me, I'm not very good at this, newbie here
what about this article here?
[http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35](http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35)
I figure you could try
```
dpkg --remove --force-remove-reinstreq usp
```
oops, probably need a 
```
sudo dpkg --remove --force-remove-reinstreq usp
```
and see if that let's you use your package manager again.
I've never had this happen to me before and just going by what it says on that web page.
what do you think?
then could try this if you wanted to have usp package installed
[https://help.ubuntu.com/community/USP](https://help.ubuntu.com/community/USP)

---

### Post by acelin on 2007-09-25
Ok- it will not let me remove it-

it says it needs to be reinstalled.

I tried to install the deb. file, but it said the package was corrupted or that I do not have the permissions to open the file.

---

### Post by SpiritIsReality on 2007-09-25
howdy
I'm sorry pard. I'm not swift enough with the inner workings of dpkg or
whatever this needs to get your job done.
There's them that be around here that are. 
I'll crawl back to cover (haha! cover to cover, reading a book and I haven't got
from cover to cover yet, that's my problem)
I just hoped that your problem would be an easy fix. It looks like til somebody
with the answer shows up...drifts off into the bush.

trails

---

### Post by SpiritIsReality on 2007-09-25
I know this is a different package,
but the problem looks the same. I don't know if it is or not though>
Jon "Yogi" seemed to come up with the answer for some, and OffHand for others.
[http://ubuntuforums.org/archive/index.php/t-398709.html](http://ubuntuforums.org/archive/index.php/t-398709.html)
hope someone helps.
[http://ubuntustudio.org/](http://ubuntustudio.org/)
>  It's easy. Just Download Install Create

---

### Post by Seisen on 2007-09-25
Try this:

Open up the terminal and change the directory to  /var/lib/dpkg/info/ by doing this

```
cd /var/lib/dpkg/info/
``` then ```
ls 
``` in the terminal this will list all the files in that location. Find the one that is for the usp package and then copy that into the terminal like this

```
sudo -rm -r usp_1.91_all.deb
``` it might be a different version number. Then run ```
sudo apt-get update
```

---

### Post by SpiritIsReality on 2007-09-25
Seisen ...thanks

---

### Post by acelin on 2007-09-25
do what with the code and the usp package?

---

### Post by SpiritIsReality on 2007-09-25
ok 
I can help you run that thru if you like.
click on Applications then > Accessories > Terminal
when the terminal opens up, type, or copy and paste 
```
cd /var/lib/dpkg/info/
```
then press enter

then type in 
```
ls | less
```
press enter
and press the pg up, pg dn, or arrow keys to have a look for the package.
they're alphabetical, so look for usp, way down the list. hold the page down key down till you see it wiz by.
then write down the usp........package name, for example usp_1.91_all.deb and then press q to quit.
or
```
ls | grep usp
```
that | is the \ key with the shift key pressed.
tell me how you make out, or copy and paste the window here?

or if Seisen shows up again, I'll get out of the line of fire.

you're in the saddle.

---

