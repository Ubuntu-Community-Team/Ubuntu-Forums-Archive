---
title: "[utility included] warty auto update script"
date: 2005-03-01
forum: Installation &amp; Upgrades
---

### Post by droneauth on 2005-03-01
Hi there,

i had to do a couple of ubuntu installations today and wrote a little utility to do some post-installation work for those of you new to ubuntu.

really no rocket science here, actually very quick & dirty hack to get your system ready (especially if you are not adept in configuring ubuntu/debian), so please don't bother flaming me.

basically this script does:

+ update your paketlist (universe, multiverse, extras - see below - a backup of your existing sources.list file is kept)
+ upgrade your pakets (if you want it to do so)
+ install extra pakets (*)

* pakets included are:
libdvdcss2, gxine, w32codecs, gstreamer0.8-mad, lame, lame-extras, flashplayer-mozilla, numlockx

features provided by those pakets are:
+ playing dvds in ubuntu with xine
+ mp3 de-/encoding
+ playing DivX/XviD files
+ flashplayer for mozilla browsers
+ startup numlock activation (if configured)

chmod +x it and run.

i hope this crap helps anybody.

droneauth.


```
#!/bin/bash
# auto baseconfiguration, updates and extras for a fresh
# and clean warty installation
# v 0.1

# Add some PATHs in our PATH
test -d /usr/local/bin && {
        PATH=$PATH:/usr/local/bin
        export PATH
        }
# Add /bin, /sbin and /usr/sbin
PATH=$PATH:/bin:/sbin:/usr/sbin
export PATH

# Lines of the sources file
Line[1]="deb http://archive.ubuntu.com/ubuntu/ warty main restricted"
Line[2]="deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted"
Line[3]="deb http://archive.ubuntu.com/ubuntu/ warty universe"
Line[4]="deb-src http://archive.ubuntu.com/ubuntu/ warty universe"
Line[5]="deb http://security.ubuntu.com/ubuntu/ warty-security main restricted"
Line[6]="deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted"
Line[7]="deb http://archive.ubuntu.com/ubuntu/ warty multiverse"
Line[8]="deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse"
Line[9]="deb ftp://ftp.nerim.net/debian-marillat/ testing main"

# Initialise the filename holding variables
APTFILE="$HOME/sources.list"
APTDIR="/etc/apt/"

# extend wanted extras here
extra_pakets="libdvdcss2 gxine w32codecs gstreamer0.8-mad lame lame-extras flashplayer-mozilla numlockx"

# create the sources.list in home directory
# Use the if control structure with test
# if test ([]) not exist (! -e) the filename which
# has the value ($) of sources then
if [ ! -e "$APTFILE" ]
then
        # touch is the best way of creating an empty file
        # although it sometimes doesn't work, we try this first.
        touch $APTFILE

        # Check again and if not there we will
        # create the file with an initial null string
        if [ ! -e "$APTFILE" ]
        then
                # > sends the output of echo to overwrite or create
                # the file.
echo "" > $APTFILE
        fi
        # end if
fi
# end if

# add additional apt repositories at end of file
# The >> appends the redirected output of echo onto
# the end of the file

# very ugly looping
for index in 1 2 3 4 5 6 7 8 9
do
        echo "${Line[index]}" >> $APTFILE
done

# make a backup of the default sources.list
# TODO: further cleanups
sudo mv /etc/apt/sources.list /etc/apt/sources.bkp

#move the generated file to apt confdir
sudo mv $APTFILE $APTDIR

# get new headers
echo "updating your paket headers..."
sudo apt-get update -y
echo "done!"

# do we want to upgrade?
echo "-----------------------------------------------"
echo " Do you want me to upgrade you system? (y/n):  "
echo "-----------------------------------------------"

read upgradeSystem  < /dev/tty

if [ "$upgradeSystem" = "y" ]; then
        sudo apt-get upgrade -y
fi

# do we want extras?
echo "------------------------------------------------"
echo " Do you want yummy extras installed, too? (y/n):"
echo "------------------------------------------------"

read installMultimedia  < /dev/tty

if [ "$installMultimedia" = "y" ]; then
        # add DVD, DivX, XviD, MP3 de- and encoding, flashplayer-mozilla
        sudo apt-get install $extra_pakets
fi

echo "---------------------------------------------------"
echo "we are done here, hopefully everything went well ;)"
echo "catch me at ubuntuforums.org                       "
echo "have a nice day!               droneauth(2004)     "
echo "---------------------------------------------------"

exit 0
```

---

### Post by droneauth on 2005-03-12
just for the record - im in the progress of extending this script to the very max atm.

stay tuned ;-)

---

