---
title: "What ppa's are you looking out for for Lucid ?"
date: 2009-11-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-11-03
I have four:
rvm/smplayer
rvm/mplayer
nvidia-vdpau
chromium-daily

---

### Post by phenest on 2009-11-03
Apart from Google Chrome, none. But then Chrome isn't in the repo's at all. I want to make sure Ubuntu works as they intended before I go messing with it. So, unless it's not in the repo's, I won't be adding any.

---

### Post by Regenweald on 2009-11-03
Good point, but in my case, i don't think that those packages are too invasive.

---

### Post by jfernyhough on 2009-11-03
You don't want to know how many PPAs I have enabled.

Actually, I wonder how many I have... let me look.

28 in total, including 10 non-PPA third-part repos (opera, skype, google etc.).

```
## Main
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse

## Updates
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Proposed
deb http://archive.ubuntu.com/ubuntu/ lucid-proposed main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse

## Commercial
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

## Security
deb http://archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse

###### Third-Party Repos ######

## Medibuntu
deb http://packages.medibuntu.org/ karmic free non-free

## Upstream Opera
deb http://deb.opera.com/opera/ testing non-free

## Wine
deb http://wine.budgetdedicated.com/apt/ karmic main
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main

## Dropbox
deb http://linux.getdropbox.com/ubuntu karmic main

## Boxee
# deb http://apt.boxee.tv jaunty main

## VirtualBox
deb http://download.virtualbox.org/virtualbox/debian karmic non-free

## Back in Time
deb http://le-web.org/repository stable main

## UbuntuOne
deb http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntuone/beta/ubuntu karmic main

## Google
deb http://dl.google.com/linux/deb/ stable non-free main
deb http://dl.google.com/linux/deb/ testing non-free main

## Miro
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

## Mendeley
deb http://www.mendeley.com/repositories/xUbuntu_9.04 /

###### PPA ######

## X updates (stable) AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu karmic main

## Karmic testing 40618B66 
# deb http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
# deb-src http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main

## Experimental boot
deb http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main 
# deb-src http://ppa.launchpad.net/ubuntu-boot/ppa/ubuntu karmic main

## Karmic kernel (Andy Whitcroft) CB0B05C0 
# deb http://ppa.launchpad.net/apw/jaunty-kernel/ubuntu karmic main restricted
# deb-src http://ppa.launchpad.net/apw/jaunty-kernel/ubuntu karmic main
# deb http://ppa.launchpad.net/apw/ppa/ubuntu karmic main restricted
# deb-src http://ppa.launchpad.net/apw/ppa/ubuntu karmic main

## VDPAU-team
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main

## Transitional
# deb http://ppa.launchpad.net/apw/staging/ubuntu karmic main
# deb-src http://ppa.launchpad.net/apw/staging/ubuntu karmic main

## ZgegBlog's Themes 881574DE 
deb http://debian.vogelweith.com/ intrepid zgegthemes
# deb-src http://debian.vogelweith.com/ intrepid zgegthemes

## Bisigi themes
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/bisigi/dev/ubuntu karmic main 
# deb-src http://ppa.launchpad.net/bisigi/dev/ubuntu karmic main

## Chromium 4E5E17B5
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

## Mozilla Daily
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ jaunty-wx main
# deb-src http://apt.wxwidgets.org/ jaunty-wx main

## UNetBootin
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main

## EarCandy
# deb http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/earcandy-devel/ppa/ubuntu jaunty main

## Liferea
# deb http://ppa.launchpad.net/liferea/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/liferea/ppa/ubuntu karmic main

## Webkit 2D9A3C5B 
# deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main

## bcmwl
# deb http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu karmic main
# deb-src http://ppa.launchpad.net/albertomilone/broadcom-sta/ubuntu karmic main
# deb http://ppa.launchpad.net/timg-tpi/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/timg-tpi/ppa/ubuntu karmic main

## gtg
deb http://ppa.launchpad.net/gtg/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/gtg/ppa/ubuntu jaunty main

## MSN-Pecan B85366AC
deb http://ppa.launchpad.net/msn-pecan/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/msn-pecan/ppa/ubuntu karmic main

## Anjal for Evo
# deb http://ppa.launchpad.net/paulliu/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/paulliu/ppa/ubuntu karmic main

## Banshee unstable
# deb http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/banshee-unstable-team/ppa/ubuntu karmic main

## Network Manager
# deb http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/network-manager/ppa/ubuntu karmic main

## TortoiseHG
deb http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu karmic main 
# deb-src http://ppa.launchpad.net/tortoisehg-ppa/releases/ubuntu karmic main 

## Listen
# deb http://ppa.launchpad.net/listen-devel/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/listen-devel/ppa/ubuntu karmic main

## Exaile
# deb http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/exaile-devel/ppa/ubuntu karmic main

## Empathy
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu karmic main

## LCD text improvements?
deb http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/improved-lcd-filtering/ppa/ubuntu karmic main

## Pidgin dev
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/iaz/pidgin/ubuntu karmic main
# deb-src http://ppa.launchpad.net/iaz/pidgin/ubuntu karmic main

## Moblin
# deb http://ppa.launchpad.net/moblin/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/moblin/ppa/ubuntu karmic main

## Bazaar
deb http://ppa.launchpad.net/bzr/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bzr/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/bzr-beta-ppa/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/bzr-beta-ppa/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu karmic main

## uzbl browser
# deb http://ppa.launchpad.net/pplr/uzbl/ubuntu karmic main
# deb-src http://ppa.launchpad.net/pplr/uzbl/ubuntu karmic main

## Gnome-Shell
deb http://ppa.launchpad.net/ricotz/testing/ubuntu karmic main 
# deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu karmic main 

## E17
deb http://packages.enlightenment.org/ubuntu karmic main extras

## Ubuntu tweak
deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/gnote/ppa/ubuntu karmic main #Gnote
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main #GNOME Do
deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu karmic main #Ubuntu Mozilla Security Team
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main #Shutter
```

---

### Post by slakkie on 2009-11-03
Added the Kubuntu PPA today. Think that is the only one I'm really interested in as a KDE user.

---

### Post by ranch hand on 2009-11-03
How in flinderation do you get the public keys for these buggers?

---

### Post by Regenweald on 2009-11-04
> **ranch hand said:**
> How in flinderation do you get the public keys for these buggers?
```
 sudo add-apt-repository ppa:'the ppa you need'
```
this command auto fetches the key.

---

### Post by ranch hand on 2009-11-04
Ah, and for "the ppa you need" I just put the title?

---

### Post by slakkie on 2009-11-04
> **ranch hand said:**
> How in flinderation do you get the public keys for these buggers?

Well, you get a bad key warning, and usually then I usually run:

```

sudo apt-key adv wwwkeys.eu.pgp.net --recv-keys KEYID

```

You can use keyserver.ubuntu.com as well, but it has been a bit flacky for me. So I use a different one.

---

### Post by zika on 2009-11-04
I think that the "new" way of adding repositories is better for this pre-toolchain upgrade to Lucid since, that way, all the data about ppa is stored in a file in sources.list.d folder inside /etc/apr/. The "old" way (entry in sources.list in /etc/apt/) could be a source of some problems. No, I've not yet switched to Lucid, waiting to see how the ppa's I use (xorg.edgers and mozilla-daily) respond to appearance of Lucid ...

---

### Post by Regenweald on 2009-11-04
> **ranch hand said:**
> Ah, and for "the ppa you need" I just put the title?

yup :) examples:
```

sudo add-apt-repository ppa:chromium-daily

sudo add-apt-repository ppa:nvidia-vdpau

sudo add-apt-repository ppa:rvm/smplayer

```
note the rvm one, some ppa's carry a small hierarchy, but they usually let you know.

---

### Post by ranch hand on 2009-11-04
Wow, I think, if I try real hard, I can handle this.

Thanks all.

---

### Post by Starks on 2009-11-04
Usually, add-apt-repository or using the "ppa: ppaname/suffix" format in the GUI will grab the keys, but if they aren't grabbed, there's a script by Blackgr that does it.

```
#! /bin/sh
if [ "`whoami`" != "root" ];
then
echo "Please run with SUDO"
exit 1
fi
RELEASE=`cat /etc/lsb-release | grep DISTRIB_CODENAME | cut -d"=" -f2`
echo Release: $RELEASE
echo Please Wait...
for q in `find /etc/apt/ -name *.list`; do
cat $q >> fullsourceslist
done
for i in `cat fullsourceslist | grep "deb http" | grep ppa.launchpad | grep $RELEASE | cut -d/ -f4`; do
    wget -q --no-check-certificate `wget -q --no-check-certificate [https://launchpad.net/~$i/+archive]("https://launchpad.net/%7E$i/+archive") -O- | grep "[http://keyserver.ubuntu.com:11371/pks/](http://keyserver.ubuntu.com:11371/pks/)" | cut -d'"' -f2 ` -O- | grep "pub  " | cut -d'"' -f2 >> keyss
done
for j in `cat keyss` ; do
    wget -q --no-check-certificate "[http://keyserver.ubuntu.com:11371$j](http://keyserver.ubuntu.com:11371$j)" -O- | grep -B 999999 END |grep -A 999999 BEGIN > keyss2
    sudo apt-key add keyss2
    rm keyss2
done
rm keyss
rm fullsourceslist

```

---

### Post by ranch hand on 2009-11-04
I really need to learn to right scripts.  It looks like almost too much FUN.

Thanks.

---

### Post by ceramicm on 2009-11-04
Here is a shorter command I picked up somewhere that updates the package list and then fetches any missing keys.

```
sudo apt-get update 2> /tmp/keymissing; for key in $(grep "NO_PUBKEY" /tmp/keymissing |sed "s/.*NO_PUBKEY //"); do echo  -e "\nProcessing key: $key"; gpg --keyserver subkeys.pgp.net --recv $key && gpg --export --armor $key | sudo apt-key add -; done
```

It works for repositories other than PPA's and fetches ALL keys (only has to be run once, not individually per repo). I keep it in the top of my sources.list file as a comment, so I don't lose it.

---

