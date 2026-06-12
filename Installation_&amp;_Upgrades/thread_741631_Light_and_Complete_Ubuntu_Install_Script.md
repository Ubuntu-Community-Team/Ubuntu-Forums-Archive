---
title: "Light and Complete Ubuntu Install Script"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by Stroganoff on 2008-03-31
Hi,

dissappointed with Xubuntu performance on my old laptop, dissatisfied with Fluxbuntus usability and lack of language support and being aware of all the downsides every other distribution has compared to Ubuntu, I decided to create my own lightweight Ubuntu Desktop sort of from scratch - this scratch being the "command-line system" installation mode of the Alternate ISO.

My Desktop is based on lightweight WM and Panel and selected components of XFCE. In contrast to most lightweight distros (Puppy *cough*) out there, this Desktop is aimed at being good looking and being usable by beginners and experts alike.
This is done using a rather long install script which installs packages and applies some tweaks. Most actions of the script are configurable in the first part of it.

The script is intended ONLY to run on a fresh and clean command-line installation.

So here it is, ready for public testing. I developed it in Vmware-Server and tested it on two Laptops, both were running fine.
Let's see how this developes. Don't install this on your mother's yet. (wait for the next release ;) )


**README:**
[http://tomfichtner.de/linux/](http://tomfichtner.de/linux/)

**Download:**
[http://www.tomfichtner.de/linux/ubuntu-light-script.tar.gz](http://www.tomfichtner.de/linux/ubuntu-light-script.tar.gz)

**Contact:**
IRC: [#minimalubuntu](irc://irc.freenode.org/minimalubuntu) on Freenode
Jabber: [email]stroganoff@jabber.systemli.org[/email]


This is from VMWare Server with 192 MB RAM, running with desktop icons and all optional services (SSHD, Samba, CUPS, VNC):
```
user@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           186        176         10          0          8        120
-/+ buffers/cache:         47        139
Swap:          690          0        690
```

Without OpenOffice and GIMP roughly 2GB of disk space are consumed.


**Screenshots (with german locale):**

[[img]http://www.abload.de/img/ubuntu-light-script-usd.png[/img]](http://www.abload.de/img/ubuntu-light-script-n31.png)

[[img]http://www.abload.de/thumb/ubuntu-light-menu2zuu.png[/img]](http://www.abload.de/img/ubuntu-light-menu2zuu.png)

[[img]http://www.abload.de/thumb/ubuntu-light-menu3x6j.png[/img]](http://www.abload.de/img/ubuntu-light-menu3x6j.png)

[[img]http://www.abload.de/thumb/ubuntu-light-script-13m.png[/img]](http://www.abload.de/img/ubuntu-light-script-13m.png)

This is without: desktop icons, samba, cups, syslog, klog, VNC and Fuse. Only SSH, XFE, Kaze and XDM are running. Without Kazehakase it boots up to roughly 25-31MB memory consumption.

Here some screenshots with Fluxbox, Openbox and sharp fonts:

[[img]http://www.abload.de/thumb/fluxbox-fbpanel-roxf2u.png[/img]](http://www.abload.de/img/fluxbox-fbpanel-roxf2u.png)

[[img]http://www.abload.de/thumb/openbox-pcmanfm-fbpavc1.png[/img]](http://www.abload.de/img/openbox-pcmanfm-fbpavc1.png)


**Features:**

[list][*] ["IceBuntu" IceWM theme](http://freshmeat.net/projects/icebuntu/), "Mist" GTK2+ theme and Tango Icon set
[*] choose window manager: IceWM, Openbox, Fluxbox, E16
[*] choose panel: FBPanel, XFCE4-Panel, LXPanel
[*] choose desktop: XFDesktop, FBDesk, ROX, PCManFm
[*] option to integrate [sharp fonts](http://sharpfonts.com) in all programs, crisp and clean.
[*] sophisticated hotkey scheme using the SUPER key (a.k.a. WINKEY)
[*] Some tweaks to IceWM behaviour (Menu mouse tracking, ALT+TAB layout)
[*] Thunar (file manager): Automount, Samba Browsing and custom context
  menu icons: Archive-Management, Music play and enqueue, Image convers-
  ion and lossless JPEG rotation
[*] double click on clock reveals a small Calendar
[*] double click on CPU meter opens up the Task Manager
[*] Audacious is paused on hibernate (so it won't crash if playing a live 
  stream)
[*] Pidgin logs out of the respective networks on hibernate
[*] Pidgin comes with some preference changes
[*] Firefox extensions: Adblock Plus, Linkification, CustomizeGoogle
[*] installs Opera weekly (alpha) to get current flash plugin working
[*] Opera comes with an ad blocking urlfilter.ini
[*] Menu item included to regenerate the IceWM Menu using [MenuMaker](http://menumaker.sourceforge.net/)
[*] Menu item included to restart FuseSMB in order to refresh Samba shares
[*] aMule comes with a quite fresh server.met
[*] preset Download directories for aMule and Transmission (BitTorrent)
[*] xscreensaver's fade-to-black is set up for smooth 60fps
[*] X.org's ugly black-white pattern on startup is eradicated both with
  XDM (login manager) and startx
[*] a [nice theme](http://themes.freshmeat.net/projects/cubicalx/) for XDM (slightly tweaked)[/list]

The following features are optional:

[list][*] Autologin without Login Manager
[*] Lock Screen on Hibernate
[*] Shutdown, Reboot and Hibernate without entering a password
[*] Hibernate on Logout and Power Button
[*] Browse samba shares with Thunar (using FuseSMB)
[*] Choose one of the 10 included Application Menu buttons
[*] Laptop closing without going to Standby
[*] PC-Speaker is disabled[/list]



**Please report back with feedback!**
What's missing, what's bloated? What's good, what's bad? How much RAM is consumed on your machine?


By the way, Ubuntu on 64MB RAM might be kind of endangered. Please try and confirm these two Ubuntu bugs:

[176562: Config fails in low memory machine (64MB)](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/176562)
[202959: [hardy] generating locales stalls on 64mb ram](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

---

### Post by wPwLUi3N on 2008-04-02
Looking good!!!

---

### Post by Stroganoff on 2008-04-02
Glad to hear that.

---

### Post by notwen on 2008-04-02
This looks very promising.  I'll be sure to try it out when I get more time on my tinker box.  I bet aysiu will find your project interesting.  Best of luck w/ future releases.  =]

---

### Post by heartburnkid on 2008-04-02
Looks very nice.  I might give it a try with a low-end system I'm building...

Ever think about bundling this together as a distro?  I wonder if Ubuntu Lite is taken...

---

### Post by Stroganoff on 2008-04-02
> **heartburnkid said:**
> Ever think about bundling this together as a distro?  I wonder if Ubuntu Lite is taken...

That's the ultimate goal.

---

### Post by notwen on 2008-04-02
You may wish to show your current progress to the guys over on this [thread]("http://ubuntuforums.org/showthread.php?t=684890") who were working on making a Icebuntu distro.  I'm not certain how they feel w/ the mixing in of some XFCE, but it's worth a shot.  =]

---

### Post by Stroganoff on 2008-04-05
Thanks for the hint, I'm staying in contact with those guys. Albeit I have to go my own (rather unorthodoxe) way for now.

Coming up....

[img]http://www.abload.de/img/ubuntu-light-menufzy.png[/img]

..and more.
"It's sink or swim." --- not anymore!

---

### Post by myusername on 2008-04-05
looks very nice ill have to try it sometime

---

### Post by smartboyathome on 2008-04-05
Perhaps you can try LXDE in place of IceWM? :)

---

### Post by madjr on 2008-04-06
grrr, how i add this thread as favorite for future reference ! :confused:

great work!

---

### Post by koenn on 2008-04-06
> **Stroganoff said:**
> 
**Please report back with feedback!**
What's missing, what's bloated? What's good, what's bad? How much RAM is consumed on your machine?


Cool.
I've done similar things before (i..; install a base cli system, then add software and custom config to it, usually scripted) but your script is more elaborate than mines ever were, so in the future I'll probably use yours in some form ((it's public domain, right ? I don't remember seeing any mention of a license)

I noticed in your TODO list that you would like to make a deb out of it. That's a very convenient way to put custom/additional config files in place but you'll probably have problems with the apt-get install section of your script, because : 
1/ you can't run 2 instances of apt simultanously, so you can not have  "apt-get install $PACKAGES" from within an "apt-get install ubuntu_light_deluxe". 

2/ you can solve 1/ by listing those packages as (pre-) dependencies, but then you couldn't do those neat 
 `[ "package"="yes" ] && package` -tricks to build a list of packages matching user choices. 

I'm sure there are a few ways around this, but they'll all be trade-offs. I'd be interested to see which way you go.

---

### Post by Stroganoff on 2008-04-06
New version (Beta 4) out now. Sporting easy to use menus (instead of the old configuration file) for package selection, default applications, extra packages and system-wide settings. XFE (very lightweight file manager, but not freedesktop.org compliant) is now also selectable, among other things.
Also some custom IceWM menu entries for starting/stopping/restarting Samba, SSH, CUPS and FuseSMB.

Also I have included slim instead of xdm because the latter is [currently broken](https://bugs.launchpad.net/ubuntu/+source/xdm/+bug/210830) in hardy. (Of course you can use xdm or even gdm nonetheless, that's what user-driven installation menus are there for)

Slim needs a nice (light) theme and a menu for games selection would be nice, too. I will work on that in the next few days.

Complete changelog? Maybe next time. :D

Test and/or enjoy, please!


**README:**
[http://www.tomfichtner.de/linux/](http://www.tomfichtner.de/linux/)

**Download:**
[http://www.tomfichtner.de/linux/ubuntu-light-script.tar.gz](http://www.tomfichtner.de/linux/ubuntu-light-script.tar.gz)


New screenshots: 

[[img]http://www.abload.de/thumb/ubuntu-light-menu2zuu.png[/img]](http://www.abload.de/img/ubuntu-light-menu2zuu.png)

[[img]http://www.abload.de/thumb/ubuntu-light-menu3x6j.png[/img]](http://www.abload.de/img/ubuntu-light-menu3x6j.png)

[[img]http://www.abload.de/thumb/ubuntu-light-script-13m.png[/img]](http://www.abload.de/img/ubuntu-light-script-13m.png)

This is without: desktop icons, samba, cups, syslog, klog, VNC and Fuse. Only SSH, XFE, Kaze and XDM are running. Without Kazehakase it boots up to roughly 25-31MB memory consumption.


> **koenn said:**
> it's public domain, right ? I don't remember seeing any mention of a license
Yes it is, see LICENSE.TXT. I might change this to GPL as soon as everything's done.

> **koenn said:**
> I noticed in your TODO list that you would like to make a deb out of it. That's a very convenient way to put custom/additional config files in place but you'll probably have problems with the apt-get install section of your script [...]

I'm aware of the problems. Using .debs would require a wholly different approach. It's not really on the agenda for now. :D

> **smartboyathome said:**
> Perhaps you can try LXDE in place of IceWM? :)
I'll look into it, as soon as it's in the official repos.

---

### Post by Stroganoff on 2008-04-08
Update & Bump.
Included ROX (with some MIME-Types of course), TOR, Wifi-Radar and Scanner Support.

One guy is using my script on his eeePC: 1.2GB used + swap.
"it boots up fine and gives a good desktop"

---

### Post by testecletes on 2008-04-13
I'm loving it man, thanks for all your help. This was probably the best and easiest script I've used to make a brick of a computer fly when all the other distros failed me. Puppy is quick, but your IceWM Ubuntu install script helps my friend's old P3-800mhz, 256mb fly.


-Edit-
I'm wondering if there is a way to put a shutdown menu, or configure a shutdown menu when the power button is pressed. I have been using terminal to sudo reboot or sudo halt. Thanks again.

---

### Post by Stroganoff on 2008-04-14
> **testecletes said:**
> I'm loving it man, thanks for all your help. This was probably the best and easiest script I've used to make a brick of a computer fly when all the other distros failed me. Puppy is quick, but your IceWM Ubuntu install script helps my friend's old P3-800mhz, 256mb fly.

**Mission accomplished!** :D

**New version out now. Gogogo!**
Updates:
- option to mount disks with "noatime"
- option to mount disks with "data=writeback"
- option to change [swappiness](http://www.linode.com/wiki/index.php/Swappiness)
- tweaks for Solid State Disks (tmpfs)
- [tweaks and kernel modules](http://ubuntu-eee.tuxfamily.org/index.php5?title=How_to_use_the_ubuntu-eee_script) for EEE PC
- added gtk-theme-switcher, acroread, gnome-app-install (all optional)
- many minor fixes and additions


> **testecletes said:**
> I'm wondering if there is a way to put a shutdown menu, or configure a shutdown menu when the power button is pressed. I have been using terminal to sudo reboot or sudo halt. Thanks again.

I've quickly created this shutdown dialog and integrated it into the last update:
[img]http://www.abload.de/img/logout7w2.png[/img]

to install it manually (after installing an old version of my script):

extract shutdown/shutdown-dialog.sh from my new script pack

```
sudo apt-get install gtkdialog
chmod +x shutdown-dialog.sh
sudo cp shutdown-dialog.sh /usr/local/bin
```

change .icewm/preferences:
```
ConfirmLogout=0
LogoutCommand="shutdown-dialog.sh"
```

This way the "logout" button of icewm shows the shutdown dialog. Showing the dialog on PowerButton is somewhat tricky, havn't figured it out yet.

---

### Post by larsemil on 2008-04-15
2GB feels like quite alot. I ended up - with full gnome - on ca 2.5GB with open office and gimp + everything needed for compiling etc and a couple of other programs. 
also i am running on a rather small amount of memory as well most of the time with peaks over 200mb very very rarely. 

So for me to change from my full gnome-desktop on my eee - to this lightweight one is not happening now.

Also i need compiz(also in those 2.5gb), dont know how thats working with icewm.

---

### Post by Stroganoff on 2008-04-15
> **larsemil said:**
> 2GB feels like quite alot. I ended up - with full gnome - on ca 2.5GB with open office and gimp + everything needed for compiling etc and a couple of other programs. 

Just FYI: those 2GB were rather estimated.

With a cleared apt-cache I'm now on 1,98GB with GIMP, Openoffice, Acroread, Evince, mtPaint, Build-Essential, Mplayer, VLC, win32codecs, libdvdcss, Sound Converter, RipperX, Claws-Mail, Firefox, Swiftfox, Pidgin, Sun Java, XChat, Wifi-Radar, ndiswrapper, Network Manager, Abiword, Gnumeric, WINE, Thunar, CUPS, Galculator, Gshutdown, Xarchiver (+rar/zip), Samba, FuseSMB, FuseISO, Mousepad, Imagemagick, Audacious (+flac etc.), Catfish, Boot-Up Manager, Icon- and GTK-Themes and various of XFCE/Gnome control panels and minor things.

There are no optimizations whatsoever regarding disk space (same goes for the official flavors) because it's quite undoable without breaking (meta-)packages. One thing is for sure: it doesn't use *more* disk space than Gnome.

> Also i need compiz(also in those 2.5gb), dont know how thats working with icewm.

I'm yet to find that out for I have no adequate hardware. The IceWM taskbar (panel) hasn't got its own binary so I suppose I'll have to replace it with xfce4-panel or [LXPanel](http://www.gnomefiles.org/app.php/LXPanel) for running with Compiz. I will look into that.

---

### Post by marquee moon on 2008-04-17
Strogonoff, 

when I 

tar -xf ubuntu-light-script.tar.gz

I get told that the file is not a tar archive, so cannot be un-zipped. I tried un-archiving the file in my existing ubuntu install &  a message came up telling me that I couldnt un-archive the tar becuase it contained .HTML files and therefore may be a risk to my system. 

Do you have any suggestions?

---

### Post by Stroganoff on 2008-04-17
Yesterday the script was offline for some hours, instead of the script you downloaded the 404-HTML-file, disguised with a misleading filename.
Just redo step 3 in the readme (download and extract).

---

### Post by shae on 2008-04-19
Would you like to join the Ubuntulite dev team?
[Ubuntulite]("ubuntulite.tuxfamily.org")

Shae Smittle
Ubuntulite Project Manager

---

### Post by john_spiral on 2008-04-19
[SIZE="5"]Good work!!![/SIZE]

Your work will go a long way to saving lots of computers from the landfill. 

Would it not be better to publish it under a GPL like license?

You have the below copyright notice in the readme.txt file:

"Copyright Notice
================


 Author: Tom Fichtner (2008)
 http://www.tomfichtner.de/linux/"

I'm sure you will get a lot more commitment from the Ubuntu community if they knew their efforts were protected by the same license as Ubuntu i.e GPL?

John

---

### Post by Stroganoff on 2008-04-26
> **john_spiral said:**
> Your work will go a long way to saving lots of computers from the landfill.
I certainly hope so.

> **john_spiral said:**
> Would it not be better to publish it under a GPL like license?
I will do that soon.


**Update!**

[list][*] choose window manager: IceWM, Openbox, Fluxbox, E16
[*] choose panel: FBPanel, XFCE4-Panel, LXPanel
[*] choose desktop: XFDesktop, FBDesk, ROX, PCManFm
[*] new option to integrate [sharp fonts](http://sharpfonts.com) in all programs, crisp and clean.
[*] added [Envy](http://www.albertomilone.com/nvidia_scripts1.html)
[*] fixed remaining bugs concerning my installation menu
[*] firefox addon handling way cleaner than before
[*] no need for numerous sudo prompts anymore
[/list]

Screenshot with Fluxbox, FBPanel, Rox and (optional) sharp fonts:

[[img]http://www.abload.de/thumb/fluxbox-fbpanel-roxf2u.png[/img]](http://www.abload.de/img/fluxbox-fbpanel-roxf2u.png)


Screenshot with Openbox, FBPanel, PCManFM and (optional) sharp fonts:

[[img]http://www.abload.de/thumb/openbox-pcmanfm-fbpavc1.png[/img]](http://www.abload.de/img/openbox-pcmanfm-fbpavc1.png)

---

### Post by Stroganoff on 2008-04-27
This needs some final testing, before I start creating ISOs and upstreaming all of this into Debian/Ubuntu.
Goal: the grand unified distribution...

---

### Post by Changturkey on 2008-04-30
Keep going!

---

### Post by Stroganoff on 2008-04-30
Integrated ivman/pmount to be used with PCManFM instead of thunar-volman.

---

### Post by newscane on 2008-05-01
Things seem to be breaking when I install IceWM.  It worked great about a week ago, then I had to reinstall Ubuntu (hard drive issue, long story).  Now IceWM is giving me broken dependencies on imlib11  and libungif4g.  Is this an IceWM problem or a script problem?  I could go with another wm, but I liked IceWM :)

---

### Post by Stroganoff on 2008-05-01
I absolutely cant imagine how this could be caused by my script. How exactly did you proceed this time? Maybe it's just a repository downtime?

---

### Post by K.Mandla on 2008-05-01
Moved to Installation and Upgrades (archived).

---

### Post by agim on 2008-05-01
I am so glad you are doing this. I am new enough that I can't do this on my own, though I have been trying (flailing might be a more apt description) of doing what you have done. I can't wait to try it.

---

### Post by firmit on 2008-05-01
Great thread!

One thing - LXDE has its own lxde-logout command. Not a big deal, but if you plan to integrate LXDE fully one day... :)

I am working on a LXDE light system myself, based on ubuntu cli. It is quite the challenge and very rewarding! I just love linux! 

Keep it up!

---

### Post by firmit on 2008-05-01
> **Stroganoff said:**
> Integrated ivman/pmount to be used with PCManFM instead of thunar-volman.

Exactly how did you do this? I have trouble implementing this in my own mini-install with LXDE using pcmanfm. I am able to mount/unmount manually, and when I hotplug, my usb-flash gets mounted. But I am not able to umount or mount be right clicking on the device (in pcmanfm) if I manually eject or umount the /media/mount_point.

Which scripts are called from pcmanfm to do this?

EDIT: 
Fixed - I followed the "misleading" instruction on lxde.sourceforge,net, where it says that if I don't have a DM, I should run startlxde in my xinitrc. This did not work for me. However, when I deleted the file, everything worked like a charm. Actually, I deleted ivman and pmount too.

PS: I do like ivman, though, as it automounts at command-line :)

---

### Post by newscane on 2008-05-01
> **Stroganoff said:**
> I absolutely cant imagine how this could be caused by my script. How exactly did you proceed this time? Maybe it's just a repository downtime?
After trying it again (and again), it does appear to be a repository issue.  Each time I run it, I'm able to get a few more packages, but it is having some major issues.  Still going on this morning...

---

### Post by Stroganoff on 2008-05-06
> **firmit said:**
> One thing - LXDE has its own lxde-logout command. Not a big deal, but if you plan to integrate LXDE fully one day... :)
As I wasn't able yet to get lxsession up and running, I'm discarding this for now.

**Update**:
Fixed incomplete Openbox config file.
Made everything localizable, hence no more warnings and missing language packages when using a language other then en|de.

Next thing is implementing a preset framework both for silent installation without menu as for menu selection presets, then I'm going to create the first ISO, I think.

---

### Post by firmit on 2008-05-06
Lxsession has now two versions - the normal and lxsession-light, which does not save sessions. The latter is also now in the LXDE-meta pacakge in their repo ( at least the debian-repo ). I added lxapperance and updated pcmanfm from source, but had some problems compiling lxpanel, so I am still using the 0.3.5.2.

I have converted 100% to LXDE, and have few, if any problems.

---

### Post by newscane on 2008-05-06
I just grabbed the latest tar.gz to do an install.  A few oddities: first, the README says it's beta 7 (the site now says beta 8).  The bigger problem: the English language directory is missing from include/languages (there's only the "de" directory).  This is a bit of a problem, seeing as I have an English-language install.  Ideas?

---

### Post by Stroganoff on 2008-05-07
Oops, I'm really sorry, sometimes I'm just too clumsy. Just move the *.en files in /de/ to include/languages/en/ or redownload the fixed version.
About the version numbers, well, they will make more sense from the point on when I release the ISO. :D

---

### Post by Stroganoff on 2008-05-07
Update:
Fixed all of yesterday's bugs, finished preset framework, included ability to add custom repositories to menu or preset.

Preset files are in /include/presets
To skip menu selection using the 'default' preset file run this:

```
sudo ./install.sh default
```

You can also import up to 8 subpresets, located in /include/presets/sub, example:

```
sudo ./install.sh default sharpfonts
```

---

### Post by songshu on 2008-05-11
what do you use for email?

claws could be recomended

---

### Post by Drate on 2008-05-12
Do you need any gruntwork help with this?  I have been looking for a project to jump in on and yours looks more than worthy.  I am only moderately skilled, and my forte is figuring stuff out by brute-force attempts and an unhealthy amount of googling.

---

### Post by Stroganoff on 2008-05-14
> **songshu said:**
> what do you use for email?
claws could be recomended
It already is.

> **Drate said:**
> Do you need any gruntwork help with this?  I have been looking for a project to jump in on and yours looks more than worthy.

You may extent the [Wiki](http://tomfichtner.de/linux/) and help me in writing a [Makefile](http://tomfichtner.de/linux/wiki/Makefile). Also this is gonna need some Artwork i guess, at least a boot splash screen for the remastered Alternate ISO.

---

### Post by songshu on 2008-05-14
still need help to remaster the alternate?

i just got my feet wet with the mini.iso, basically changing the package selection and changing the preseed file.
looks like you want to have the install script executed as a late command, should be no problem.
briefly scimmed the script tough, but it might be an idea to have some of these things done by meta-packages, just a tought.



just drop me a line if you still need help on this

---

### Post by Drate on 2008-05-15
Two things, one feedback, one question:

Question is this.... how do I turn the numlock off?  I just stalled this on my friend's old laptop and while in X (icewm) the numlock is stuck on!!  On a laptop that renders the keyboard practically unusable.

And my feedback is this:  When I DON'T select Thunderbird or Open Office, it still seems to be installing components of Open Office (greatly slowing down install) and all of Thunderbird... btw.

*EDIT* Did have problem with Java on my friend's laptop, but not my own, attempting to fix now... just didn't install right... doesn't seem to want to either (the bummer beign he is a java programmer :) )

---

### Post by songshu on 2008-05-15
uninstalling numlockx would do it fast and thorough, maybe to thorough ;)

did not see thunderbird but can confirm openoffice, apparently it is in the ubuntu-standard base install, probably as a dependency of some other package which is sloppy in my opinion.
```
Package: ubuntu-standard
Source: ubuntu-meta
Version: 1.102
Architecture: i386
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Installed-Size: 52
Depends: at, cpio, cron, dmidecode, dnsutils, dosfstools, ed, file, ftp, hdparm, info, inputattach, iptables, logrotate, lshw, lsof, ltrace, man-db, memtest86+, mime-support, nano, parted, popularity-contest, psmisc, rsync, strace, time, ufw, w3m, wget
Recommends: apparmor-utils, bash-completion, command-not-found, fdutils, friendly-recovery, iputils-arping, iputils-tracepath, manpages, mlocate, mtr-tiny, ntfs-3g, openssh-client, ppp, pppconfig, pppoeconf, reiserfsprogs, tcpdump, telnet, update-manager-core, uuid-runtime
Section: metapackages
Priority: optional
Description: The Ubuntu standard system
 This package depends on all of the packages in the Ubuntu standard system.
 This set of packages provides a comfortable command-line Unix-like
 environment.
 .
 It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.
```

---

### Post by Drate on 2008-05-15
Wow, I appreciate your insanely quick reply, but i just figured that out (had to VIM all through icewm config fiels, THEN vim through Strog's startup script, found a reference to NUMLOCKX, figured it out from there)...

But you to restore my faith in the Ubuntu Forum help system :)  !!

And by the way... GREAT WORK Stroganoff!

---

### Post by songshu on 2008-05-15
[QUOTE=Drate;4966306found a reference to NUMLOCKX, figured it out from there)...
[/QUOTE]

you wan to keep it a secret ;)

---

### Post by Ripfox on 2008-05-15
I've been looking for something like this to be active for awhile. Thanks!

(btw...*cough* puppy is QUITE usable ;))

---

### Post by Stroganoff on 2008-05-15
> **Drate said:**
> Question is this.... how do I turn the numlock off?  I just stalled this on my friend's old laptop and while in X (icewm) the numlock is stuck on!!  On a laptop that renders the keyboard practically unusable.
I'll insert a question instead of enabling it by default.

> When I DON'T select Thunderbird or Open Office, it still seems to be installing components of Open Office (greatly slowing down install) and all of Thunderbird... btw.
Apparently you have selected "GnuPG", so enigmail (Thunderbird extension) was also installed. Fixed it.
I don't quite know yet where those parts of Openoffice are coming from. Have you installed language-support-en? (or whatever your lang is)

> Did have problem with Java on my friend's laptop, but not my own, attempting to fix now...
Wow, I accidentally dropped Java from the package list at some point. If sun-java6-jre doesn't work for you, try [openjdk-6-jre](http://en.wikipedia.org/wiki/IcedTea).

---

### Post by john_spiral on 2008-05-15
People on this thread might find **gmemusage** useful for isolating memory hogs:

[http://www.tectonic.co.za/2396/find-memory-hogs-with-gmemusage/](http://www.tectonic.co.za/2396/find-memory-hogs-with-gmemusage/)

---

