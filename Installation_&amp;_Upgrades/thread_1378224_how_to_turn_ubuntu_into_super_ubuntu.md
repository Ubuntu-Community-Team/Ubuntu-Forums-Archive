---
title: "how to turn ubuntu into super ubuntu???"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by gabak on 2010-01-11
hi i want to know how to install all software need it to make ubuntu into super OS.
Reason #1 even after i installed all codec i found , java , etc, sometime there are DVD movies i cant play , or sites that does nt work that well.

Here i leave you guys , my file with basic selection for ubuntu , just remove the TXT extension , (i had to do it or it wont let me upload it).

Software selection you have to import it with synaptic and you will have all software need to have ubuntu running well. (amsn , pidgin, vlc , freedvd, adobe flash,amule, etc)

Compiz.profile it is for compiz , it has nice effect if you dont have time to play with compiz.

---

### Post by slakkie on 2010-01-11
You might want to run the following:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi


# Get distro
distro=$(lsb_release -cs)

# Check if medibuntu repo is already present
src=/etc/apt/sources.list

grep -v "^#" $src | grep "packages.medibuntu.org" &>/dev/null
if [ $? -ne 0 ] ; then
    # Add them if not and update
    echo "" >> $src
    echo "## Medibuntu repositories, visit http://www.medibuntu.org/ for more details" >> $src
    echo "deb http://packages.medibuntu.org/ $distro free non-free" >> $src
    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs

```

Save the contents as multimedia.sh. Then: chmod +x multimedia.sh and run it as root: sudo ./multimedia.sh

---

### Post by gabak on 2010-01-12
great
i done that.
now what about all software it comes with super ubuntu?
do u have any script so it will leave it the same way it is?

---

### Post by 00ber n00b on 2010-01-12
> **slakkie said:**
> You might want to run the following:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi


# Get distro
distro=$(lsb_release -cs)

# Check if medibuntu repo is already present
src=/etc/apt/sources.list

grep -v "^#" $src | grep "packages.medibuntu.org" &>/dev/null
if [ $? -ne 0 ] ; then
    # Add them if not and update
    echo "" >> $src
    echo "## Medibuntu repositories, visit http://www.medibuntu.org/ for more details" >> $src
    echo "deb http://packages.medibuntu.org/ $distro free non-free" >> $src
    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs

```

Save the contents as multimedia.sh. Then: chmod +x multimedia.sh and run it as root: sudo ./multimedia.sh

Thanks! LOL

---

