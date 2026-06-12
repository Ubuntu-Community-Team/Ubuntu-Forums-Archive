---
title: "safe way upgrading from warty to hoary"
date: 2005-04-03
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-04-03
What is the safest way to upgrade from warty to hoary.
Do i use dist-upgrade or should i use synaptic. I need a stable system so i will wait for the final release. 

Last time i installed hoary,  my system began to freeze withe the new kernel.

---

### Post by bihe on 2005-04-03
ubuntuguide: [http://ubuntuguide.org/index.html#upgradewartytohoary](http://ubuntuguide.org/index.html#upgradewartytohoary) 

ubuntu-homepage1: [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)  
ubuntu-homepage2: [http://www.ubuntulinux.org/wiki/UpgradingMyWartySystemToHoary/view?searchterm=hoary](http://www.ubuntulinux.org/wiki/UpgradingMyWartySystemToHoary/view?searchterm=hoary)

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=bihe]ubuntuguide: [http://ubuntuguide.org/index.html#upgradewartytohoary](http://ubuntuguide.org/index.html#upgradewartytohoary) 

ubuntu-homepage1: [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)  
ubuntu-homepage2: [http://www.ubuntulinux.org/wiki/UpgradingMyWartySystemToHoary/view?searchterm=hoary](http://www.ubuntulinux.org/wiki/UpgradingMyWartySystemToHoary/view?searchterm=hoary)[/QUOTE]
 don't forget to change to UTF8 like mentioned on the wiki by the command :

sudo dpkg-reconfigure locales

Also check the backports forum if you're using backports you have to remove them before dist-upgrading.

---

### Post by awtomlinson on 2005-04-05
HELP!!!  I have completely hosed my Warty install while attempting to upgrade to Hoary.  The first thing that I noticed was tons of dependency issues.  Then, Synaptic would not open.  Apt-get worked fine, but no Synaptic.  After rebooting, the situation is much worse.  I get an error stating that XFree86 is still running.  Nautilus crashes over and over again, and will not even open.  The only way I can log in is with the Fail Safe Terminal option.  I am not currently with my home system now, so I can post the exact error messages later if required.  Why is XFree86 still being used, and why is it completely hosed, causing Nautilus to not open?  My graphics card is the NVIDIA 5600 Ultra, and I'm running the Athlon XP 3200+ processor.  At any rate, I changed all instances of Hoary back to Warty in my sources.list file, to no avail.  The same issues occur.  I would like to revert back to Warty so I can back up certain data before doing a fresh install of Hoary.  If at all possible, I would like to simply upgrade to Hoary.  The only backport that I used is for Firefox.

---

### Post by ubuntu_demon on 2005-04-05
[QUOTE=awtomlinson]HELP!!!  I have completely hosed my Warty install while attempting to upgrade to Hoary.  The first thing that I noticed was tons of dependency issues.  Then, Synaptic would not open.  Apt-get worked fine, but no Synaptic.  After rebooting, the situation is much worse.  I get an error stating that XFree86 is still running.  Nautilus crashes over and over again, and will not even open.  The only way I can log in is with the Fail Safe Terminal option.  I am not currently with my home system now, so I can post the exact error messages later if required.  Why is XFree86 still being used, and why is it completely hosed, causing Nautilus to not open?  My graphics card is the NVIDIA 5600 Ultra, and I'm running the Athlon XP 3200+ processor.  At any rate, I changed all instances of Hoary back to Warty in my sources.list file, to no avail.  The same issues occur.  I would like to revert back to Warty so I can back up certain data before doing a fresh install of Hoary.  If at all possible, I would like to simply upgrade to Hoary.  The only backport that I used is for Firefox.[/QUOTE]
 don't be too afraid you will lose data but you can always backup using hoary of course

downgrading is not such a good idea I think.

I'm assuming you have followed the guides correctly. If you don't please follow them before doing my suggestions.

sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install xserver-xorg ubuntu-desktop
sudo apt-get dist-upgrade

If X won't startup after this please do :
sudo dpkg-reconfigure xserver-xorg
also change your locales using :
sudo dpkg-reconfigure locales

---

### Post by awtomlinson on 2005-04-05
demon666_nl, thanks for your reply.  will try this when i get home from work.  i would assume that my issues occur because i have greatly mixed several debian repositories with the ubuntu ones.  

actually, my /home directory is on a separate partition, so all i really need to backup are my firefox bookmarks.  where are they located?  also, a somewhat unrelated question.  under my home directory, i have directories named:  Audio Library, Document Library, Video Library, etc.  using the terminal, i can't change into these directories.  i'm told that they don't exist, i assume because there's a space between names instead of an underscore (Audio Library vs. Audio_Library).  obviously, i can access these directories via the gui, but in the event that i have to do a clean install, how do i access these folders via the command line?

---

### Post by ubuntu_demon on 2005-04-06
awtomlinson : your firefox bookmarks are located in your homedir also.... somewhere in .mozilla

awtomlinson : type the first few letters of a directorie and then press tab to get the name.

awtomlinson : You're probably right that you have those issues because of other repositories mixed in. If you didn't add too much packages from other repositories apt-get install ubuntu-base -f will probably work. But please read on before you do this.

I always gave the advice that newbies shouldn't run hoary before the release unless they understand the risk. Of course minor issues could occur but the chances of big ones that would damage your data were very low. Since hoary will be released very very soon I encourage everyone who wants to upgrade to do it.

Regarding repositories in both warty and hoary. I wouldn't include other repositiories than marillat and ubuntu-backports. 

If you need a specific .deb file that isn't included in these repositories (most are included) just having a little patience is the safest bet. But sometimes you really need a specific package then try to download it manually and see whether you can resolve the dependencies by apt-getting them (install the packages that "dpg -i packagename.deb" says that are needed ... don't go download a lot of dependencies ... if you can't apt-get them from your repositories it's probably not worth the risk). Sometimes there are no .deb files available or you can't resolve the dependencies then you can try to compile them yourself .. you can create a deb file with the package "checkinstall". 

practical advice regarding safe upgrading for everyone :

-you can keep marillat in your sources.list when you are upgrading

-you should remove all other repositories from your sources.list and also remove the corresponding packages. 

In this thread there's an explanation how to remove your warty backports packages : [http://ubuntuforums.org/showthread.php?t=12174](http://ubuntuforums.org/showthread.php?t=12174)

awtomlinson :

1) If you have upgraded packages to hoary. If you have only a couple of installed packages from other repositories this will work :

Follow the backports thread about how to remove their packages. Remove packages from other repositories in an analogue way. And then do this :

sudo apt-get update 
sudo apt-get install ubuntu-base -f
sudo apt-get install ubuntu-desktop xserver-xorg -f
sudo apt-get dist-upgrade

You have upgraded to hoary now. Do dpkg-reconfigure locales and dpkg-reconfigure xserver-xorg if needed.

If it still didn't work you have created a bigger mess than I thought. We'll have to resolve the depencies issues manually. Please post your sources.list and the output of the procedure I just said.

2) If you haven't upgraded packages you aren't actually running hoary. Change your sources.list back to warty. Follow the backports thread about how to remove their packages. Remove packages from other repositories in an analogue way. And then do this :

sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade

After this follow the regular guides of upgrading to hoary. (change your sources.list , keep marillat and dist-upgrade)

You have upgraded to hoary now. Do dpkg-reconfigure locales and dpkg-reconfigure xserver-xorg if needed.

---

### Post by awtomlinson on 2005-04-06
demon666, thanks again.  you've helped me to log back into the gui.  not sure if i'm running hoary or warty, but i definitely am running gnome 2.10.  synaptic still won't work, but obviously, apt-get will.  from the following directions that you previously gave me, everything worked except for installing the ubuntu base and the x server.  i received the following error for both:  sub-process /usr/bin/dpkg returned an error code (1)

"sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install xserver-xorg ubuntu-desktop
sudo apt-get dist-upgrade

If X won't startup after this please do :
sudo dpkg-reconfigure xserver-xorg
also change your locales using :
sudo dpkg-reconfigure locales"

so, now my issues are:

1.  can't install ubuntu base
2.  can't switch to x server from xfree86
3.  synaptic doesn't work

also, please help explain the ubuntu-base.  it is my understanding that if the ubuntu-base is not installed, the only drawback is that i will have to manually update the distro.  i can live with that, because i often want to uninstall some packages, but am warned that ubuntu-base will be removed.  i would rather have my system exactly how i want it.  manually upgrading is no big deal.

thanks again for all of your help.

---

### Post by ubuntu_demon on 2005-04-06
[QUOTE=awtomlinson]demon666, thanks again.  you've helped me to log back into the gui.  not sure if i'm running hoary or warty, but i definitely am running gnome 2.10.  synaptic still won't work, but obviously, apt-get will.  from the following directions that you previously gave me, everything worked except for installing the ubuntu base and the x server.  i received the following error for both:  sub-process /usr/bin/dpkg returned an error code (1)

"sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install xserver-xorg ubuntu-desktop
sudo apt-get dist-upgrade

If X won't startup after this please do :
sudo dpkg-reconfigure xserver-xorg
also change your locales using :
sudo dpkg-reconfigure locales"

so, now my issues are:

1.  can't install ubuntu base
2.  can't switch to x server from xfree86
3.  synaptic doesn't work

also, please help explain the ubuntu-base.  it is my understanding that if the ubuntu-base is not installed, the only drawback is that i will have to manually update the distro.  i can live with that, because i often want to uninstall some packages, but am warned that ubuntu-base will be removed.  i would rather have my system exactly how i want it.  manually upgrading is no big deal.

thanks again for all of your help.[/QUOTE]
 please post your sources.list

make sure these lines are exactly in your sources.list :

```

deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

```

then do again

sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install xserver-xorg ubuntu-desktop
sudo apt-get dist-upgrade

---

### Post by awtomlinson on 2005-04-06
demon66_nl, i do indeed have these repositories.  i simply changed all instances of warty to hoary.  i also have the marillat and backports repositories, but i have commented them out a month or so ago.  again, the only backport that i used was for firefox (i think).  i have at least 10 official debian repositories also, but i commented them all out before attempting to upgrade to hoary.  during my attempted upgrade, the hoary repositories were the only ones used.  i can give you my exact sources.list file later tonight.  my main problem, i think, is that i used the debian repositories to update every program that i had, i simply wanted the latest version of everything.

---

### Post by ubuntu_demon on 2005-04-06
[QUOTE=awtomlinson]demon66_nl, i do indeed have these repositories.  i simply changed all instances of warty to hoary.  i also have the marillat and backports repositories, but i have commented them out a month or so ago.  again, the only backport that i used was for firefox (i think).  i have at least 10 official debian repositories also, but i commented them all out before attempting to upgrade to hoary.  during my attempted upgrade, the hoary repositories were the only ones used.  i can give you my exact sources.list file later tonight.  my main problem, i think, is that i used the debian repositories to update every program that i had, i simply wanted the latest version of everything.[/QUOTE]
 If you have ever done an sudo apt-get update followd by an sudo apt-get upgrade when you had backports in your sources.list not only firefox will be from backports. Please follow their thread. 

If you added the debian repositories (probably unstable right?) then you are running debian instead of ubuntu. Please replace your sources.list with the one  from the Guidetohoary. 

Go here to solve your dependencies hell :

[http://www.ubuntuforums.org/showthread.php?p=118613#post118613](http://www.ubuntuforums.org/showthread.php?p=118613#post118613)

---

### Post by awtomlinson on 2005-04-07
demon666_nl, i also had the following repositories in sources.list:

#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) stable main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) stable/non-US main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) unstable/non-US main contrib non-free
#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) testing main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) testing/non-US main contrib non-free

when trying to get rid of the backports, i can't even install apt-show-versions, nor can i install debfoster.  i receive the following error while attempting to get rid of the backports & when attempting to install debfoster:

The following packages have unmet dependencies:
  apt-show-versions: Depends: libapt-pkg-perl but it is not going to be installed
  bicyclerepair: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  gnome-panel: Depends: gnome-menus (>= 2.9.4) but it is not going to be installed
  hal-device-manager: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
                      Depends: python2.4-dbus (>= 0.22-3) but it is not going to be installed
                      Depends: python2.4-gnome2 but it is not going to be installed
                      Depends: python2.4-glade2 but it is not going to be installed
  nautilus-cd-burner: Depends: libnautilus-burn1 but it is not going to be installed
  python-examples: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  python-id3lib: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  python-pyogg: Depends: python (>= 2.4) but 2.3.5-1 is to be installed

---

### Post by ubuntu_demon on 2005-04-07
[QUOTE=awtomlinson]demon666_nl, i also had the following repositories in sources.list:

#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) stable main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) stable/non-US main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) unstable/non-US main contrib non-free
#deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) testing main contrib non-free
#deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) testing/non-US main contrib non-free

when trying to get rid of the backports, i can't even install apt-show-versions, nor can i install debfoster.  i receive the following error while attempting to get rid of the backports & when attempting to install debfoster:

The following packages have unmet dependencies:
  apt-show-versions: Depends: libapt-pkg-perl but it is not going to be installed
  bicyclerepair: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  gnome-panel: Depends: gnome-menus (>= 2.9.4) but it is not going to be installed
  hal-device-manager: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
                      Depends: python2.4-dbus (>= 0.22-3) but it is not going to be installed
                      Depends: python2.4-gnome2 but it is not going to be installed
                      Depends: python2.4-glade2 but it is not going to be installed
  nautilus-cd-burner: Depends: libnautilus-burn1 but it is not going to be installed
  python-examples: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  python-id3lib: Depends: python (>= 2.4) but 2.3.5-1 is to be installed
  python-pyogg: Depends: python (>= 2.4) but 2.3.5-1 is to be installed[/QUOTE]
 If you are choosing the debfoster way you won't need to remove packages by hand using apt-show-versions.

what's the output of :
$ sudo apt-get install -f

if this succeeds probably you can install debfoster. if this doesn't succeed we could try to figure out the dependencies hell but I would choose for a reinstall then (unless it's an easy one to solve)

---

### Post by awtomlinson on 2005-04-07
demon666_nl, i will check this later tonight when i get home.  just in case i do have to do a clean install of hoary, do i need to do anything special to make it mount my /home partition once installed, or will it automatically do this?  in this case, i would simply format my / partition anew with the hoary install CD.

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=awtomlinson]demon666_nl, i will check this later tonight when i get home.  just in case i do have to do a clean install of hoary, do i need to do anything special to make it mount my /home partition once installed, or will it automatically do this?  in this case, i would simply format my / partition anew with the hoary install CD.[/QUOTE]
 type this :
$ cat /etc/fstab

and rember the location of your homedir (for example /hda7). When reinstalling you have to partition manually and mount this homedir. If you think this is too complicated just backup your homedir and let the installer do the partitioning.

And if you still haven't tried the clean install this is also you might try :

sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get install ubuntu-base -f
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade

---

### Post by Deusiah on 2005-04-09
My Hoary upgrade was messed up too, more apt get issues.

I think the best thing to do (at least it was for me) is to wipe everything and start again, everything except for your home partition of course. You'll loose lots of programs you installed but it's easier to install them again than it is to get a Hoary upgrade to work lol.

---

### Post by awtomlinson on 2005-04-09
o.k.  i decided to go ahead & do a fresh install of hoary.  thanks for the help though, demon666_nl, i really appreciate it.  now, since doing a fresh install of hoary, i have a problem with my /home partition.  when i did the fresh install, i simply formatted my / and swap partitions anew with hoary, i left the /home partition alone. however, when installing hoary, i did manually edit the partition table & make sure /home was flagged as the home directory. now, hoary has made a /home directory on the / partition.  i know how to mount the old /home partition, and i added it to my fstab file.  the first time that i mounted it, my desktop settings from warty were automatically loaded upon login to the gdm, but i had duplicate menu entries under Applications, one each for the warty settings and one each for the new hoary settings.  now since rebooting the system, i have to manually mount the /home partition, but my new hoary menu & desktop configurations are all that i have, the old ones are gone.

how can i automatically mount the /home partition at bootup, use the /home configuration settings (bookmarks, menu entries, desktop background, etc) from my old warty install, and avoid having duplicate menu entries?

my fstab file referring to the /home partition is as follows.  please note that the hda4 (/home partition) listing has been changed for indexing with beagle:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /home           reiserfs defaults,errors=remount-ro,user_xattr 0 1
/dev/hda3       /               reiserfs notail          0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by awtomlinson on 2005-04-10
o.k. so i've changed my fstab file & my /home partition now boots automatically.  however, i still have duplicate menu entries from the warty settings & the hoary settings.  the gnome menu editor won't even see these duplicates.  how can i delete the duplicates?

---

### Post by ubuntu_demon on 2005-04-10
[QUOTE=awtomlinson]o.k. so i've changed my fstab file & my /home partition now boots automatically.  however, i still have duplicate menu entries from the warty settings & the hoary settings.  the gnome menu editor won't even see these duplicates.  how can i delete the duplicates?[/QUOTE]
 try removing the .gnome* directories and re-login.This probably will reset your menu to default. Then you just have to install menu-editor from the 3d party project also on the forums and edit the menu until you are satisfied.

---

### Post by ubuntu_demon on 2005-04-10
[QUOTE=Deusiah]My Hoary upgrade was messed up too, more apt get issues.

I think the best thing to do (at least it was for me) is to wipe everything and start again, everything except for your home partition of course. You'll loose lots of programs you installed but it's easier to install them again than it is to get a Hoary upgrade to work lol.[/QUOTE]
 for most people it works.
But you have a couple important things to do :
1) remove all software from all other repositories (excluding marillat but including backports)
2) if you are using gnome make sure ubuntu-desktop and ubuntu-base are installed before dist-upgrading

If these two conditions are met for most people there aren't much problems. It could be you have to reconfigure you xserver-xorg though.

---

### Post by awtomlinson on 2005-04-10
no go on the menus.  i have the gnome menu editor installed.  i have deleted all references to the files & folders mentioned in the following thread:

[http://ubuntuforums.org/showthread.php?t=19652&highlight=hoary+menus](http://ubuntuforums.org/showthread.php?t=19652&highlight=hoary+menus)

no matter what i do, i have duplicate menu entries.  even using the menu editor as root does not resolve the issue.  the menu editor can't even see the duplicates.  surely, these entries are stored somewhere in hoary?

also, even though i know exactly how to change the gdm screen and the gnome splash screen, when i change these, it does not work.  i guess hoary is not quite ready & a few bugs need to be worked out.  none of these things are a huge deal, but they are very annoying and will hopefully be fixed soon, especially the menu entries.

---

### Post by awtomlinson on 2005-04-11
well, guys, i got rid of the duplicate entries, but in the process i deleted almost all entries under Applications: System Tools, Games, System: Preferences & System: Administration.  this is terrible.  anybody got a clue how to get those entries back without repeating my duplicate entry nightmare???

---

### Post by ubuntu_demon on 2005-04-11
[QUOTE=awtomlinson]well, guys, i got rid of the duplicate entries, but in the process i deleted almost all entries under Applications: System Tools, Games, System: Preferences & System: Administration.  this is terrible.  anybody got a clue how to get those entries back without repeating my duplicate entry nightmare???[/QUOTE]
 remove the ~/.gnome* directories and re-login  ... then you have the default menu. After this run the menueditor to put in what you need.

---

### Post by Deusiah on 2005-04-11
Yes I forgot to say that I had to delete all the .gnome* folders :)

demon666_nl I should imagine the upgrade does work for most just it didn't work for me on two PC's and perhaps a third if I bother to try and upgrade it, I think a fresh install would be quicker.

The first computer I tried it on has some kdelibs dependancy issues, the second computer I tried it on had some other dependancy issues. Perhaps the things you suggested would have fixed them but I did not see any info about them on the upgrade guide.

---

### Post by jdong on 2005-04-11
Ok, as of late last week, backports smoothly upgrades to Hoary. Just replace warty-backports/extras with hoary in sources.list, and you're set.

---

### Post by awtomlinson on 2005-04-11
demon666_nl,

deleting all of the ~/.gnome* directories and re-logging in did not resolve the issue.  it simply removed some of my panel launchers.  i still don't have most of the menu entries.  entries that i have to have.  the issue is that my /home partition transferred my warty settings to hoary when i mounted /home in hoary.  the menu editor does not help.  please tell me that i won't have to reinstall hoary to recover my menu items.  this is easily the most annoying thing that i've ever dealt with.

---

### Post by ubuntu_demon on 2005-04-12
[QUOTE=awtomlinson]demon666_nl,

deleting all of the ~/.gnome* directories and re-logging in did not resolve the issue.  it simply removed some of my panel launchers.  i still don't have most of the menu entries.  entries that i have to have.  the issue is that my /home partition transferred my warty settings to hoary when i mounted /home in hoary.  the menu editor does not help.  please tell me that i won't have to reinstall hoary to recover my menu items.  this is easily the most annoying thing that i've ever dealt with.[/QUOTE]
 You won't have to reinstall. Gnome 2.12 will make managing your menus a lot easier. This is a missing feature in gnome 2.10 and has nothing to do with Ubuntu.

Didn't removing ~/.gnome* directories  solve duplicate entries in your menu ?

Why can't you add the menu entries that you want using the menu editor ?

If for some reason you can't edit a particular item with the menu editor and the issue is not known you should report it in their forum.

To remove a particular menu item from showing up in gnome you can locate the corresponding .desktop file and edit this file.
most menu items are in .desktop files in /usr/share/applications
so for example:
$ sudo pico /usr/share/applications/gaim.desktop
and add/edit the last line into 
```

OnlyShowIn=kde

```

The debian menu and maybe some others you can remove by doing this (the menu and menu-xdg packages get you a debian menu in all your desktop environments):

Delete
~/.menu
~/.menu-xdg

after adding/removing menu items re-login or 
$ killall gnome-panel

---

### Post by awtomlinson on 2005-04-12
Demon666_nl, 

yes, it did get rid of my duplicate entries.  i don't have the debian menu.  i should have no problem adding the entries back to the games menu, but how do i know exactly what is supposed to be in Applications: System Tools, System: Preferences & System: Administration?  Almost every entry from these categories is gone.  the menu editor will only see the accessories and graphics categories under Applications.  nothing else.  my usr/share/applications folder is empty except for the kde folder.  can anyone help??  i know this is not a hoary issues, but rather a gnome 2.10 issue, but any help would be appreciated.

---

### Post by ubuntu_demon on 2005-04-13
[QUOTE=awtomlinson]Demon666_nl, 

yes, it did get rid of my duplicate entries.  i don't have the debian menu.  i should have no problem adding the entries back to the games menu, but how do i know exactly what is supposed to be in Applications: System Tools, System: Preferences & System: Administration?  Almost every entry from these categories is gone.  the menu editor will only see the accessories and graphics categories under Applications.  nothing else.  my usr/share/applications folder is empty except for the kde folder.  can anyone help??  i know this is not a hoary issues, but rather a gnome 2.10 issue, but any help would be appreciated.[/QUOTE]
 gnome 2.10 menu editting is not very nice I don't like it either.

If you did a clean install and you removed your ~/.gnome* directories you should have the same menus as everyone else who just installed. If this isn't the case then maybe you have uninstalled ubuntu-desktop or did something else wrong after the installation. Try installing ubuntu-desktop and removing your ~/.gnome* directories once more then.

You should be able to add menuitems in all the submenu's of the applications menu using the menu editor. If you just add what you need you should be fine. There's no point in adding things you don't use.

If this doesn't help you should search the forums or ask the people at the menu editor project because I've told you pretty much as much as I know regarding menu editting. I'm sorry.

---

### Post by awtomlinson on 2005-04-13
thanks again, demon666_nl.  i'll let this one die, in this thread anyway, as it's strayed away from the main thread topic.

---

### Post by ubuntu_demon on 2005-04-13
[QUOTE=awtomlinson]thanks again, demon666_nl.  i'll let this one die, in this thread anyway, as it's strayed away from the main thread topic.[/QUOTE]
 ok

---

### Post by Psquared on 2005-04-17
[QUOTE=jdong]Ok, as of late last week, backports smoothly upgrades to Hoary. Just replace warty-backports/extras with hoary in sources.list, and you're set.[/QUOTE]

Not for me it doesn't. I've tried 5 or 6 times and each time the dist-upgrade ends with a message about fixing Alsa and something called bogofilter ... it never upgrades to Hoary.

The sources.list file I am using for the update and dist-upgrade is as follows:

> 
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe  
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe 

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse 

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted 

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main 
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main 
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main 

# deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe 
# deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 
# deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 

# deb [http://www.grawert.net/ubuntu/](http://www.grawert.net/ubuntu/) warty universe 

# deb [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./ 



Am I missing something?

---

### Post by jdong on 2005-04-17
I don't have anything in Backports that may conflict Alsa or bogofilter. It doesn't look Backports-related. Can you post the exact error message?

---

### Post by Psquared on 2005-04-17
> **jdong]I don't have anything in Backports that may conflict Alsa or bogofilter. It doesn't look Backports-related. Can you post the exact error message?[/QUOTE]

Sure, here goes:

[quote]
 937 upgraded, 168 newly installed, 25 to remove and 1 not upgraded.
Need to get 0B/606MB of archives.
After unpacking 241MB of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg-deb: file `/var/cache/apt/archives/diveintopython_5.4-1ubuntu1_all.deb' contains ununderstood data member data.tar.bz2 , giving up

********************** this is where the buffer clears itself and then the following starts:

alsa-lib (1.0.7-1) unstable said:**
> http://bugs.debian.org/275573[/url] for more information.

-- Jordi Mallach <jordi@debian.org> Wed, 18 Nov 2004 10:00:00 +0200
bogofilter (0.93.1-2) unstable; urgency=medium

* If this is a new installation, or if you are upgrading from a
version prior to 0.93.0-1, you should have no problems. If,
on the other hand, you are unfortunate enough to be upgrading
from 0.93.0-1 or 0.93.0-2, you must manually upgrade each of
your wordlist databases before it will function again.
- To do so, first make sure you have the db4.2-util package
installed, then
1. Stop invocation of bogofilter
2. db4.2_recover -h ~/.bogofilter
3. rm ~/.bogofilter/lockfi*
4. cd ~/.bogofilter && rm $(db4.2_archive -h .)
5. Resume invocation of bogofilter
- Repeat this upgrade procedure for each relevant bogofilter
wordlist database, substituting the directory name for
"~/.bogofilter".
* Alternately, if you don't want to upgrade your database, you
may move or delete it and rebuild your wordlist from scratch.

-- Clint Adams <schizo@debian.org> Sat, 27 Nov 2004 16:29:00 -0500

bogofilter (0.93.0-1) unstable; urgency=low

* For more detailed information, read
/usr/share/doc/bogofilter/RELEASE.NOTES-0.93 .
* bogofilter's defaults have changed. All users should be made aware
that depending on their configurations, the words in the header added
to messages by bogofilter in passthrough mode may abruptly change from
"Yes" and "No" to "Spam", "Ham", and "Unsure"; and this may render
useless any filtering based on these headers.
* bogofilter has switched to use the Berkeley DB Transactional Data
Store. bogofilter will read databases created by previous versions,
though rebuilding the database is recommended to take advantage of all
features. Currently transaction log files need to be archived or
deleted manually.

-- Clint Adams <schizo@debian.org> Sat, 6 Nov 2004 23:05:11 -0500
eog (2.8.1-1) experimental; urgency=low

:

* The Nautilus "View as Collection" component isn't available anymore.

The release note explanations:

The by far biggest change for the default GNOME image viewer is the removal
of the bonobo components. It comes now as a monolithic program again and
makes use of the new wonderful GtkUIManager API. This change leads to great
speed improvements and a much better user interface. On the shadow side the
Nautilus "View as Collection" component isn't available anymore. It's
planned to provide a new Nautilus extension in the future as a replacement.

- Sebastien Bacher <seb128@debian.org> Mon, 25 Oct 2004 22:03:56 +0200
gnome-volume-manager (1.1.2-3) unstable; urgency=low

As of this version gnome-volume-manager uses pmount for mounting and
unmounting devices. To be able to use pmount, the user must be a
member of the plugdev group. If a user isn't part of this group,
gnome-volume-manager will be unable to mount devices!

For more information about pmount and its policy see the pmount manpage.

-- Sjoerd Simons <sjoerd@debian.org> Wed, 24 Nov 2004 11:21:31 +0100
mozilla (2:1.7.6-2) unstable; urgency=low

* Executable name was changed to mozilla-suite.
Please update property of your personal desktop icons.

-- Takuo KITAME <kitame@debian.org> Wed, 23 Mar 2005 20:14:42 +0900

End


As I said, this text spits out in the terminal (if I am using apt-get dist-upgrade or synaptic) at the end and I cannot proceed any further.

I use the sources.list above (with everything changed to hoary) except I comment out merillat. I have tried it with merillat not commented out and I have tried it with just the basic (official) repos and though the number of packages changes I get the same message.

Any ideas?  ](*,)

---

### Post by jdong on 2005-04-17
Somehow, you're using an older version of dpkg/apt that doesn't support .bz2 compression.

Try using Synaptic to upgrade APT and dpkg first.

---

### Post by Psquared on 2005-04-17
[QUOTE=jdong]Somehow, you're using an older version of dpkg/apt that doesn't support .bz2 compression.

Try using Synaptic to upgrade APT and dpkg first.[/QUOTE]

Seems I am using the most current versions of both:

Apt: Installed Version: 0.5.27.1
dpkg: Installed Version: 1.10.27ubuntu1

There are some other things I could install, but none of them seem related to what we are talking about.

---

### Post by Psquared on 2005-04-17
One other thing that might help. I have aptitude installed. Could that be interfering?

I also have a couple of unmet dependencies and two packages are held back with every update or upgrade.

They are:

libimlib2
libpostproc0

When I try to install them I get the following error:

> 
peyre@PTL-Mobile:~ $ sudo apt-get install libimlib2
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libimlib2: Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
             Depends: libungif4g (>= 4.1.3) but 4.1.0b1-6 is to be installed
E: Broken packages


> 
peyre@PTL-Mobile:~ $ sudo apt-get install libpostproc0
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpostproc0: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-13ubuntu2.2 is to be installed
E: Broken packages


---

