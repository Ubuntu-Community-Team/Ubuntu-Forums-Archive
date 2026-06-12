---
title: "Heads up: Jaunty upgrades will be broken"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-02-27
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html)

Temporarily of course. :D

---

### Post by Nullack on 2009-02-27
Thanks

---

### Post by KhaaL on 2009-02-27
Argh, too late! will you announce once the change is complete here? 
PS. could this have caused my nvidia problem? ([http://ubuntuforums.org/showthread.php?t=1082091](http://ubuntuforums.org/showthread.php?t=1082091))

---

### Post by taavikko on 2009-02-27
> **KhaaL said:**
> Argh, too late! will you announce once the change is complete here? 
PS. could this have caused my nvidia problem? ([http://ubuntuforums.org/showthread.php?t=1082091](http://ubuntuforums.org/showthread.php?t=1082091))

Probably not, there were X.org update earlier today, If you retarted after that... It may rise from there the solution...

This issue that whiprush reported is pkg's concerning python and it's dependencies...

---

### Post by autocrosser on 2009-02-27
Already saw it & worked around it---Thanks for the heads up!!! I tend to stay wary of partial upgrades & don't install anything in that area until it looks good......

---

### Post by plun on 2009-02-27
> **whiprush said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html)

Temporarily of course. :D

Well... a little late...:lolflag:

Giant mess  ):P

---

### Post by rbmorse on 2009-02-27
Aw...not that bad. Except I lost my HP printers even with the work-around.

---

### Post by plun on 2009-02-27
> **rbmorse said:**
> Aw...not that bad. Except I lost my HP printers even with the work-around.

Well I have these.....

```
No apport report written because MaxReports is reached already
 
Errors were encountered while processing:
 python
 gedit
 gnome-orca
 hplip-data
 jockey-common
 jockey-gtk
 python-all
 python-dev
 python-all-dev
 python-launchpad-bugs
 rhythmbox
 totem-gstreamer
 totem-plugins
 totem
 totem-mozilla
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Also removed a bunch of packages, including update-manager...

No problem with apt and the terminal functional..

---

### Post by Kow on 2009-02-27
There is a reason you shouldn't partial upgrade a development set of repositories.... it will break unless you know for a fact a particular package is being removed. You know why I'm here? I noticed quite a few packages update-manager wanted to remove which shouldn't have been. I'm now happily upgraded with the PPA until the main build system can upgrade those packages itself.

---

### Post by taavikko on 2009-02-27
Good reminder indeed not to do partial upgrades, like never..
Just like Kow said.

Whenever apt wants to remove package, search what it is used for.
Or is it intended to be removed as obsolete pkg.


```
The following packages will be REMOVED:
  apturl blender foomatic-db-hpijs gimp gnome-app-install gnome-games hpijs
  hplip openoffice.org-emailmerge python-beagle python-launchpad-integration
  python-uno ubufox ubuntu-desktop
The following NEW packages will be installed:
  libpython2.6
The following packages will be upgraded:
  eog gdm gedit gedit-common gimp-data locales python python-minimal totem
  totem-common totem-dbg totem-gstreamer totem-mozilla totem-plugins
  update-manager update-manager-core
16 upgraded, 1 newly installed, 14 to remove and 0 not upgraded.
Need to get 20.1MB of archives.
After this operation, 49.9MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by plun on 2009-02-27
> **taavikko said:**
> Good reminder indeed not to do partial upgrades, like never..
Just like Kow said.



Well... you can choose a removal and see if its possible to rebuild...
In this case its broken....:^o

Still no problem if apt and the terminal works...):P   Just to wait and install ubuntu-desktop again.

(and backups if everything breaks)

---

### Post by vishalrao on 2009-02-27
thanks for the heads-up. now when do i know its safe to try an update? :D

edit: ok doko@ubuntu will post to ubuntu-devel-announce when main is stable again...

---

### Post by Kow on 2009-02-27
> **vishalrao said:**
> thanks for the heads-up. now when do i know its safe to try an update? :D

When it doesn't want to remove packages you should keep... like eog, gedit, etc. You can just use the PPA mentioned at the beginning of the thread. If they versioned the ppa packages correctly then you should automatically be updated to the official jaunty packages when they make it through the build system.

---

### Post by whoop on 2009-02-27
I do partial upgrades all the time :confused:. I only don't do a dist-upgrade when it wants to remove something critical. Can't remember I had problems with this.
Maybe I'm stupid, but my stupidity hasn't failed me yet:P

---

### Post by Vorian Grey on 2009-02-27
Thanks for the heads up. :)

---

### Post by MacUntu on 2009-02-27
Damn, have I missed the breakage?

---

### Post by plun on 2009-02-27
> **MacUntu said:**
> Damn, have I missed the breakage?

Yup.... a severe one, ongoing  :lolflag:

No all main functions works..

---

### Post by andrewabc on 2009-02-27
So, I'm installing alpha 5 now. So easiest/safest thing to do is wait a couple days before doing any updates for this all to sort out?
Also, I normally use mirrors that can be 12 hours behind, so does that mean I'd have to wait even longer to be on safeside?

---

### Post by BGFG on 2009-02-27
> **whiprush said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html)

Temporarily of course. :D

Too late for me too :) broke some things too, but switching my server from 'main' to 'united states' and reloading sorted it all out....

Thanks.

---

### Post by dBuster on 2009-02-27
> **Kow said:**
> When it doesn't want to remove packages you should keep... like eog, gedit, etc. You can just use the PPA mentioned at the beginning of the thread. If they versioned the ppa packages correctly then you should automatically be updated to the official jaunty packages when they make it through the build system.

Okay my updater is now telling me it will upgrade the eog and gedit.  Not removing them but upgrading them.  The following is what it is telling me:

REMOVE apturl
REMOVE bitpim
REMOVE bitpim-lib
REMOVE fusion-icon
REMOVE gnome-games
REMOVE openoffice.org-emailmerge
REMOVE python-apsw
REMOVE python-compizconfig
REMOVE python-uno
REMOVE python-wxgtk2.6
REMOVE ubufox

then it wants to install the new python 2.6

Other than that the rest is all upgrades.  

Any ideas?  Should I let it go?  I do not use compiz at this time and have a pretty plain configuration.  Is this a bigger jump in upgrades than when we went from Alpha 3 to Alpha 4???

---

### Post by RaZoR1394 on 2009-02-27
The latest updates broke sabnzbdsplus because of python conflict and I don't find any way of getting it back.

So stay off if you like sabnzbdplus from external repos.

---

### Post by jlacroix on 2009-02-27
Is Kubuntu effected too?

---

### Post by Vorian Grey on 2009-02-27
It still wants to remove Exaile, which happens to be my favorite player. I think I'll wait a bit longer to upgrade.

---

### Post by dBuster on 2009-02-27
ARGH~~~!!!

I just couldn't resist!  The update fixed my issue with screenlets not working or the screenlet manager not working however now I am being told that the broken package is of all things

ubuntu-desktop!!!

Go figure...

So adding this to the sources : deb [http://ppa.launchpad.net/pythoneers/ppa/ubuntu](http://ppa.launchpad.net/pythoneers/ppa/ubuntu) jaunty main

then trying to get the key is something that is still not working for me...  any ideas?  I downloaded the file from the link and yet no joy.

---

### Post by whoop on 2009-02-27
just did a dist-upgrade here. no breakage. So either its fixed or I have a "magic" install :-)

---

### Post by Mindless Automata on 2009-02-27
Is this what caused my kubuntu plasmoid desktop settings to suddenly reset to default...?

---

### Post by caryb on 2009-02-28
For me I'm on Vista temporarily:mad:


Cary

---

### Post by tawmas on 2009-02-28
I have added the pythoneers PPA to my sources, and that let me perform a clean dist-upgrade on my (i386) netbook, but not on my (amd64) desktop.

Don't know if this is to blame to the architecture, or to something messy in the status of my desktop. I surely do more experimentation on the latter.

---

### Post by Stochastic on 2009-02-28
Mmmmm, burnt ham.  Tasty.

I love half-cooked meat and half-cooked upgrades; both lead to exciting and precarious situations.

---

### Post by afv on 2009-02-28
> **dBuster said:**
> ARGH~~~!!!
[…]
So adding this to the sources : deb [http://ppa.launchpad.net/pythoneers/ppa/ubuntu](http://ppa.launchpad.net/pythoneers/ppa/ubuntu) jaunty main

then trying to get the key is something that is still not working for me...  any ideas?  I downloaded the file from the link and yet no joy.


To get the key:

```
gpg --keyserver keyserver.ubuntu.com --recv EE176F89 && gpg --export -a EE176F89 | sudo apt-key add -

```


I'm also getting problems...

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  anki avant-window-navigator awn-applets-c-core awn-applets-c-extras
  awn-applets-python-core awn-applets-python-extras awn-manager blender
  compizconfig-settings-manager exfalso fusion-icon music-applet python-awn
  python-awn-extras python-awnlib python-beaker python-cheetah
  python-compizconfig python-gpod python-ldb-samba4 python-matplotlib
  python-pygoocanvas python-pysqlite2 python-samba python-sqlite python-tdb
  python-webkitgtk python-xml revelation samba4 xbmc xbmc-common
  xbmc-skin-pm3-hd xbmc-web-pm3
The following NEW packages will be installed:
  python2.6-dev
The following packages will be upgraded:
  gimp hpijs hplip openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-officebean
  openoffice.org-report-builder-bin openoffice.org-style-andromeda
  openoffice.org-style-crystal openoffice.org-style-galaxy
  openoffice.org-style-hicontrast openoffice.org-style-human
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-writer python python-beagle python-dev python-minimal
  python-uno
33 upgraded, 1 newly installed, 34 to remove and 0 not upgraded.


---

### Post by Gina on 2009-02-28
> **caryb said:**
> For me I'm on Vista temporarily:mad:


CaryThat's a bit drastic isn't it?!  Haven't you got another version of Ubuntu?

---

### Post by DougieFresh4U on 2009-02-28
> **Gina said:**
> That's a bit drastic isn't it?!  Haven't you got another version of Ubuntu?

Funny, you are :P

---

### Post by meborc on 2009-02-28
you guys have no patience :D

i saw that 9 packages were to be removed and did not upgrade...

i waited for half a day, tried again, and everything was OK


PLEASE STOP WHINING ABOUT PARTIAL UPGRADE FAILURES

that is what happens when a lot of new packages are uploaded to the repositories... wait a few hours, try again... see if the number of upgraded/removed packages change... if it does then you know that uploading is taking place in the repo... sleep on it... then try again

like children a night before Christmas opening gifts ;)

---

### Post by Gina on 2009-02-28
Absolutely!!:lolflag:

---

### Post by dBuster on 2009-02-28
> **afv said:**
> To get the key:

```
gpg --keyserver keyserver.ubuntu.com --recv EE176F89 && gpg --export -a EE176F89 | sudo apt-key add -

```


So awesome, it worked!  I added the key and then ran the 
```

sudo apt-get update && sudo apt-get dist-upgrade
```

from root of course and it worked!  I upgraded and now I am not getting the stupid broken package error and the icon is gone telling me something is broken...  

Although it seems like I am missing some stuff such as the games and what not but what I mainly use is still here and intact!!!

---

### Post by KhaaL on 2009-02-28
> **tawmas said:**
> I have added the pythoneers PPA to my sources, and that let me perform a clean dist-upgrade on my (i386) netbook, but not on my (amd64) desktop.

Don't know if this is to blame to the architecture, or to something messy in the status of my desktop. I surely do more experimentation on the latter.

On a clean daily (28 feb) live cd install, i have the same problem also with amd64...

---

### Post by dentaku65 on 2009-02-28
> **meborc said:**
> you guys have no patience :D

i saw that 9 packages were to be removed and did not upgrade...

i waited for half a day, tried again, and everything was OK


PLEASE STOP WHINING ABOUT PARTIAL UPGRADE FAILURES

that is what happens when a lot of new packages are uploaded to the repositories... wait a few hours, try again... see if the number of upgraded/removed packages change... if it does then you know that uploading is taking place in the repo... sleep on it... then try again

like children a night before Christmas opening gifts ;)

I quote all.
With these upgrades the system is ok and mostly works quite well.
Just few packages are not yet ready compiz-settings and fusion-icon on my box at the moment.

:-)

---

### Post by Starks on 2009-02-28
Updates killed Deluge.

---

### Post by plun on 2009-02-28
This is my situation on **64 bit**

```
The following packages are BROKEN:
  python-launchpad-integration 
The following NEW packages will be installed:
  apturl{a} gnome-app-install gnome-games ubufox ubuntu-desktop 

```

Compiz running from GIT source...

---

### Post by nbubis on 2009-02-28
hmm..

apt still wants to remove "awn" and "exaile". any idea when they'll be available?

---

### Post by GARoss on 2009-02-28
I have both Ubuntu 8.10 & Kubuntu jaunty 9.04 partitioned & installed. Kubuntu 9.04 alpha 4 might be a mistake as I'm a newbie to Linux. So, I hope it's not too inappropriate to post here but I figure the systems are cousins. If it annoys anyone, please remove or ignore. 
I always boot to Ubuntu & then go to Kubuntu 9.04 to try different things. So, typically, when I boot Kubuntu 9.04 I get a message about a nepomukservicestub error but it works otherwise. Today, a window opens after the nepomukservicestub error that suggested updating python, python-minimal, libsmbclient, libgmp3cz, x11common, python-central, libwbclient0, libpulse0 & libxftz might correct the problem. While I was at it, I noticed there was a system update & added some new plasmas as well.
After update & rebooting I'm now having issues with Plamas. Weather plasma quit working & after opening *add widgets* it crashes! Then the desktop went black. I rebooted & removed a few plasmas that I had installed earlier, thinking that might help but crashed again! Not sure what to do next. As I was typing this the weather plasma began working!!! 
Reading this thread implies maybe the update is flauded but not sure how to troubleshoot the root cause.
One thing I did notice there are several versions of the same software installed. For example; Python 2.5, 2.6 & 3.0. 2.6 & 2.6 have the Ubuntu logo next to them. 
Could this cause a conflict?

---

### Post by isecore on 2009-02-28
I'm confused. Does this relate to people wanting to UPDATE their existing Jaunty installations, or does it relate to people wanting to UPGRADE to Jaunty?

Because I'm in the latter category, and I get a message about not being able to mark "ubuntu-desktop" for upgrade when I try to upgrade (I'm tired of Intrepid).

Some clarification please!

---

### Post by talkingwires on 2009-02-28
> **isecore said:**
> I'm confused. Does this relate to people wanting to UPDATE their existing Jaunty installations, or does it relate to people wanting to UPGRADE to Jaunty?Some clarification please!Both.

I upgraded without knowing about the Python situation until afterwards, and haven't had any problems. But I didn't just dist-upgrade and hope for the best; I checked apt first, saw that the new version of Python wanted to remove some apps, and upgraded everything but Python.

I still haven't let Python upgrade because a lot of apps from Universe haven't been updated.

---

### Post by kansasnoob on 2009-02-28
> **isecore said:**
> I'm confused. Does this relate to people wanting to UPDATE their existing Jaunty installations, or does it relate to people wanting to UPGRADE to Jaunty?

Because I'm in the latter category, and I get a message about not being able to mark "ubuntu-desktop" for upgrade when I try to upgrade (I'm tired of Intrepid).

Some clarification please!

Never expect things to go smoothly in an Alpha! Nor even in a Beta!

Breakage is normal during any Alpha stage!

Like my HP printer has not been supported by the repo version of hplip since Intrepid - still not in Jaunty - so I have to download and install the newest HPLIP:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

With the python updates it was lost so I tried to reinstall but it failed because python-devel was NOT there! So I installed "python2.6-dev" and "python-dev". Then HPLIP reinstalled my printer OK, but my CPU kept running at 90% even after restarting!

So I had to remove "python2.6-dev" and "python-dev" and restart! Now printer is still working and CPU is running normally, but these sort of things are to be expected during development!

My advice is be patient!

---

### Post by plun on 2009-02-28
> **nbubis said:**
> hmm..

apt still wants to remove "awn" and "exaile". any idea when they'll be available?

Both needs to be rebuild.

Exaile works OK from source-Bzr,  probably the same with AWN

Gnome-do/docky works OK as AWN replacement

---

### Post by darco on 2009-02-28
> **dBuster said:**
> So awesome, it worked!  I added the key and then ran the 
```

sudo apt-get update && sudo apt-get dist-upgrade
```

from root of course and it worked!  I upgraded and now I am not getting the stupid broken package error and the icon is gone telling me something is broken...  

Although it seems like I am missing some stuff such as the games and what not but what I mainly use is still here and intact!!!

I tried again this morning to upgrade but was still getting the partial upgrade,,follow above and all is great!!...

also not sure if this is new since I had auto login enabled but the login screen is sharp! Nice job!

darco

---

### Post by isecore on 2009-02-28
> **kansasnoob said:**
> Never expect things to go smoothly in an Alpha! Nor even in a Beta!

Breakage is normal during any Alpha stage!
Of course, I already know this. I'm not exactly new to Ubuntu (third year now) or Linux in general (First dip was in '95 or thereabouts) so I'm well aware what alphas and betas signify.

I was simply confused since some people talked about updating [an existing install] and others were talking about upgrading [an older install]. So I just asked to clarify things.

Now I know and I'll probably hold off upgrading my Intrepid box for a while.

---

### Post by tawmas on 2009-02-28
> **plun said:**
> This is my situation on **64 bit**

```
The following packages are BROKEN:
  python-launchpad-integration 
The following NEW packages will be installed:
  apturl{a} gnome-app-install gnome-games ubufox ubuntu-desktop 

```

Compiz running from GIT source...

Here it's even worse:

```
The following packages will be REMOVED:
apturl exfalso fontypython gnome-app-install gnome-games listen python-axiom python-coherence python-launchpad-integration python-pysqlite2 python-tagpy python-wxgtk2.6 python-wxversion quodlibet-plugins ubufox ubuntu-desktop
```

I know I just need to be patient... But I have a Gimp crasher that I cannot report because the package is not up to date, and I can't update it without borking the rest of the system... :-(

---

### Post by caryb on 2009-02-28
To answer my critics I have Vista on my Laptop only because it was there from new & I shrank it down to a 8G partition only to do the Lenovo bios updates. I had to install FF yesterday so I could get onto the forum :P I just couldn't bring myself to use Vista & IE my ego just couldn't handle that:lolflag:


Cary

---

### Post by Starks on 2009-02-28
Do these updates break the expected behavior of the volume control sliders and associated hotkeys?

---

### Post by rv65 on 2009-02-28
Having GPG key issues with the new repo. Hope the issue gets resolved.

---

### Post by caryb on 2009-03-01
Tis me on a "real" system again:P If I constantly use it & don't let the acpi or screensaver kick in I'm ok! If not I cant use the mouse or keyboard. When it breaks the only keyboard commands that work are ctl + alt + backspace or ctl + alt F1-6 & kill kdm


Cary

---

### Post by dBuster on 2009-03-01
> **rv65 said:**
> Having GPG key issues with the new repo. Hope the issue gets resolved.

Did you add the key with the following as was posted earlier in this thread?

> **afv said:**
> To get the key:

```
gpg --keyserver keyserver.ubuntu.com --recv EE176F89 && gpg --export -a EE176F89 | sudo apt-key add -

```

Then followed up by:

> **dBuster said:**
> So awesome, it worked!  I added the key and then ran the 
```

sudo apt-get update && sudo apt-get dist-upgrade
```

from root of course and it worked!  I upgraded and now I am not getting the stupid broken package error and the icon is gone telling me something is broken...  

Although it seems like I am missing some stuff such as the games and what not but what I mainly use is still here and intact!!!

Once I did that I had no problems and no broken packages either.  All of it done from a root terminal not just a regular terminal.  After it was done I rebooted and all is well.  Sure I do not have the games back nor the compiz icon for those settings, but I am running screen effects just can't change them for now.  Now crashes since doing normal work.  Did have an issue with nMap trying to get a new map of my network but I think I caused my own dns type attack on my network by doing so... not good...

---

### Post by ubername on 2009-03-01
Hi

I have a mission critical need for the games to come back, otherwise my business empire will collapse. Any clues when this will be?

(I have used the PPA tip even though my only problem appears to be lack of games, but it didn't fix it. I got errors trying to install ubuntu-desktop:
ubuntu-desktop:
 Depends: gnome-app-install but it is not going to be installed
 Recommends: gnome-games but it is not going to be installed
 Recommends: ubufox but it is not going to be installed)

---

### Post by plun on 2009-03-01
> **ubername said:**
> Hi

I have a mission critical need for the games to come back, otherwise my business empire will collapse. Any clues when this will be?



Well... those mission criticals are fixed for me...:lolflag:


I am using "main" as repo, maybe these fixes can take some time for a mirrored repo ?  You can change to main with Menu System > administration> software sources.

---

### Post by JohnJackson on 2009-03-01
It's all working for me now, too

---

### Post by KhaaL on 2009-03-01
> **plun said:**
> Well... those mission criticals are fixed for me...:lolflag:


I am using "main" as repo, maybe these fixes can take some time for a mirrored repo ?  You can change to main with Menu System > administration> software sources.

weird, you're using the main with or without the pythoneers repo? because it still want to remove AWN, ubufox and other packages... I'm on 64bit if it makes any diffrence.

---

### Post by JohnJackson on 2009-03-01
I'm using 64bit without the PPA, perhaps your update server isn't up to date yet

---

### Post by ace214 on 2009-03-01
Should we filing bugs for universe packages that need updating just to alert developers or is there some sort of list they have of packages that use python.

For me, the pythoneers PPA works fine. The only thing knocked out for me is QuodLibet and ExFalso.

---

### Post by taavikko on 2009-03-01
> **ace214 said:**
> Should we filing bugs for universe packages that need updating just to alert developers or is there some sort of list they have of packages that use python.


That's part of a reason there are MOTU's... 
I'm certain they are aware of any problems concerning python2.6 *bump.

While using main server my issues has been resolved. (64bit)
All-up-to-date once more.

---

### Post by dBuster on 2009-03-01
> **plun said:**
> Well... those mission criticals are fixed for me...:lolflag:


I am using "main" as repo, maybe these fixes can take some time for a mirrored repo ?  You can change to main with Menu System > administration> software sources.

You were able to get the games back??

---

### Post by DPic on 2009-03-01
So this update broke Deluge for me, but even though everything is fixed now, deluge is still borked. And yes, i tried deleting everything but my state folder, no dice. =/

---

### Post by BwackNinja on 2009-03-01
Currently waiting on:
miro
music-applet
python-gtkglext1
python-mmkeys
python-zsi
python-tagpy
python-xml

not really worried about the first 3, but the last 4 are stuff for Sonata

waiting...

---

### Post by plun on 2009-03-01
> **dBuster said:**
> You were able to get the games back??

Yup 

```
sudo apt-get update

sudo apt-get install ubuntu-desktop

and a check

sudo apt-get install gnome-games
```

---

### Post by bash on 2009-03-01
For me AWN is still broken. Anyone else got problems with as well? Packages depend on python-awn which is still want Python 2.5.

---

### Post by dBuster on 2009-03-01
> **plun said:**
> Yup 

```
sudo apt-get update

sudo apt-get install ubuntu-desktop

and a check

sudo apt-get install gnome-games
```

confirmed it worked!!!  Thanks

---

### Post by GARoss on 2009-03-01
> **jlacroix said:**
> Is Kubuntu effected too?
Yep! No mention on the Kubuntu forum. Searching got me here. Too late for me. I'm going to wait a few days for things to settle a bit before I try again.:(

---

### Post by ubername on 2009-03-01
> **dBuster said:**
> confirmed it worked!!!  Thanks
Thanks to plun

 I have my mission critical  games back. My empire survives. I wonder why synaptic didn't sort it?

---

### Post by lonniehenry on 2009-03-01
awn still affected by the breakage in mine.  Python breaking Awn-manager-trunk, avant-window-navagator-trunk, and python-awn-trunk.  Everything else updated.

---

### Post by caryb on 2009-03-01
Still effected on Kubuntu 64 


Cary

BTW installing ubuntu desktop is not an option:lolflag:

---

### Post by caryb on 2009-03-01
After thinking I was so smart with my last post I tried this to see if it worked

> root@stinkpad:~# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@stinkpad:~#



Cary

---

### Post by ronacc on 2009-03-01
> **DPic said:**
> So this update broke Deluge for me, but even though everything is fixed now, deluge is still borked. And yes, i tried deleting everything but my state folder, no dice. =/

go to the deluge site and grab the 1.1.3 source tarball and build it  , worked for me on amd64 after I installed python-setuptools and pyton-distutils-extra for dependency .

edit: I left my original .config/deluge intact and the local built deluge picked rightup where the repo one left off .

---

### Post by DPic on 2009-03-01
> **ronacc said:**
> go to the deluge site and grab the 1.1.3 source tarball and build it  , worked for me on amd64 after I installed python-setuptools and pyton-distutils-extra for dependency .

edit: I left my original .config/deluge intact and the local built deluge picked rightup where the repo one left off .

If i wait, an update to the repo should fix it though, right?

---

### Post by ronacc on 2009-03-02
eventualy

---

### Post by forteller on 2009-03-02
When are we supposed to remove the PPA?

---

### Post by bash on 2009-03-02
> **forteller said:**
> When are we supposed to remove the PPA?

AFAIK the PPA is just for packages from main. And I think that transition is more or less complete. At least if you are using the archive.ubuntu.com update servers you should get all the new packages as well. 

Sadly the same can't be said for programs from universe. They are neither covered by the PPA nor seem does like much updated versions have landed in the update servers yet.

---

### Post by LordVeovis on 2009-03-02
Other than running updates (which I did) is there any other way I could have had ubuntu-desktop removed?  When I ran the updates I had litterally just installed and it did not mention removing anything.  I was browsing forums for the reason why my Add / Remove Programs went away and I came across a post about enabling NTP and trying to auto update causing ubuntu-desktop to be removed.  This seems to be an old post, does thjis still happen?  I did try to update my time, so that may have removed without prompting; otherwise I NEVER update when it wants to remove packages.

EDIT: I have since been able to reinstall it, I am mainly just wondering if the NTP updating could have removed before I ran the update (since that was the order I did them in anyways).  I was prompted to install some packages by the NTP.  Not if I go back to the 'Time and Date' under System > Administration I cannot re-install NTP, it just acts like it installs then keeps it set to manual.  Upon changing to keep updated, I am prompted to install NTP again.

---

### Post by KhaaL on 2009-03-02
Updates has finally hit my repo, so now i'm all updated and shiny with the exception to AWN which i will have to live without for the time being.

---

### Post by Technoviking on 2009-03-02
Other than gwibber not installing most of my python issues have cleared up.

```
dbasinge@mikebuntu:~$ sudo apt-get install gwibber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gwibber: Depends: python-webkitgtk but it is not going to be installed
E: Broken packages
```

---

### Post by meborc on 2009-03-02
that and elisa...

---

### Post by GARoss on 2009-03-02
I'm still having trouble with Nvidia driver v180.35 but is it safe to install the other updates yet, namely Python?

---

### Post by LordVeovis on 2009-03-02
> **GARoss said:**
> I'm still having trouble with Nvidia driver v180.35 but is it safe to install the other updates yet, namely Python?

as long as it is not prompting you to remove any packages you should be safe.  This is of course also assuming you will not be trying to install python packages which have not been rebuilt yet as well.

---

### Post by tawmas on 2009-03-02
> **meborc said:**
> that and elisa...

... and exfalso...

---

### Post by hype on 2009-03-03
There are around 35 apps not yet compiled against new python; that's quite a lot.
 I tried to compile xchat, which is a package that needs to be removed at the moment by the upgrade, but it fails to build from source (2.8.6).

Is there a place on launchpad where we can tracks the changes added these not-yet upgradable apps? There must be bug reports somewhere. :D

---

### Post by DPic on 2009-03-04
Not only Deluge, but also PiTiVi is broken. Well, PiTiVi won't even install because of pygoocanvas which it depends on but can't be installed with this version of python. 

Such in inconvenience >,< oh well =]

Anyone have an estimate of how long this will last?

---

### Post by userdce on 2009-03-04
When I try to DIST-UPGRADE following message comes --with jaunty:
what to do 


252 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/214MB of archives.
After this operation, 6705kB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up python2.6-minimal (2.6.1-1ubuntu1) ...
update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.6-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by userdce on 2009-03-04
anybody please reply :(

---

### Post by thiebaude on 2009-03-04
I wish there was a workaround for bug # 304871, because i can't even install 9.04.

---

### Post by sovnarkom on 2009-03-04
Hi :(

how do you think, when theese packages will be fixed?
revelation
libapache2-mod-wsgi
python-awn

What do you think about manual installing using `dpkg -i --force-depends <...>`?

---

### Post by dBuster on 2009-03-04
> **thiebaude said:**
> I wish there was a workaround for bug # 304871, because i can't even install 9.04.

After reading through the launchpad bug you quoted in your post apparently there are some work arounds...  

Quoted from the bug report:
```
If you have had a chance to read the various things stated, there are
three workarounds:

- use the 2.6.27 kernel
- use the 2.6.28 kernel
- skip the upgrade to 9.04
```

Have you tried any of those work arounds?  Do you have a stable release other than Jaunty running right now?  Like 8.04 Hardy Heron?  

Are you trying to get Jaunty running because it is new?  And you have no other reason for trying it?  I had no choice as my new laptop would only boot the Alpha 2 of Jaunty so I have stuck with it since.  From reading that bug report it is a well known issue with the intel graphics chipset.

Just my 2 cents...

Oh and it is a high priority bug for the Jaunty release....

---

### Post by MacUntu on 2009-03-04
Are there any guides about what needs to be done to be able to install those "broken" packages (eg. rebuild process)?

---

### Post by pickscrape on 2009-03-05
For me the current problem is that it wants to remove revelation, without which I cannot access my passwords, so I'd rather not do that. :)

Am I reading it right? Is revelation the problem, or is it just a manifestation of some other issue? (I'm fairly new to apt.)

```

# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  kdeplasma-addons revelation
The following NEW packages will be installed:
  gnome-themes-selected libpackagekit-glib11 libpython2.6 libwxbase2.8-0 libwxgtk2.8-0 packagekit packagekit-backend-apt python-packagekit python2.6 python2.6-dev
  python2.6-minimal python3-minimal python3.0 python3.0-minimal
The following packages will be upgraded:
  blender boinc-manager eog evolution evolution-common evolution-plugins gedit gimp gnome-themes hpijs hpijs-ppds hplip kdeplasma-addons-data kpackagekit openoffice.org
  openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-filter-binfilter openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-kde openoffice.org-math openoffice.org-officebean openoffice.org-writer python python-beagle python-dev python-launchpad-integration
  python-minimal python-uno rhythmbox totem totem-gstreamer totem-mozilla totem-plugins update-manager update-manager-core vim vim-common vim-runtime xulrunner-1.9
  xulrunner-1.9-gnome-support xulrunner-1.9.1
47 upgraded, 14 newly installed, 2 to remove and 0 not upgraded.
Need to get 28.9MB/135MB of archives.
After this operation, 62.0MB of additional disk space will be used.

```

---

### Post by pressureman on 2009-03-06
Still waiting for libapache2-mod-wsgi and python-m2crypto :(

---

### Post by adult swim on 2009-03-07
i just updated and the only snag i ran into was it wouldnt go forward without python 2.6.  apt-get -f install sorted it out.

---

### Post by kilinu5889 on 2009-03-12
I am updating right now and i hope that there wont be any problems. (at least not for a while)

---

### Post by novafluxx on 2009-03-13
Alpha 6 came out on the 12th, so I'm willing to bet this release is pretty dern stable (compared to the previous alphas!)

---

### Post by PsychedelicReaction on 2009-03-13
still no Miro, I'm very sad :(

---

### Post by DougieFresh4U on 2009-03-13
> **PsychedelicReaction said:**
> still no Miro, I'm very sad :(

It's taking quite a long time to sort this 'python drama' out!

---

### Post by dBuster on 2009-03-13
> **PsychedelicReaction said:**
> still no Miro, I'm very sad :(

Have you tried to download the source tarballs to see if they would  work for you?

Have you tried to file a bug report with the Miro people?  [http://bugzilla.pculture.org/]("http://bugzilla.pculture.org/")

They even have their own repositories that you can install from.  Took a second to look through the ftp directories but didn't see a Jaunty however their source looks like it has a Jaunty tree so who knows...

I too would like to give Miro a spin once it is working....  Just not enough time to try at the moment.

---

### Post by PsychedelicReaction on 2009-03-13
> **dBuster said:**
> Have you tried to download the source tarballs to see if they would  work for you?

Have you tried to file a bug report with the Miro people?  [http://bugzilla.pculture.org/]("http://bugzilla.pculture.org/")

They even have their own repositories that you can install from.  Took a second to look through the ftp directories but didn't see a Jaunty however their source looks like it has a Jaunty tree so who knows...

I too would like to give Miro a spin once it is working....  Just not enough time to try at the moment.

i tried the sources but make ends with an error that my knowledge not able to understand about the fasttypes extension. when i got some spare time i will check out the svn branch.

there are a couple of open bugs about python 2.6 so i think they're aware of it...

---

### Post by dBuster on 2009-03-13
> **PsychedelicReaction said:**
> 
there are a couple of open bugs about python 2.6 so i think they're aware of it...

Were those bug reports about python or MIRO at their bug reporting area?  I think if they know there is an issue with python they may try to fix it on their end as well...  imho...

---

### Post by autocrosser on 2009-03-13
> **PsychedelicReaction said:**
> i tried the sources but make ends with an error that my knowledge not able to understand about the fasttypes extension. when i got some spare time i will check out the svn branch.

there are a couple of open bugs about python 2.6 so i think they're aware of it...

It's getting a good amount of attention: 
[https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029)

---

### Post by dBuster on 2009-03-14
> **autocrosser said:**
> It's getting a good amount of attention: 
[https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029)

Read that bug report.  Interesting.  I did notice though it makes mention of Miro 2.0.2 and on the download page it has a download for 2.0.3...  Are they past that release in which they thought would fix the issue?  Would be nice to give this a try...

---

### Post by andrewsomething on 2009-03-15
[https://lists.ubuntu.com/archives/ubuntu-motu/2009-March/005577.html](https://lists.ubuntu.com/archives/ubuntu-motu/2009-March/005577.html)

Transitioning miro (was: Re: Status of Python 2.6 transition)
Iain Lane laney at ubuntu.com
Sun Mar 15 02:09:41 GMT 2009

Luca Falavigna wrote:
> Fellow developers, interested contributors,
> 
> as you know, Jaunty will ship Python 2.6 by default. New version brought
> several changes in the structure of the Ubuntu Python stack, Matthias
> already summarised them very well [1].

Hello colleagues,

This is a related plea for help. I am trying to update Miro[0] for this
transition[1], but it is not as straightforward as it might otherwise be
 as the application is not compatible with python 2.6 and must be
restricted to working with 2.5 only.

I am trying to merge the Debian version and have applied a small patch
to version the interpreter used to /usr/bin/python2.5. Also required is
an additional build-dep on python2.5-dev as this is no longer pulled in
by libboost-python-dev and the build requires the headers. My current
debdiff is attached.

The problem I'm having is that the resulting deb is uninstallable due to
a python-support generated dependency (via ${python:Depends}) on python
(<< 2.6). It seems that python-support always insists that public
modules/extensions are made available for the "current" python version,
regardless of what pycompat/XS-Python-Version says (is this a bug?).

I guess the best current fix is to make the modules and extensions
private and have miro use them out of /usr/share/miro, as it seems that
these respect the requested versions. This is where I come unstuck
though; I cannot realise this. I've tried various patches to setup.py,
but to no avail, and I wonder if there is a better way.

Gentle reader, please assist me if you have the knowledge and time to
make this happen. IRC would be best for getting this done fast. Miro is
a popular application that we should endeavour to fix :).

Thanks for reading,
Iain

[0] [http://www.getmiro.com/](http://www.getmiro.com/)
[1] [https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029](https://bugs.launchpad.net/ubuntu/+source/miro/+bug/336029)

---

### Post by DougieFresh4U on 2009-03-16
Not trying to be a pain but I cannot install 'gnome' or 'serpentine' as there are dependency issues with 'python' Any heads up as to when we can expect something?
Thanks

---

### Post by scaine on 2009-03-16
I've just noticed that blueman 1.02 doesn't work either.  It installs, but then you get this when you try to run blueman-services :

```
scaine@Tosh:~$ blueman-services 
Loading configuration plugins
/usr/lib/python2.6/dist-packages/blueman/bluez/Manager.py:41: DeprecationWarning: object.__new__() takes no parameters
  cls._instance = super(Manager, cls).__new__(cls, *args, **kwargs)
Traceback (most recent call last):
  File "/usr/bin/blueman-services", line 167, in <module>
    BluemanServices()
  File "/usr/bin/blueman-services", line 31, in __init__
    adapter = self.Manager.GetAdapter()
  File "/usr/lib/python2.6/dist-packages/blueman/bluez/utils.py", line 28, in warp
    raise errors.parse_dbus_error(exception)
blueman.bluez.errors.DBusNoSuchAdapterError: No such adapter
```It's late, I'll try to log a bug about this tomorrow.  I installed from here, in case anyone is interested : 
[https://launchpad.net/~blueman/+archive/ppa]("https://launchpad.net/%7Eblueman/+archive/ppa")

[EDIT: Found a bug that *might* be relevant and added my comments.  [https://bugs.launchpad.net/blueman/+bug/317566]](https://bugs.launchpad.net/blueman/+bug/317566])

---

### Post by dBuster on 2009-03-17
What the happened with this mornings updates?!  Talk about a loss of the desktop!!!!  I updated from terminal window as the update manager was telling me broken packages and now I boot all the way to the desktop but I have no bars at the top or bottom!!! No menu, nothing!  Only the desktop items and I keep that clean so I am stuck to terminal TTY1....

Any ideas when or how to resolve??  Or is everyone else facing the same thing since it is so quiet here today?

I do know it went to kernel 2.6.2.28-10 this morning as well...  

I know this is a noob question but can you roll back an update???  I tried to boot into an earlier kernel and same results happened....

---

### Post by zika on 2009-03-17
> **dBuster said:**
> What the happened with this mornings updates?!  Talk about a loss of the desktop!!!!  I updated from terminal window as the update manager was telling me broken packages and now I boot all the way to the desktop but I have no bars at the top or bottom!!! No menu, nothing!  Only the desktop items and I keep that clean so I am stuck to terminal TTY1....
Any ideas when or how to resolve??  Or is everyone else facing the same thing since it is so quiet here today?
I do know it went to kernel 2.6.2.28-10 this morning as well...  
I know this is a noob question but can you roll back an update???  I tried to boot into an earlier kernel and same results happened....
it not so big a deal! I had the same scare this morning:[http://ubuntuforums.org/showthread.php?t=1098480](http://ubuntuforums.org/showthread.php?t=1098480). just install ubuntu-desktop. ...:)

---

### Post by scaine on 2009-03-17
Well, generally, if you see "Broken packages" or "Partial update", don't do it.  Same if it wants to remove anything (unless that's part of the over-all plan, which you can generally get a feel for by looking at the posts in this forum).

Check this page out before you update an Alpha to get an idea if it's safe to do so.

[https://launchpad.net/ubuntu/jaunty/+builds](https://launchpad.net/ubuntu/jaunty/+builds)

If there's a lot going on in "builds" (and it's for your architecture), then it's best to wait a bit before doing an upgrade.

Dunno how you could rollback, sorry.  You could just keep trying "sudo apt-get upgrade" to see how things progress.

Or, from your bare-bones desktop, try hitting ALT-F2 to bring up a run dialog and try "gnome-panel" or "gnome-terminal"...

---

### Post by kilinu5889 on 2009-03-19
> **scaine said:**
> Well, generally, if you see "Broken packages" or "Partial update", don't do it.  Same if it wants to remove anything (unless that's part of the over-all plan, which you can generally get a feel for by looking at the posts in this forum).

Check this page out before you update an Alpha to get an idea if it's safe to do so.

[https://launchpad.net/ubuntu/jaunty/+builds](https://launchpad.net/ubuntu/jaunty/+builds)

If there's a lot going on in "builds" (and it's for your architecture), then it's best to wait a bit before doing an upgrade.

Dunno how you could rollback, sorry.  You could just keep trying "sudo apt-get upgrade" to see how things progress.

Or, from your bare-bones desktop, try hitting ALT-F2 to bring up a run dialog and try "gnome-panel" or "gnome-terminal"...
It's a good thing I didn't update yet lol.

---

### Post by itismike on 2009-03-24
I wasn't so lucky.  It freezes about 1/6 of the way through the boot progress bar.  Can't switch to a terminal to see what is bugging out.  Even downloaded a fresh release of Ubuntu and Xububtu Jaunty Alpha 6, but they produce the same symptoms after 'update-manager -d'.  Guess I'll wait for beta.

---

### Post by thedarkbackward on 2009-04-03
Okay...so I'm pretty borked.

I had Intrepid on my PS3 running quite well and decided to get that promised wireless support with Jaunty. Did an upgrade through the old find and replace in the sources.list and all went well until the end of the install when I ran into this Python issue. As part of this, I lost my network connectivity (network-manager was uninstalled). 

I should be able to get the network up and running from the terminal with IFCONFIG, right? How do I fix this Python thing after that? Gawd...I feel like such a noob.

Thanks!

---

### Post by ktp on 2009-04-04
you should be able to do:

sudo apt-get update
sudo apt-get upgrade

---

### Post by zaphodbblx on 2009-04-04
whoops.....

---

