---
title: "Upgrade Failed On Packages I Didn't Want Anyway"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by llanitedave on 2016-05-23
I tried running a distribution upgrade from 15.10 to 16.04, but only got to the step of checking packages before I generated the following error message:
**Could not calculate the upgrade**


**An unresolvable problem occurred while calculating the upgrade.**


**This can be caused by:**
*** Upgrading to a pre-release version of Ubuntu**
*** Running the current pre-release version of Ubuntu**
*** Unofficial software packages not provided by Ubuntu**


[B]This is most likely a transient problem, please try again later.

[/B]
I thought about doing a clean install, and downloaded the image, but I really didn't want to have to re-install all the third-party packages I already have.  But I figured I'd need to update the computer anyway, so I ran a standard update.  It showed 1.5 g of packages to update -- essentially the entire upgrade!  I ran that and everything downloaded.  It began extracting packages and got all the way to the end.  Then it failed, with the following message:
**Package operation failed**
[B]The installation or removal of a software package failed.

[/B]I ran it again with the terminal open to see where the failure occurred, and it showed the following:
*Errors were encountered while processing*
*/var/cache/apt/archives/account-plugin-facebook_0.12+16.04.20160126-0ubuntu1_all.deb*
*/var/cache/apt/archives/account-plugin-google_0.12+16.04.20160126-0ubuntu1_all.deb*


Now, I'm not at all interested in any facebook packages, and thought I could live without the google one as well, so I entered the directory and removed those packages.  However, when I re-ran the installation, they were simply downloaded again -- and failed again.

So now I'm stuck, when I run an update, the dialog box says:

Not all upgrades can be installed
Run a partial upgrade, to install as many updates as possible.


This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu


It then shows me two buttons, Partial Upgrade, and Continue


For "Partial Upgrade", I get the error:
**Could not calculate the upgrade**

Same as copied above.


For &#8220;Continue&#8221;, I get the 'Package operation failed' error once again.



I'm I going to be stuck with a clean install, or is there some way I can get rid of or ignore those unwanted packages and do the upgrade without them?

BTW, now when I log into my computer, it flashed "Ubuntu 16.04" on my desktop, but when I use the "About this computer" menu, it identifies the system as "Ubuntu 15.10".  

Something's definitely borked.

---

### Post by Bashing-om on 2016-05-23
llanitedave; Weeelllll ...

3rd party (PPAs) {Google} are not part of the ubuntu ecosystem, tacked on clever programming to fit the particular environment.

Let's look at what you have active . and the state now of the package manager;
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

If one does not remove the source fetches ... then when updated .. these packages will be fetched once more !

Once the sources are sanitized then we see what results:
```

sudo apt update
sudo apt full-upgrade

```

get the sources correct before doing anything else and then whittle the problems away .

[INDENT][INDENT]package manager not happy
[INDENT][INDENT][INDENT]no body is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-05-23
Ubuntu has a package manager. Its purpose is to keep a list of what packages are installed/removed/upgraded. Simply deleting a package (library) does not update the package manager's record. This is why we install & remove applications using the Software Centre (Store) or using the apt-get (apt) command line utility. 

How did you try to upgrade from 15.10 to 16.04? Did you use a command? Which one of these three possible causes of the inability to calculate the upgrade fits your situation?

> **This can be caused by:**
*** Upgrading to a pre-release version of Ubuntu**
*** Running the current pre-release version of Ubuntu**
*** Unofficial software packages not provided by Ubuntu**



I have seen examples of people using a certain command even though it will not upgrade 15.10 to 16.04 but will instead attempt to upgrade 15.10 to 16.10 development version. I wonder if you used this command.

```
do-release upgrade -d
```

It is the -d switch. It means development version. Ubuntu 16.04 is no longer a development version. The only Ubuntu development version available is 16.10.

Ubuntu is built on Debian. Here you can read about the package management tools that Ubuntu uses.

[https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

Regards

---

### Post by llanitedave on 2016-05-23
> **Bashing-om said:**
> llanitedave; Weeelllll ...

3rd party (PPAs) {Google} are not part of the ubuntu ecosystem, tacked on clever programming to fit the particular environment.

Let's look at what you have active . and the state now of the package manager;
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

If one does not remove the source fetches ... then when updated .. these packages will be fetched once more !

Once the sources are sanitized then we see what results:
```

sudo apt update
sudo apt full-upgrade

```

get the sources correct before doing anything else and then whittle the problems away .
[INDENT][INDENT]package manager not happy[INDENT][INDENT][INDENT]no body is happy
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


The following packages are specifically listed the etc/apt/sources.list

    53        deb [http://qgis.org/debian](http://qgis.org/debian) xenial main # disabled on upgrade to wily disabled on upgrade to xenial
    54	deb-src [http://qgis.org/debian](http://qgis.org/debian) xenial main # disabled on upgrade to wily disabled on upgrade to xenial
    55	deb [http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu](http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu) xenial main # disabled on upgrade to wily disabled on upgrade to xenial

In sources.list.d there are the following entries:

==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/google-earth.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-vivid.list <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) wily main # disabled on upgrade to wily
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) vivid main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-vivid.list.distUpgrade <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) wily main # disabled on upgrade to wily
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) vivid main


==> /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-vivid.list.save <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) wily main # disabled on upgrade to wily
deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) vivid main


Google Earth and qGIS are applications I've had installed since 15.04 at least, and they gave me no problems when I upgraded from 15.04 to 15.10.  I wouldn't have expected them to be problematic now?  Do they need to be removed?  I can understand how Google Earth might carry with it an "*account-plugin-google", *but I still don't see the connection to a facebook package.  I know I'm probably just slow, but I don't see the relationship between where the package errors came from and what my PPA's show.

---

### Post by llanitedave on 2016-05-23
> **grahammechanical said:**
> Ubuntu has a package manager. Its purpose is to keep a list of what packages are installed/removed/upgraded. Simply deleting a package (library) does not update the package manager's record. This is why we install & remove applications using the Software Centre (Store) or using the apt-get (apt) command line utility. 

How did you try to upgrade from 15.10 to 16.04? Did you use a command? Which one of these three possible causes of the inability to calculate the upgrade fits your situation?



I have seen examples of people using a certain command even though it will not upgrade 15.10 to 16.04 but will instead attempt to upgrade 15.10 to 16.10 development version. I wonder if you used this command.

```
do-release upgrade -d
```

It is the -d switch. It means development version. Ubuntu 16.04 is no longer a development version. The only Ubuntu development version available is 16.10.

Ubuntu is built on Debian. Here you can read about the package management tools that Ubuntu uses.

[https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

Regards
No, this came directly from the Ubuntu upgrade notifications.  The packages state 'xenial'.  I didn't even know I had an 'account-plugin-facebook' file until I got the error on the upgrade attempt, it's nothing I've ever knowingly installed, either from the Software Center or elsewhere.

---

### Post by Bashing-om on 2016-05-24
llanitedave; Hey !

Take a look at your sources again . You are on xenial .. however, there are sources for both wily and vivid .
The ones I have looked at I see no problem to upgrade them to that of xenial.

I have not got to Google yet .. be aware that Google has discontinued all 32 bit support . I do not know yet how this may apply in this situation.
For now ... fix :
[http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) wily main
deb-src [http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) vivid main
to xenial //

and then we will want to see the complete outputs of:
```

sudo apt update
sudo apt full-upgrade

```
Between code tags, please ! as that will promote readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]small things
[INDENT][INDENT][INDENT]in small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by llanitedave on 2016-05-25
> **Bashing-om said:**
> llanitedave; Hey !

Take a look at your soutces again . You are on xenial .. however, there are sources for both wily and vivid .
The ones I have looked at I see no problem to upgrade them to that of xenial.

I have not got to Google yet .. be aware that Google has discontinued all 32 bit support . I do not know yet how this may apply in this situation.
For now ... fix :
[http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) wily main
deb-src [http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) vivid main
to xenial //

and then we will want to see the complete outputs of:
```

sudo apt update
sudo apt full-upgrade

```
Between code tags, please ! as that will promote readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)[INDENT][INDENT]small things[INDENT][INDENT][INDENT]in small steps
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Two things happened since this post.  First, I went to sudo apt update, then sudo apt full-upgrade.  I restarted my computer, and the display server is now trashed.  I can only log in in TTY mode.  Fortunately, I have an older computer as a backup, which is running 14.04 with no issues.

Secondly, I saw an email from the development team about this issue which I'd reported as a bug.   Seems to be a duplicate of bug  [COLOR=#000000][FONT=Helvetica Neue]1565772.  Seems to be a conflict with KDE, which I've also got on my system.  Here's the relevant text:

[/FONT][/COLOR]> [COLOR=#000000][FONT=Helvetica Neue]("/usr/share/accounts/services/google-im.service" which is also in[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]"account-plugin-google")[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]It is important to say that the problem appears then configuring "kde-[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]config-telepathy-accounts" which is not contained in the above mentioned[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]PPA for xenial. This explains why it cannot be fixed.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Finally, I highly recommend that the Kubuntu quality testers should add the following extremely simple test case:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]- install ubuntu (standard, no changes)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]- sudo apt-get install kubuntu-desktop[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]The expected behavior is that one should get a system where the user can[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]select between unity and kde. In current Ubuntu 16.04, however, one gets[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]install conflicts. (In general, one should be able to install the meta-[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]packages of all flavors in parallel.)[/FONT][/COLOR]


I don't see any other solution but doing a clean install, and leaving out KDE.  I'll be doing that today.

---

### Post by Bashing-om on 2016-05-25
llanitedave; Ho Kay !

A nice clean fresh install for that warm feeling of security . Nothing to compare to it .
I too have seen lots of problems mixing Desktop Environments - even though a great deal of effort is expended to have them co-exit in parallel . I am not a proponent of multi DEs .

[INDENT][INDENT]that nuclear solution
[INDENT][INDENT]works everytime
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by yoshii on 2016-05-25
seeing stuff about facebook that you didnt initiate makes me think that you got hacked by someone or something.

---

### Post by bashiergui on 2016-05-25
> **yoshi2 said:**
> seeing stuff about facebook that you didnt initiate makes me think that you got hacked by someone or something.
account-plugin-facebook is part of the GNOME Control Center account plugin for single signon. And that's probably part of the base package. Highly unlikely to be a hack.

---

### Post by llanitedave on 2016-05-25
> **Bashing-om said:**
> llanitedave; Ho Kay !

A nice clean fresh install for that warm feeling of security . Nothing to compare to it .
I too have seen lots of problems mixing Desktop Environments - even though a great deal of effort is expended to have them co-exit in parallel . I am not a proponent of multi DEs .
[INDENT][INDENT]that nuclear solution[INDENT][INDENT]works everytime
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


It's time, I guess.  I used to be a big fan of Kubuntu, and kept looking for reasons to use it exclusively.  Problem is, Ubuntu keeps getting better and more elegant, and KDE continues to seem rather kludgy.  I do like the customizability, but even that has limitations compared with how I'd like to work.  So, I haven't used it much anyway.  I'm a glutton for punishment, though, I'm going to keep an eye on it and see if I can find an excuse to re-install it down the line.  So many of its applications are superior top the stock ones, but the DE just doesn't quite do it.

---

### Post by llanitedave on 2016-05-25
> **bashiergui said:**
> account-plugin-facebook is part of the GNOME Control Center account plugin for single signon. And that's probably part of the base package. Highly unlikely to be a hack.

Yeah, I'm pretty sure it's a compatibility bug with carrying KDE as a dual desktop.  We'll soon find out!

---

