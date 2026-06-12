---
title: "Ubuntu can not find Ubuntu ? Upgrade 12.04 to 12.10"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by TheVisitors on 2012-10-18
[COLOR=#000000] [COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install update[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]manager[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]core[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]update[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]manager[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]release[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]upgrades

[/COLOR][/COLOR][COLOR=#000000] [COLOR=#0000BB]Prompt[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]normal[/COLOR][COLOR=#007700];[/COLOR][/COLOR]

[COLOR=#000000] [COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get update [/COLOR][COLOR=#007700]&& [/COLOR][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get upgrade[/COLOR][/COLOR]



[COLOR=#000000] [COLOR=#0000BB]sudo [/COLOR][COLOR=#007700]do-[/COLOR][COLOR=#0000BB]release[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]upgrade [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]d[/COLOR] [/COLOR] 


Follow me so far?  Hope so....

[COLOR=DarkRed]Updating repository information
WARNING: Failed to read mirror file

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

To continue please press [ENTER][/COLOR]


**^** OK. Simple enough.  **ENTER** :)



[COLOR=DarkRed]Checking package manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done

Calculating the changes

Calculating the changes

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.


Restoring original system state

Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
=== Command terminated with exit status 1 (Thu Oct 18 13:22:12 2012) ===[/COLOR]


I can press R which just keeps repeating this process. Or X and basically abort the upgrade.

Solution ?

---

### Post by TheVisitors on 2012-10-18
[COLOR=DarkRed]sudo dpkg --configure -a
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/COLOR]

**No broken packages are found.**


[COLOR=DarkRed]sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/COLOR]
[B]
No pending updates either.[/B]

---

### Post by grahammechanical on 2012-10-18
It could be that you are just a bit too quick to upgrade to 12.10. It may be that the mirrors or servers that hold your repositories have not yet been updated with 12.10. Some mirrors are days behind.

[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

Regards.

---

### Post by TheVisitors on 2012-10-18
> **grahammechanical said:**
> It could be that you are just a bit too quick to upgrade to 12.10. It may be that the mirrors or servers that hold your repositories have not yet been updated with 12.10. Some mirrors are days behind.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Regards.

As the update process disabled my 3rd party sources (see above)

And I'm using the main server ...... I would think I'd be safe to rule that out :confused:

---

### Post by kcy29581 on 2012-10-18
It's not ```
sudo do-release-upgrade -d
```, the correct command is ```
sudo do-release-upgrade
```.

The "-d" option is for development releases, so you should avoid using it. I imagine it wont work anymore due to the final version of 12.10 being released.

---

### Post by TheVisitors on 2012-10-18
> **kcy29581 said:**
> It's not ```
sudo do-release-upgrade -d
```, the correct command is ```
sudo do-release-upgrade
```.

The "-d" option is for development releases, so you should avoid using it. I imagine it wont work anymore due to the final version of 12.10 being released.
I learn something new.  Guess all those web guides are not always so helpful.

Well I did as you instructed and still got this.

[COLOR=DarkRed]Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
=== Command terminated with exit status 1 (Thu Oct 18 14:15:49 2012) ===
[/COLOR]

---

### Post by kcy29581 on 2012-10-18
Hmm... I would suggest that you try and make sure everything is updated via ```
sudo aptitude update && sudo aptitude upgrade
```, maybe then reboot just in case it's needed and try the release upgrade again.

I'll see if I can find anything more.

---

### Post by TheVisitors on 2012-10-18
> **kcy29581 said:**
> Hmm... I would suggest that you try and make sure everything is updated via ```
sudo aptitude update && sudo aptitude upgrade
```, maybe then reboot just in case it's needed and try the release upgrade again.

I'll see if I can find anything more.

sudo apt-get update
sudo apt-get upgrade
[COLOR=DarkRed]sudo dpkg --configure -a
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

Same result.  Even after reboot.

---

### Post by Frogs Hair on 2012-10-18
Has the update manager been set to check for all available release updates ? If this has been done the update manager will offer the new release when it is able to connect to the repository.  You should not need the command unless upgrading early .
[http://www.liberiangeek.net/2012/06/upgrade-to-ubuntu-12-10-quantal-quetzal-from-ubuntu-12-04/?ModPagespeed=noscript](http://www.liberiangeek.net/2012/06/upgrade-to-ubuntu-12-10-quantal-quetzal-from-ubuntu-12-04/?ModPagespeed=noscript)

---

### Post by TheVisitors on 2012-10-18
> **Frogs Hair said:**
> Has the update manager been set to check for all available release updates ? If this has been done the update manager will offer the new release when it is able to connect to the repository.  You should not need the command unless upgrading early .
[http://www.liberiangeek.net/2012/06/upgrade-to-ubuntu-12-10-quantal-quetzal-from-ubuntu-12-04/?ModPagespeed=noscript](http://www.liberiangeek.net/2012/06/upgrade-to-ubuntu-12-10-quantal-quetzal-from-ubuntu-12-04/?ModPagespeed=noscript)

Same outcome

Could not calculate the needed changes

---

### Post by TheVisitors on 2012-10-18
I thought removing all my 3rd party repositories would maybe help..... No such luck. :(

Format, install Windows?

^ I joke, but seriously, Linux is a lot harder to upgrade in my opinion.

---

### Post by sffvba[e0rt on 2012-10-18
> **TheVisitors said:**
> I thought removing all my 3rd party repositories would maybe help..... No such luck. :(

Format, install Windows?

^ I joke, but seriously, Linux is a lot harder to upgrade in my opinion.

I would disagree.  The problem you are having is, well... a problem, and not the norm.

That being said, I myself rather keep my data in a seperate partition and do clean installs to avoid any possible issues.



404

---

### Post by TheVisitors on 2012-10-18
> **not found said:**
> I would disagree.  The problem you are having is, well... a problem, and not the norm.

That being said, I myself rather keep my data in a seperate partition and do clean installs to avoid any possible issues.



404
Except I seem to have it every time I try to upgrade to a different version.

The norm for me is I just give up, format, install fresh, and re-install all my programs and settings.... again :(  *sigh*

I'd like to finally be able to upgrade at least once.

---

### Post by oldos2er on 2012-10-18
> **TheVisitors said:**
> And I'm using the main server ...... 

The main server is probably swamped with connections right now. Give it another try in a few days, or try a mirror for your country, if one exists.

---

### Post by phoe2693 on 2012-10-18
having the exact same problem.

had installed the edgers ppa, but ive backed out and still no love.  tried all the usual apt-get and dpkg commands mentioned, no luck either.

Is there a log and lists what packages are "held and broken" when the upgrade starts?  I cant find it anywhere.

---

### Post by TheVisitors on 2012-10-19
Well I do not know what is causing it.

I [COLOR=DarkRed]***purged every***[/COLOR] installed program.  Basically have a fresh install at this point.

Still getting the same error. :(

Will be burning a copy on DVD and just doing a fresh format and install.

This really SUCKS.   Do you have any idea how hard it was to get VMWARE Workstation to play nice?!? (I've un-installed that too)

---

### Post by kcy29581 on 2012-10-19
I'm sorry you're having all the issues, but to be fair, you did try to update to a development release; you mentioned a site where you grabbed the info. What website said to use the "-d" option?

If they are incorrect, we can fix that at least. When you try to refresh your sources, are they still 12.04? If not, they should be.

---

### Post by TheVisitors on 2012-10-19
> **kcy29581 said:**
> I'm sorry you're having all the issues, but to be fair, you did try to update to a development release; you mentioned a site where you grabbed the info. What website said to use the "-d" option?

If they are incorrect, we can fix that at least. When you try to refresh your sources, are they still 12.04? If not, they should be.

Every Google search for "command line upgrade"  (or something similar to that)

I don't think there is anything to fix at this point.

With or without the **-d **it never proceeded past it calculating what was needed.  So it never did try to upgrade (always aborted before)

---

### Post by kcy29581 on 2012-10-19
When I google search the same thing, i never get the "-d"; the sites always say that it's a development release/beta/alpha.

Could you post your/etc/apt/sources.list file? Unless I missed it in a previous post.

---

### Post by kcy29581 on 2012-10-19
[http://ubuntuforums.org/showthread.php?t=1475678](http://ubuntuforums.org/showthread.php?t=1475678)
Give the above a shot.

---

### Post by Tanker Bob on 2012-10-19
> **TheVisitors said:**
> Do you have any idea how hard it was to get VMWARE Workstation to play nice?!? (I've un-installed that too)

You have to manually uninstall Workstation 9 before upgrading Ubuntu, then install Workstation 9 and then a patch for the new kernel. The specific instruction and patch are on the VMWare forums.

---

### Post by TheVisitors on 2012-10-19
> **kcy29581 said:**
> When I google search the same thing, i never get the "-d"; the sites always say that it's a development release/beta/alpha.

Could you post your/etc/apt/sources.list file? Unless I missed it in a previous post.

Originally it was all this

```

###### Ubuntu Main Repos
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ dists/quantal/main/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ dists/quantal/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ quantal main restricted
deb http://www.lug.bu.edu/mirror/ubuntu/ precise main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise main restricted universe multiverse #Added by software-properties

###### Ubuntu Update Repos
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-security main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-security main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-updates main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-proposed main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-proposed main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main # Audacity - http://audacity.sourceforge.net/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # Banshee - https://edge.launchpad.net/~banshee-team

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75198A89
deb http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu precise main # Cairo Composite Manager - http://cairo-compmgr.tuxfamily.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CA186228
deb http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu precise main # Cortina - https://launchpad.net/~cs-sniffer/+archive/cortina

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main # DeaDBeeF - http://deadbeef.sourceforge.net/

## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main # Equinox - https://launchpad.net/~tiheum/+archive/equinox

## Run this command: wget -q -O - http://download.opensuse.org/repositories/Java:/esmska/common-deb/Release.key | sudo apt-key add -
deb http://download.opensuse.org/repositories/Java:/esmska/common-deb/ ./ #Esmska # Esmska - http://code.google.com/p/esmska/

## Run this command: wget http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb http://www.fbreader.org/desktop/debian stable main # FBReader - http://www.fbreader.org/desktop/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # Flacon - http://kde-apps.org/content/show.php?content=113388

## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu precise-getdeb apps # GetDeb - http://www.getdeb.net

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main # Gimp - https://launchpad.net/~otto-kesselgulasch/+archive/gimp

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main # Glx-Dock / Cairo-Dock - http://www.glx-dock.org

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main # GNOME3 extra apps - https://launchpad.net/~gnome3-team/+archive/gnome3

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
deb http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu precise main # GNUzilla and IceCat - http://www.gnu.org/software/gnuzilla/

## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/chrome/deb/ stable main # Google Chrome Browser - http://www.google.com/linuxrepositories/

## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/earth/deb/ stable main # Google Earth - http://www.google.com/linuxrepositories/

## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free # Google Linux Software Repositories - http://www.google.com/linuxrepositories/

## Run this command: wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add  -
deb http://dl.google.com/linux/deb/ testing non-free # Google Linux Software Repositories (Testing) - http://www.google.com/linuxrepositories/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main # Gwibber (Daily) - https://launchpad.net/gwibber

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main # HandBrake Snapshots - http://handbrake.fr/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu precise main # Ironhide - https://launchpad.net/~mj-casalogic/+archive/ironhide/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/jupiter/ubuntu precise main # Jupiter - http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main # Kubuntu Backports - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu precise main # Kubuntu Beta Backports - https://launchpad.net/~kubuntu-ppa/+archive/beta

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu precise main # Kubuntu Experimental - https://launchpad.net/~kubuntu-ppa/+archive/experimental

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu precise main # Kubuntu Updates - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa

## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
deb http://www.hu.freepascal.org/lazarus/ lazarus-stable universe # Lazarus - http://www.lazarus.freepascal.org/

## Run this command:  gpg --keyserver hkp://pgp.mit.edu:11371 --recv-keys 6A11800F  && gpg --export --armor 0F7992B0  | sudo apt-key add -
deb http://www.hu.freepascal.org/lazarus/ lazarus-testing universe # Lazarus (Testing) - http://www.lazarus.freepascal.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main # LibreOffice - http://www.documentfoundation.org/download/

## Run this command: sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
deb http://packages.medibuntu.org/ precise free non-free # Medibuntu - http://www.medibuntu.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb http://ppa.launchpad.net/midori/ppa/ubuntu precise main # Midori - https://launchpad.net/~midori/+archive/ppa

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb http://ppa.launchpad.net/pcf/miro-releases/ubuntu precise main # Miro HD Video Player - http://www.getmiro.com/

## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb http://www.bunkus.org/ubuntu/precise/ ./ # MKVToolnix - http://www.bunkus.org/videotools/mkvtoolnix/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen # MongoDB - http://www.mongodb.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main # Mozilla Daily Build Team - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa

## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add -
deb http://apt.mucommander.com stable main non-free contrib # muCommander - http://www.mucommander.com/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main # OpenShot - http://www.openshotvideo.com

## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ stable non-free # Opera - http://www.opera.com/

## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera-beta/ stable non-free # Opera Beta - http://www.opera.com/

## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
deb http://deb.paissad.net unstable main contrib non-free personal # Paissad's PS3 Media Server - http://deb.paissad.net

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main # Pidgin - http://pidgin.im

## Run this command: wget -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu precise-getdeb games # PlayDeb - http://www.playdeb.net/

## Run this command: wget -q "http://deb.playonlinux.com/public.gpg" -O- | sudo apt-key add -
deb http://deb.playonlinux.com/ precise main # PlayOnLinux - http://www.playonlinux.com/en

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu precise main # qBittorrent - http://qbittorrent.sourceforge.net/

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4BB9F05F
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu precise main # SABnzbd - http://sabnzbd.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
deb http://repository.spotify.com stable non-free # Spotify for Linux Preview - http://www.spotify.com/

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -

## Run this command: wget -q -O- http://archive.ualinux.com/ualinux.key | sudo apt-key add -
deb http://archive.ualinux.com/ubuntu precise main # UAlinux - http://ualinux.com/ualinux-repo

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb http://ppa.launchpad.net/tualatrix/ubuntu precise main # Ubuntu Tweak - http://ubuntu-tweak.com/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu precise main # UbuntuGIS (unstable) - http://trac.osgeo.org/ubuntugis/wiki

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu precise main # UNetbootin - http://unetbootin.sourceforge.net/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main # Unsettings - http://www.florian-diesch.de/software/unsettings/

## Run this command: wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
deb http://download.virtualbox.org/virtualbox/debian precise contrib # VirtualBox - http://www.virtualbox.org

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu precise main # WebKit Team PPA - https://launchpad.net/~webkit-team/+archive/ppa

## Run this command: wget http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -
deb http://download.webmin.com/download/repository sarge contrib # Webmin - http://www.webmin.com

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main # X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 142986CE
deb http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main # Xfce 4.10 - https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main # Xorg Edgers - https://launchpad.net/~xorg-edgers

deb http://update.yuuguu.com/repositories/apt hardy multiverse # Yuuguu - http://yuuguu.com


####### 3rd Party Source Repos

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb-src http://ppa.launchpad.net/audacity-team/daily/ubuntu precise main # Audacity (Source) - http://audacity.sourceforge.net/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu precise main # Banshee (Source) - https://edge.launchpad.net/~banshee-team

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75198A89
deb-src http://ppa.launchpad.net/shnatsel/cairo-compmgr/ubuntu precise main # Cairo Composite Manager (Source) - http://cairo-compmgr.tuxfamily.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CA186228
deb-src http://ppa.launchpad.net/cs-sniffer/cortina/ubuntu precise main # Cortina (Source) - https://launchpad.net/~cs-sniffer/+archive/cortina

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C8E2A7F
deb-src http://ppa.launchpad.net/alexey-smirnov/deadbeef/ubuntu precise main # DeaDBeeF (Source) - http://deadbeef.sourceforge.net/

## Run this command: sudo apt-get update && sudo apt-get install faenza-icon-theme && sudo apt-get install equinox-theme
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main # Equinox (Source) - https://launchpad.net/~tiheum/+archive/equinox

## Run this command: wget http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc -O- | sudo apt-key add -
deb-src http://www.fbreader.org/desktop/debian stable main # FBReader (Source) - http://www.fbreader.org/desktop/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F2A61FE5
deb-src http://ppa.launchpad.net/flacon/ppa/ubuntu precise main # Flacon (Source) - http://kde-apps.org/content/show.php?content=113388

## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main # Gimp (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
deb-src http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu precise main # Glx-Dock / Cairo-Dock (Source) - http://www.glx-dock.org

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main # GNOME3 extra apps (Source) - https://launchpad.net/~gnome3-team/+archive/gnome3

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
deb-src http://ppa.launchpad.net/gnuzilla-team/ppa/ubuntu precise main # GNUzilla and IceCat (Source) - http://www.gnu.org/software/gnuzilla/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu precise main # Gwibber (Daily) (Source) - https://launchpad.net/gwibber

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 816950D8
deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu precise main # HandBrake Snapshots (Source) - http://handbrake.fr/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ECF7E0B3
deb-src http://ppa.launchpad.net/mj-casalogic/ironhide/ubuntu precise main # Ironhide (Source) - https://launchpad.net/~mj-casalogic/+archive/ironhide/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb-src http://ppa.launchpad.net/webupd8team/jupiter/ubuntu precise main # Jupiter (Source) - http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu precise main # Kubuntu Backports (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/backports

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/beta/ubuntu precise main # Kubuntu Beta Backports (Source) - https://launchpad.net/~kubuntu-ppa/+archive/beta

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 493B3065
deb-src http://ppa.launchpad.net/kubuntu-ppa/experimental/ubuntu precise main # Kubuntu Experimental (Source) - https://launchpad.net/~kubuntu-ppa/+archive/experimental

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8AC93F7A
deb-src http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu precise main # Kubuntu Updates (Source) - https://edge.launchpad.net/~kubuntu-ppa/+archive/ppa

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu precise main # LibreOffice (Source) - http://www.documentfoundation.org/download/

## Run this command: sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
deb-src http://packages.medibuntu.org/ precise free non-free # Medibuntu (Source) - http://www.medibuntu.org/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A69241F1
deb-src http://ppa.launchpad.net/midori/ppa/ubuntu precise main # Midori (Source) - https://launchpad.net/~midori/+archive/ppa

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D75E850
deb-src http://ppa.launchpad.net/pcf/miro-releases/ubuntu precise main # Miro HD Video Player (Source) - http://www.getmiro.com/

## Run this command: wget -q http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -
deb-src http://www.bunkus.org/ubuntu/precise/ ./ # MKVToolnix (Source) - http://www.bunkus.org/videotools/mkvtoolnix/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu precise main # Mozilla Daily Build Team (Source) - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B9BA26FA
deb-src http://ppa.launchpad.net/openshot.developers/ppa/ubuntu precise main # OpenShot (Source) - http://www.openshotvideo.com

## Run this command: wget -q -O - http://deb.paissad.net/public-key.asc | sudo apt-key add -
deb-src http://deb.paissad.net unstable main contrib non-free personal # Paissad's PS3 Media Server (Source) - http://deb.paissad.net

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu precise main # Pidgin (Source) - http://pidgin.im

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 47B4D1C4
deb-src http://ppa.launchpad.net/hydr0g3n/ppa/ubuntu precise main # qBittorrent (Source) - http://qbittorrent.sourceforge.net/

## Run this command: gpg --keyserver subkeys.pgp.net --recv 886DDD89 && gpg --export --armor 94C09C7F  | sudo apt-key add -

## Run this command: wget -q -O- http://archive.ualinux.com/ualinux.key | sudo apt-key add -
deb-src http://archive.ualinux.com/ubuntu precise main # UAlinux (Source) - http://ualinux.com/ualinux-repo

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0624A220
deb-src http://ppa.launchpad.net/tualatrix/ubuntu precise main # Ubuntu Tweak (Source) - http://ubuntu-tweak.com/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 314DF160
deb-src http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu precise main # UbuntuGIS (unstable) (Source) - http://trac.osgeo.org/ubuntugis/wiki

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu precise main # UNetbootin (Source) - http://unetbootin.sourceforge.net/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main # Unsettings (Source) - http://www.florian-diesch.de/software/unsettings/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu precise main # WebKit Team PPA (Source) - https://launchpad.net/~webkit-team/+archive/ppa

## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main # Wine (Source) - https://launchpad.net/~ubuntu-wine/+archive/ppa/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main # X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 142986CE
deb-src http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu precise main # Xfce 4.10 (Source) - https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10

## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8844C542
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main # Xorg Edgers (Source) - https://launchpad.net/~xorg-edgers

#Dotdeb.org
deb http://packages.dotdeb.org squeeze all
deb-src http://packages.dotdeb.org squeeze all
#Dotdeb.org php 5.4
deb http://packages.dotdeb.org squeeze-php54 all
deb-src http://packages.dotdeb.org squeeze-php54 all

deb http://download.virtualbox.org/virtualbox/debian precise contrib
```


However it is now only just this

```


###### Ubuntu Main Repos
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ dists/quantal/main/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ dists/quantal/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Alpha amd64 (20120905.2)]/ quantal main restricted
deb http://www.lug.bu.edu/mirror/ubuntu/ precise main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise main restricted universe multiverse #Added by software-properties

###### Ubuntu Update Repos
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-security main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-security main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-updates main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-proposed main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-proposed main restricted universe multiverse #Added by software-properties
deb http://www.lug.bu.edu/mirror/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://www.lug.bu.edu/mirror/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by ast3citos on 2012-10-23
If you do-release-upgrade with -d it should upgrade to 12.10

Mine is doing right now. It has something to do with 12.04 being LTS

Found it [here]("http://askubuntu.com/questions/125392/why-is-no-new-release-found-when-upgrading-10-04-to-12-04-lts")

According to Ubuntu Engineering Foundations team manager Steve Langasek:

> Upgrades between LTS releases are not enabled by default until the first point release, 12.04.1, scheduled for July. It is recommended that most LTS users wait until then before upgrading to 12.04.

**EDIT:**

Further investigation led me to the following:

LTS versions won't find new versions until a new LTS version is released (that'd be 14.04). Should you need to upgrade from 12.04 LTS to the following non-LTS version, you have to use -d

LTS is meant for systems needed to be stable, which don't upgrade functionalities over time, and only have security updates... More or less, this what I learnt in the last hour. I hope someone here will shed little more light on the subject.

Hope this helps.

---

### Post by BitBuilder on 2012-10-27
To allow upgrades to incremental non-LTS releases: 
edit --> /etc/update-manager/release-upgrades and set Prompt=normal
for only LTS releases have Prompt=lts.

This corrects what is described at the link below, because the information seems faulty as having this set to 'lts' as described did not allow for the upgrade from 12.04LTS to 12.10 for me. Only after setting it to 'normal', and then issuing the normal *do-release-upgrade* command was the upgrade found and installed successfully.

[https://help.ubuntu.com/community/QuantalUpgrades](https://help.ubuntu.com/community/QuantalUpgrades)

---

