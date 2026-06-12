---
title: "Totem-xine in lucid"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-01-23
If coming upon please note that this isn't a 'proper' how-to - was just a post in the lucid dev forum.
There really wasn't any interest so I use it for myself basically.
There are 4 intertwined  how to's   here with slight diff's, karmic, lucid, maverick, natty -  read carefully and it should build/run fine.
(( timeline is only available in fs in lucid, maverick, natty ))


Edit2+:
(have working fine in lucid as of 03/11 - Maverick -Beta
install libtotem-plparser12 and libtotem-plparser-dev from karmic
Edit: no longer avail. normally - [get from here]("https://launchpad.net/ubuntu/+source/totem-pl-parser/2.28.1-1")
 (**remove lucid or maverick version** of libtotem-plparser-dev if installed first.
Note - for lucid, mav and natty install build-deps before  using dpkg to install libtotem-plparser-dev, gdebi doesn't matter

libtotem-plparser12 stays installed alongside the 17 ver. in lucid

<removed edit - old>

I always like to have a totem-xine player around, so this is a quick basic how to for the few that may feel likewise.

Based on a fresh, updated install, some things may be redundant otherwise, the menu creation, setting as a default dvd choice, may have things already in place. No matter  - should be obvious what to do.

Note this is totem-xine for use as local, streaming and dvd media player, no plugins are built including a working screensaver, video properties plugin.

While those are possible it requires a different config, some symlinks and possibly doing as shared. Personally not interested in those.

There is no longer an update-alternatives for totem, this method will though set totem-xine as the default audio-preview player. ( can be unset by deleting or renaming totem-audio-preview in /usr/local/bin, should be done in 64 bit 

Should only take about 5 -10 min.

build-deps (a few may be extraneous but no time ...  (-remove red in maverick and natty or remove altogether - not needed...?

```
sudo apt-get install python-support libglib2.0-dev liblircclient-dev \
libirman-dev gnome-pkg-tools libxine-dev libglade2-dev libxml-parser-perl \
libxml2-dev  gstreamer0.10-tools librsvg2-dev shared-mime-info libhal-dev  \
libssl-dev gtk-doc-tools librsvg2-common iso-codes libgmime-2.4-dev  \
libmusicbrainz4-dev gnome-icon-theme intltool dpkg-dev libx11-dev libcairo2-dev \
libdbus-glib-1-dev autotools-dev libgconf2-dev libgtk2.0-dev \
libxtst-dev libxrandr-dev libxxf86vm-dev gnome-doc-utils python-dev python-xdg \
python-apt python-rdflib python-gtk2-dev python-gobject-dev python-gst0.10 \
python-gdbm libxine1 checkinstall libxine1-ffmpeg [COLOR="Red"]libtrackerclient-dev[/COLOR] 
```

Edit3:
for karmic only 
```
sudo apt-get install libtotem-plparser-dev xulrunner-1.9.1-dev
```

**For lucid, maverick and natty only**
remove current libtotem-plparser-dev if installed (17)
get and install karmic version of libtotem-plparser12 and 
libtotem-plparser-dev as noted and linked above in Edit 2

For ALL
```
 mkdir totemx_build && cd totemx_build

```

```
wget http://ftp.acc.umu.se/pub/GNOME/sources/totem/2.26/totem-2.26.5.tar.gz

```
```

tar xzvf totem-2.26.5.tar.gz
```
```

cd totem-2.26.5 
```

Edit4:  consideration to adding to configure of this should be taken

--disable-python or leave (- can leave, have now added to  the checkinstall to deal with

Mainly because of how a # of .pyo's will be installed to /usr/..., could potentiality cause an issue with later install, rare but possible..

_Configure for Lucid and Maverick_
```
./configure --enable-xine --disable-browser-plugins --disable-nautilus \
--disable-shared --enable-xine --disable-browser-plugins --disable-nautilus \
--with-plugins=none --disable-shared --disable-schemas-install

```

Edit 4+:_ Configure for natty, O_, there are 2. One  allows smclient to be enabled, the other removes. I've no idea what use it is so either way is the same here

```
./configure --enable-xine --disable-browser-plugins --disable-nautilus \
--disable-shared --enable-xine --disable-browser-plugins --disable-nautilus \
--with-plugins=none --disable-shared --disable-schemas-install LDFLAGS=-lICE
```

```
./configure --enable-xine --disable-browser-plugins --disable-nautilus \
--disable-shared --enable-xine --disable-browser-plugins --disable-nautilus \
--with-plugins=none --disable-shared --disable-schemas-install --without-smclient
```

Configure for 12.04-A1
```
./configure --enable-xine --disable-browser-plugins --disable-nautilus \
--disable-shared --enable-xine --disable-browser-plugins --disable-nautilus \
--with-plugins=none --disable-shared --disable-schemas-install \
--without-smclient  LDFLAGS=-lgthread-2.0
```

```
make
```

Checkinstall for karmic only

```
sudo checkinstall --backup=no --deldoc=yes --pkgname totem-xine \
--pkgversion 2.28.5  --exclude=/usr/lib/python2.6/ --provides totem-xine \
--exclude=/usr/local/share/icons/hicolor/icon-theme.cache --default

```

Checkinstall for lucid only

```
sudo checkinstall --backup=no --deldoc=yes --pkgname totem-xine \
--pkgversion 2.30.5  --exclude=/usr/lib/python2.6/ --provides totem-xine \
--exclude=/usr/local/share/icons/hicolor/icon-theme.cache  --default

```

Checkinstall  for maverick only

```
sudo checkinstall --backup=no --deldoc=yes --pkgname totem-xine --default \
--pkgversion 2.32.6 --exclude=/usr/lib/python2.6/ --provides totem-xine \
--exclude=/usr/local/share/icons/hicolor/icon-theme.cache --fstrans=no
```

Checkinstall for natty only - no reason to beat around the bush, versioned higher than natty will ever see.

```
sudo checkinstall --backup=no --deldoc=yes --pkgname totem-xine \
--default --pkgversion 2.32.6 --exclude=/usr/lib/python2.7/ \
--provides totem-xine --exclude=/usr/local/share/icons/hicolor/icon-theme.cache \
--exclude=/usr/local/libexec/ --fstrans=no
```

Edit: it may be that the exclude icon-theme doesn't work anymore - if it is an issue now or later install the .deb in question w/
sudo dpkg -i --force  overwrite /path/to/deb

```
sudo mv /usr/local/bin/totem /usr/local/bin/totem-xine
```
```
sudo rm /usr/local/bin/totem-video-indexer
```
```
sudo rm /usr/local/bin/totem-video-thumbnailer
```

```
sudo ldconfig
```

 Create a  new menu item and change Exec=

```
mkdir ~/.local/share/applications
```
(if the dir already  exists you'll be told, just continue on

```
cp /usr/local/share/applications/totem.desktop ~/.local/share/applications/totem-xine.desktop
```

```
gedit ~/.local/share/applications/totem-xine.desktop
```

Change the name at the top from  Movie Player to what ever you wish, I use Totem Xine Media Player

Scroll down near bottom, find the #Exec=totem %U line and change to look like this ( **you must do this**..
EXEC=totem-xine %U
For natty maybe pick an icon, so on Icon= line - 
```
Icon=/usr/local/share/icons/hicolor/32x32/apps/totem.png
```
and Fro Natty  change to this
StartupNotify=false
save


To set a default dvd autorun choice

```
gedit ~/.local/share/applications/mimeapps.list
```

If mimeapps.list didn't exist the the file will be empty, if so insert
```
[Added Associations]
x-content/video-dvd=totem-xine.desktop;
```

If there is an existing mimeapps.list then look for the above line, if not there c+p in the new line
```
x-content/video-dvd=totem-xine.desktop;
```
if the line was there just this add to end, no space from last entry
```
totem-xine.desktop;
```

Then restart to set menu item, ect.

To activate dvd default
```
nautilus-file-management-properties
```
media -> dvd dropdown

Edit for Natty - unity: 
to add to the launcher

```
chmod +x ~/.local/share/applications/totem-xine.desktop
```

Either of these may  be considered in natty (or any)
```
sudo mv /usr/local/share/applications/totem.desktop /usr/local/share/applications/totem.desktop.bak
```
or

```
sudo rm /usr/local/share/applications/totem.desktop
```


Then in the dashboard - find more apps > browse to ~/.local/share/applications and select totem-xine.desktop

Edit: tested and working in natty beta1

The first time totem-xine starts it may have audio slider at 0

On my 32 bit - after adding libdvdcss2 played dvd's fine, all audio fine, added w32codecs for wma

Will also work on karmic ( you could change version to 2.28.5, no matter really

a few things not specific to this - 
if running nvidia you may wish to install compz-config-settings-manager and in 'Utility' enable 'video playback' or you may get flashing and be unable to access controls in fullscreen playback.
Also in general  options -> display settings ->  enable vsync and set refresh rate to actual one used, uncheck the 'unredirect  Fullscreen windows

With a small adjustment still good in maverick, though that may be the end of this - still going, natty and O Alpha2

---

