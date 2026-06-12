---
title: "sources.list help"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by ThatGuy07 on 2010-01-09
I made the mistake of following someone else advice, replacing my sources.list with a copy of theirs and now Im having all sorts of problems. Cannot remove some programs and cannot install others. Also when I open pidgin or evolution I get keyring pop ups never seen before. This was a fresh install of 9.10 yesterday, but I still spent a few hours getting it how Id like. Any idea what I need to add to my sources.list to get things working right again?

here is my current list

```
# Ubuntu Karmic Koala 9.10 Sources list
#
# Repository List based on standard Karmic with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY



# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#skype
deb http://download.skype.com/linux/repos/debian stable non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb http://deb.opera.com/opera/ lenny non-free

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main 

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main 

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#nautilus-dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
#deb http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
deb http://ppa.launchpad.net/freenx-team/ubuntu karmic main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu karmic main

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
deb http://le-web.org/repository stable main

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu karmic main

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main

```

---

### Post by slakkie on 2010-01-09
Looks to be ok, altough the backports don't have partner repo's afaik. anyhows, my sources.list 

```

### Karmic 9.10
# Required     
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
# Recommended                                                                                  
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse      
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse  
# Optional                                                                                     
#deb http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse     
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse 
#deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse    
#deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

```

---

### Post by konqueror7 on 2010-01-09
> **ThatGuy07 said:**
> I made the mistake of following someone else advice, replacing my sources.list with a copy of theirs and now Im having all sorts of problems. Cannot remove some programs and cannot install others. Also when I open pidgin or evolution I get keyring pop ups never seen before. This was a fresh install of 9.10 yesterday, but I still spent a few hours getting it how Id like. Any idea what I need to add to my sources.list to get things working right again?

here is my current list

```
# Ubuntu Karmic Koala 9.10 Sources list
#
# Repository List based on standard Karmic with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com KEY



# Ubuntu supported packages
deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-proposed main restricted universe multiverse

#Canonical Commercial Repository
deb http://archive.canonical.com/ubuntu karmic partner
deb http://archive.canonical.com/ubuntu karmic-backports partner
deb http://archive.canonical.com/ubuntu karmic-updates partner
deb http://archive.canonical.com/ubuntu karmic-security partner
deb http://archive.canonical.com/ubuntu karmic-proposed partner
deb-src http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic-backports partner
deb-src http://archive.canonical.com/ubuntu karmic-updates partner
deb-src http://archive.canonical.com/ubuntu karmic-security partner
deb-src http://archive.canonical.com/ubuntu karmic-proposed partner

#medibuntu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free

#MPlayer Core Libraries
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0DA7581859566E92
deb http://ppa.launchpad.net/rvm/libs/ubuntu karmic main

#vlc 1
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com D739676F7613768D
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu karmic main

#GIMP (Testing Version)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 43BB102C405A15CB
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

# Ubuntu tweak
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6AF0E1940624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu karmic main

#compiz-fusion
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2ED6BB6042C24D89
deb http://ppa.launchpad.net/compiz/ubuntu karmic main

#skype
deb http://download.skype.com/linux/repos/debian stable non-free

#firefox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 632D16BB0C713DA6
deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main

#Ubuntu Mozilla Security Team
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A6DCF7707EBC211F
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main

#opera
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F9A2F76A9D1A0061
deb http://deb.opera.com/opera/ lenny non-free

#chromium-browser
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

#google
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A040830F7FAC5991
deb http://dl.google.com/linux/deb/ stable non-free

#empathy
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FA3A1271
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main 

#pidgin
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7FB8BEE0A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main

#emesene 1.5
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0CC1223EE2314809
deb http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/bjfs/ppa/ubuntu karmic main 

#gnome-globalmenu
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7889D725DA6DEEAA
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main

#gnome-do
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 28A8205077558DD0
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main

#nautilus-dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

#gnome-colors theme
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2D79F61BE8D31A30
deb http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu karmic main

##Themes du ZgegBlog: Project Bisigi
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DE
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main

# disper tool multiple graphical displays
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 66D5C734F6EFB904
#deb http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main
#deb-src http://ppa.launchpad.net/wvengen/ppa/ubuntu karmic main

# Virtualbox
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCF9F87B6DFBCBAE
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

#Freenx Team (freenx, nxagent - remote X)
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A8E3034D018A4CE
deb http://ppa.launchpad.net/freenx-team/ubuntu karmic main
deb-src http://ppa.launchpad.net/freenx-team/ubuntu karmic main

#Back In Time
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2A423FD95416E75D
deb http://le-web.org/repository stable main

#shutter
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FC6D7D9D009ED615
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main

# ifuse for iphone/itouch
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F0876AC9
deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu karmic main

#Terminator
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 978228591BD3A65C
deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu karmic main

#Drizzle
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4FEC45DD06899068
deb http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/drizzle-developers/ppa/ubuntu karmic main

#subversion 1.6
# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6298AD34413576CB
deb http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main
deb-src http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu karmic main

```

comment out all the backports and proposed, also remove the partners repos leaving only the karmic-updates...the rest is fine so far...after all try to update your list...

---

### Post by Docaltmed on 2010-01-09
You didn't happen to keep a copy of your former sources.list, as, like, sources.old or something? (I learned that one the hard way).

Instead of adding more, I might prune the whole thing until I got it back to a working state, then add the stuff I wanted one by one. That way, if you have a problem, you'll know what caused it, and the "why" part will be a whole lot easier to figure out.

---

### Post by Barriehie on 2010-01-09
Found this [[color="blue"]link[/color]](http://repogen.simplylinux.ch/index.php) somewhere here in the forums.  I believe it will generate the sources.list that you get on a new install.  I too have hosed mine before and as previously stated, **sources.old** is a good idea. :)

---

### Post by ThatGuy07 on 2010-01-09
No backup, dont know what I was thinking . Ive quoted out most everything but still the same issues. Specific example, Swapping empathy for pidgin, and cannot remove empathy. In the software center it only has an option to upgrade but that fails saying, well saying nothing now. It seems to have disappeared. but it was saying something along the lines of this is broke, run sudo apt-get install -f .

Barriehie thanks for the link, Im checking it out now .

---

### Post by Barriehie on 2010-01-09
> **ThatGuy07 said:**
> No backup, dont know what I was thinking . Ive quoted out most everything but still the same issues. Specific example, Swapping empathy for pidgin, and cannot remove empathy. In the software center it only has an option to upgrade but that fails saying, well saying nothing now. It seems to have disappeared. but it was saying something along the lines of this is broke, run sudo apt-get install -f .

Barriehie thanks for the link, Im checking it out now .

No problem!  I had an issue trying to remove a package that had left files scattered about and I ended up reinstalling it and then purging it, which completely removed everything.  Prior to the reinstall I couldn't remove anything because package manager says it wasn't installed!

---

### Post by ThatGuy07 on 2010-01-09
ok so I backed up my current sources.list, like I should have to begin with. Went with the link you supplied, and all seems good now. Many thanks for all the quick responses. The support in this community just blows me away.

---

