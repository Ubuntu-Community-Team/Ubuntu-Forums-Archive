---
title: "[SOLVED] Flash stopped working"
date: 2008-12-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-12-27
I had noticed a few days ago that flash quit working  on all my browsers, (opera, firefox, swiftweasel), but I was involved in another more serious problem to deal with it. When I look in synaptic, Flash plugin nonfree is installed. I tried Adobe flash and still no worky. Any tips or some other way to see whats up? I get the messege that says plugins missing when I open all browsers.
Thanks

---

### Post by ronacc on 2008-12-27
take a look at /usr/lib/mozilla/plugins some of the plugins may be links make sure they aren't broken , also is it all plugims or just flash ?

---

### Post by DougieFresh4U on 2008-12-27
> **ronacc said:**
> take a look at /usr/lib/mozilla/plugins some of the plugins may be links make sure they aren't broken , also is it all plugims or just flash ?

It's just flash.
I noticed when I opened 'Opera' that flash was working as I have a line on my home page that uses flash and it was working, but when I open Firefox or Swiftweasel, I get the missing plugin and then it says Adobe flash and I then click for it to install missing plugin but then it comes back with 'install manually'

---

### Post by ronacc on 2008-12-28
if you are 64bit try the 64bit flash see here
[http://ubuntuforums.org/showpost.php?p=6196594&postcount=451](http://ubuntuforums.org/showpost.php?p=6196594&postcount=451)

---

### Post by vishalrao on 2008-12-28
My flash isn't enabled either. But I don't remember if I had it installed in the first place before upgrading Intrepid to Jaunty.

I just did "sudo aptitude install flashplugin-nonfree" and it downladed the 64 bit version which works in FF now.

You could try "sudo aptitude **re**install flashplugin-nonfree"...

edit: changed apt-get to aptitude since i dont see reinstall option in apt-get

---

### Post by ronacc on 2008-12-28
I didn't realise that the ubuntu flash-nonfree had caught up to the 64bit version yet . you could also use synaptic , it has a reinstall option also.

---

### Post by cb34 on 2008-12-28
```

sudo updatedb && locate libflashplayer.so

```
remove any firefox libflashplayer.so files, without interfearing with the opera one, or maybe just see where the opera flash plugin file is linked to by clicking on it(after you've found it with the command above) and checking properties to see where it's linked to and then place a link to that flashplugin file from your $HOME/.mozilla/plugins dir.

just basically run the command above to first find any and all libflashplayer.so files, then gotta make it all work properly, because if opera runs flash content fine, then one of the things you can do is just link the opera's flashplugin file to firefox, or just move the flashplugin file to the firefox plugins dir, which there are a few...

but after you run the command above and find where the files are and if there are maybe doubles of some things, write back here and we can help you. because i realize what i wrote is confusing..lol :D

p.s. to make flash work, you dont need to use apt-get or the adobe message inside firefox.. or any adobe flash installer.. all u need is 1 file.. libflashplayer.so... you just put that file in the firefox or opera plugins directory. so just find the libflashplayer.so file/s, and place them in the right place and all will work. and make sure in firefox about[noparse]:p[/noparse]lugins you dont have more than 1 kind of flash player installed, like swfdec-mozilla etc. if so, use apt-get or synaptic and remove it.

---

### Post by taavikko on 2008-12-28
> **vishalrao said:**
> My flash isn't enabled either. But I don't 
You could try "sudo aptitude **re**install flashplugin-nonfree"...

edit: changed apt-get to aptitude since i dont see reinstall option in apt-get

sudo apt-get --reinstall install <package>

---

### Post by DougieFresh4U on 2008-12-30
> **cb34 said:**
> ```

sudo updatedb && locate libflashplayer.so

```
remove any firefox libflashplayer.so files, without interfearing with the opera one, or maybe just see where the opera flash plugin file is linked to by clicking on it(after you've found it with the command above) and checking properties to see where it's linked to and then place a link to that flashplugin file from your $HOME/.mozilla/plugins dir.

just basically run the command above to first find any and all libflashplayer.so files, then gotta make it all work properly, because if opera runs flash content fine, then one of the things you can do is just link the opera's flashplugin file to firefox, or just move the flashplugin file to the firefox plugins dir, which there are a few...

but after you run the command above and find where the files are and if there are maybe doubles of some things, write back here and we can help you. because i realize what i wrote is confusing..lol :D

p.s. to make flash work, you dont need to use apt-get or the adobe message inside firefox.. or any adobe flash installer.. all u need is 1 file.. libflashplayer.so... you just put that file in the firefox or opera plugins directory. so just find the libflashplayer.so file/s, and place them in the right place and all will work. and make sure in firefox about[noparse]:p[/noparse]lugins you dont have more than 1 kind of flash player installed, like swfdec-mozilla etc. if so, use apt-get or synaptic and remove it.

dougie@DougiesLeanMachine:~$ sudo updatedb && locate libflashplayer.so
[sudo] password for dougie: 
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
dougie@DougiesLeanMachine:~$

Does not even show Opera, but I assure you it works in Opera.

---

### Post by ronacc on 2008-12-30
Opera looks in /usr/lib/mozilla/plugins also for plugins and also any other /dir that you point it to with (opera) tools>preferences>advanced>content>plugin options

---

### Post by jfernyhough on 2008-12-30
Same thing just happened to me. Simple fix of purge and install flashplugin-nonfree.

:)

Though it's a little worrying why the file disappeared from /usr/lib/mozilla/plugins in the first place...

---

### Post by DougieFresh4U on 2008-12-30
> **jfernyhough said:**
> Same thing just happened to me. Simple fix of purge and install flashplugin-nonfree.

:)

Though it's a little worrying why the file disappeared from /usr/lib/mozilla/plugins in the first place...

Forgive my stupidity but what is the exact code for the purge you did?
Thanks, Dougie

---

### Post by ShirishAg75 on 2008-12-30
Dougie, 

 It would have been a simple 

```
$sudo aptitude purge flashplugin-nonfree
```

and then 

```
$sudo aptitude install flashplugin-nonfree
```

that is what he was trying to say. 

The purge would remove the old configuration files as well.

---

### Post by DougieFresh4U on 2008-12-30
> **ShirishAg75 said:**
> Dougie, 

 It would have been a simple 

```
$sudo aptitude purge flashplugin-nonfree
```

and then 

```
$sudo aptitude install flashplugin-nonfree
```

that is what he was trying to say. 

The purge would remove the old configuration files as well.
Thanks so much.
Still no flash after doing the purge and reinstall. Only Opera has working flash.

---

### Post by ShirishAg75 on 2008-12-30
Dougie, 
what other repos have you got. Can you attach or show your /etc/apt/sources.list

Dougie, also are you looking for only the closed source flashplugin-nonfree or also using or seeing the alternatives i.e. gnash and/or swfdec ?

---

### Post by DougieFresh4U on 2008-12-30
> **ShirishAg75 said:**
> Dougie, 
what other repos have you got. Can you attach or show your /etc/apt/sources.list

Dougie, also are you looking for only the closed source flashplugin-nonfree or also using or seeing the alternatives i.e. gnash and/or swfdec ?

Here you go, I just want plain ole flash and have not tried gnash or others:

```
deb http://packages.medibuntu.org/ jaunty free non-free

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse

deb http://ppa.launchpad.net/fta/ubuntu jaunty main
deb-src http://ppa.launchpad.net/fta/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe

deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
```

---

### Post by cb34 on 2008-12-30
> **DougieFresh4U said:**
> Thanks so much.
Still no flash after doing the purge and reinstall. Only Opera has working flash.if opera has flash, hunt down where it's getting it from.. flash is only 1 file

libflashplayer.so, or a link to that file.

like that file could exist in 1 place, then all browsers would link to that 1 file, and all would have flash from only one really having it..
its only 1 file.

so in terminal locate the libflashplayer.so file, and also any symlink files:
sudo updatedb && locate libflashplayer.so
see where opera is getting its flash plugin from.

copy the libflashplayer.so file to the ~/.mozilla/plugins directory, then find the file xpti,dat in the ~/.mozilla/firefox/profile.name directory and delete it so firefox re-read its plugins, that file will be recreated each time firefox is started.

flash is 1 file. put it in the plugins dir.
and if you dont have the libflashplayer.so file dont use the repo, download off adobes's site the .tar.gz file, unzip it, and move the 1 file to the ~/.mozilla/plugins dir, delete xpti.dat.. done. :D

and make sure firefox is not running in the background while doing this so in terminal:
killall -9 firefox
before you do anything.

peace.

---

### Post by DougieFresh4U on 2008-12-30
> **cb34 said:**
> if opera has flash, hunt down where it's getting it from.. flash is only 1 file

libflashplayer.so, or a link to that file.

like that file could exist in 1 place, then all browsers would link to that 1 file, and all would have flash from only one really having it..
its only 1 file.

so in terminal locate the libflashplayer.so file, and also any symlink files:
sudo updatedb && locate libflashplayer.so
see where opera is getting its flash plugin from.

copy the libflashplayer.so file to the ~/.mozilla/plugins directory, then find the file xpti,dat in the ~/.mozilla/firefox/profile.name directory and delete it so firefox re-read its plugins, that file will be recreated each time firefox is started.

flash is 1 file. put it in the plugins dir.
and if you dont have the libflashplayer.so file dont use the repo, download off adobes's site the .tar.gz file, unzip it, and move the 1 file to the ~/.mozilla/plugins dir, delete xpti.dat.. done. :D

and make sure firefox is not running in the background while doing this so in terminal:
killall -9 firefox
before you do anything.

peace.

Hello, and thanks for input. It started happening when  Firefox 3.1 came out
In post #9 of this thread I posted terminal output, and still not sure what to do. I am no 'guru' but trying to learn, again thanks for any help given!!:D

---

### Post by ronacc on 2008-12-30
you can find where Opera is getting flash by going to (in opera) tools>preferences>advanced>content>plugin options , it will tell you the path to each plugin just move the  libflashplayer.so to /usr/lib/mozilla/plugins most browsers look there for plugins . you'll need to use sudo to move it .

---

### Post by DougieFresh4U on 2008-12-30
Here is what is in lib/mozilla/plugins

```
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/mozilla/plugins/libtotem-basic-plugin.so
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so
/usr/lib/mozilla/plugins/mozplugger.so
/usr/lib/mozilla/plugins/nppdf.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.nppdf.so
```

And here is Opera content/plugins

---

### Post by cb34 on 2008-12-30
deleted post
--------

you know what.. if you wanna just start fresh and nuke anything to do with flash, i can get everything working for u quick i'm sure of it. when you play around trying to fix a problem to long and make too many tweaks and attempts, it makes things much harder and is easier to start fresh.

---

### Post by DougieFresh4U on 2008-12-30
> **cb34 said:**
> deleted post
--------

you know what.. if you wanna just start fresh and nuke anything to do with flash, i can get everything working for u quick i'm sure of it. when you play around trying to fix a problem to long and make too many tweaks and attempts, it makes things much harder and is easier to start fresh.

Excellent Idea, please help
Thanks, Dougie

---

### Post by cb34 on 2008-12-31
sorry.. i went out and now im eating man.. typing with greasy hands..:D but i didn't wanna leave you hanging since i said i'd help.. so gimme 10 and ill be back and ill edit this post. :D
-----
close all instances of firefox and opera and even check in gnome-system-monitor that there really isn't any firefox or opera's running and/or:
killall -9 firefox
killall -9 opera

ok..
first remove any flash packages you may have installed through synaptic/apt-get
```

sudo apt-get purge adobe-flashplugin flashplugin-nonfree*

```
then still in the terminal erase all instances of libflashplayer.so and anything npwrapper.
after running "sudo updatedb && locate libflashplayer.so" use each of those lines and add the rm(remove) command before each line and delete them all one by one. here you go:
```

sudo rm /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/flashplugin-nonfree/libflashplayer.so
sudo rm /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so

```
dont worry if it says file doesn't exist, cuz when you first ran "apt-get purge", it might have already deleted some of the flash stuff.
(example: /usr/lib/flashplugin-nonfree should no longer exist since you ran purge flashplugin-nonfree beforehand)

then go to:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download the .tar.gz from the drop down list, not the .deb

that .tar.gz has 1 file in it, libflashplayer.so (actually 2, but you only need the .so file, the other script file is not needed.)
extract libflashplayer.so to ~/.mozilla/plugins (if plugins directory doesn't exist, create it.)
then delete the xpti.dat file so when you start firefox next time it will re-read the plugins directory. xpti.dat file will be recreated which is what it's suppose to do.
it is located in ~/.mozilla/firefox/profile.name
profile.name will be some weird numbers/digits, it is unique to you and your profile.. delete xpti.dat from in there.
then start firefox and check if it works.

and next time you open opera, go into the plugin settings of opera and point it to the ~/.mozilla/plugins directory, and opera should also have flash working from that same libflashplayer.so file.

lemme know. :D

---

### Post by DougieFresh4U on 2009-01-01
> **cb34 said:**
> 

lemme know. :D

I went through your whole thing and still no flash. Only Opera has flash. 
Thanks for your help. I am gonna try it again.

---

### Post by DougieFresh4U on 2009-01-04
Ok, I printed out the all the codes provided and did ALL

```
dougie@DougiesLeanMachine:~$ sudo apt-get purge adobe-flashplugin-nonfree*
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package adobe-flashplugin-nonfree*
dougie@DougiesLeanMachine:~$ sudo rm /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/firefox/plugins/npwrapper.libflashplayer.so': No such file or directory
dougie@DougiesLeanMachine:~$ sudo rm /usr/lib/flashplugin-nonfree/libflashplayer.so
rm: cannot remove `/usr/lib/flashplugin-nonfree/libflashplayer.so': No such file or directory
dougie@DougiesLeanMachine:~$ sudo rm /usr/lib/swiftweasel/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/swiftweasel/plugins/npwrapper.libflashplayer.so': No such file or directory
dougie@DougiesLeanMachine:~$ sudo rm /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so': No such file or directory
dougie@DougiesLeanMachine:~$ sudo rm /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
rm: cannot remove `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': No such file or directory
dougie@DougiesLeanMachine:~$ 
```

So now I am ready to download the .tar file. I am horrible at installing .tar files. Have never been able to do one on my own, so can some one please walk me through getting this flash installed, please?

---

### Post by tad1073 on 2009-01-04
It is working sporaticlly for me also.

Didn't read post title. 

I am not using JJ but am having some flash problem with Fx.

I cleared my history and that solved the problem, on Best Buys wesite anyway.

---

### Post by DougieFresh4U on 2009-01-04
> **tad1073 said:**
> It is working [COLOR=#cc0000][/COLOR]sporaticlly for me also.

It was working in Opera only for a while but now I have NO flash at all

---

### Post by jfernyhough on 2009-01-04
(I've only read parts of the thread so don't shout if these have been covered already ;P )

* What does about:plugins report in Firefox?
* What is in ~/.mozilla/plugins/ ? (IIRC this is only needed for a local copy of Firefox, e.g. I have Shiretoko in ~/bin/Firefox/, so two copies/versions could be conflicting or a symlink could be dangling)
* Have you deleted ~/.mozilla/firefox/{PROFILE}.default/pluginreg.dat and then run Firefox (replacing {PROFILE} with your actual profile)?

Combine these:
Delete (or move) ~/.mozilla/plugins/
$sudo aptitude purge flashplugin-nonfree
$sudo aptitude purge adobe-flashplugin
Delete ~/.mozilla/firefox/{PROFILE}.default/pluginreg.dat
$sudo aptitude install flashplugin-nonfree

Or:
Create a directory ~/.mozilla/plugins/
Symlink to the content of /usr/lib/mozilla/plugins/ (easy in Nautilus - select all in one window, Ctrl-Shift-Drag to other)

---

### Post by DougieFresh4U on 2009-01-04
YIKES!! Went to remove/purge flashplugin-nonfree and it wanted to remove 34 packages. Whats up with that and should these be removed?
```
dougie@DougiesLeanMachine:~$ sudo aptitude purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  arj{u} cheese{u} desktop-base{u} flashplugin-nonfree{p} gdm-themes{u} 
  gnome-core{u} gnome-games-extra-data{u} gnome-network-admin{u} 
  gnome-office{u} gnome-themes-extras{u} gnome-vfs-obexftp{u} 
  gnome-volume-manager{u} gnumeric{u} gnumeric-common{u} gparted{u} 
  gthumb{u} gthumb-data{u} hardinfo{u} inkscape{u} libmagick++10{u} 
  libsoup2.2-8{u} libwmf-bin{u} liferea{u} menu-xdg{u} p7zip{u} 
  perlmagick{u} planner{u} python-4suite-doc{u} python-4suite-xml{u} 
  python-lxml{u} python-reportlab{u} python-uniconvertor{u} serpentine{u} 
  sound-juicer{u} 
0 packages upgraded, 0 newly installed, 34 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 185MB will be freed.
Do you want to continue? [Y/n/?] 

```

EDIT: Don't know what I did, but flash seems to be working  all around now, go figure

---

### Post by tad1073 on 2009-01-04
> **DougieFresh4U said:**
> YIKES!! Went to remove/purge flashplugin-nonfree and it wanted to remove 34 packages. Whats up with that and should these be removed?
```
dougie@DougiesLeanMachine:~$ sudo aptitude purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  arj{u} cheese{u} desktop-base{u} flashplugin-nonfree{p} gdm-themes{u} 
  gnome-core{u} gnome-games-extra-data{u} gnome-network-admin{u} 
  gnome-office{u} gnome-themes-extras{u} gnome-vfs-obexftp{u} 
  gnome-volume-manager{u} gnumeric{u} gnumeric-common{u} gparted{u} 
  gthumb{u} gthumb-data{u} hardinfo{u} inkscape{u} libmagick++10{u} 
  libsoup2.2-8{u} libwmf-bin{u} liferea{u} menu-xdg{u} p7zip{u} 
  perlmagick{u} planner{u} python-4suite-doc{u} python-4suite-xml{u} 
  python-lxml{u} python-reportlab{u} python-uniconvertor{u} serpentine{u} 
  sound-juicer{u} 
0 packages upgraded, 0 newly installed, 34 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 185MB will be freed.
Do you want to continue? [Y/n/?] 

```EDIT: Don't know what I did, but flash seems to be working  all around now, go figure

try:
```
whereis flashplugin non-free
```

then got to the corresponding folders and remove them manually, or rm it

---

