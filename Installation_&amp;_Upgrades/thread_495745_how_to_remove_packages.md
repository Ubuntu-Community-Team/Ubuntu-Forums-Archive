---
title: "how to remove packages"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by drgoplayer on 2007-07-08
I am definitely not an advanced user.
We installed feisty on a 3 gb partition and had very little space left.
I had successfully removed many apps from breezy so thought feisty might work the same.
We tried removing various apps and they all said they would remove ubuntu desktop and other
frightening things.
Finally we removed a few things assuming that it wouldnt remove critical dependencies.  The box would only reboot in safe mode (as root) and the wifi card wouldnt work so no access to any repostories except thru the live CD.  When I tried reinstalling thru the live CD, it either said the package wasnt available or was already installed.  Finally donwloaded a cd image for dapper and installed that.  only 780 mb free but that is more than feisty left.  Again all the packages say they will also remove ubuntu-desktop.

Is it possible to remove apps without breaking the desktop?  Even removing a font such as ttf-arphic-ukai will remove ubuntu-desktop.  We would like to remove most of these but with dapper
and feisty they seem to be tied to ubuntu-desktop.
aspell
bicyclerepair
blt
busybox
cdrecord
contact lookup
diveintopython
eog
evolution
fd utils
foomatic
gaim
gcalctool
gettext
gnome-games
gnomemeeting
groff-base
gthumb
gtk2 themes
gucharmap
j2re1.4
irrsi-text
metacity
rhythmbox
rss-glx
samba-common
smbclient
ttf-arphic
ttf-baekmuk
other foreign fonts
x-fonts

---

### Post by aquavitae on 2007-07-08
The ubuntu-desktop package is just an empty package with a lot of dependancies.  This is so that by installing just ubuntu-desktop you can be sure of getting most of the common apps required, as well as all the required apps for the descktop to run.  But by itself it does nother, no there's no danger in removing it.  But be careful then about what other packages you remove, because the ubuntu-desktop dependacy is also a safety device to make sure you don't remove anything inportant.  I can see at least two packages you've listed that could break your desktop if removed: metacity and busybox.  If your pc won't start after removing something, reinstallation isn't necessarily the only way - its sometimes possible to patch it up by changing settings so that you can get in a fix it properly.  If that happenes again, I'd suggest you make a post of the problem as hopefullly we'll be able to help!

---

