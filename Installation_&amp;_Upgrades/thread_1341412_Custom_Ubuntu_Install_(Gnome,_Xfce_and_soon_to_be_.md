---
title: "Custom Ubuntu Install (Gnome, Xfce and soon to be KDE)"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Cypher2 on 2009-11-29
Hello to all, this is my first official post after having used the forum as an answer pool for all my *ubuntu issues.

My current little project involves streamlining and customizing my ubuntu install to its bare necessities for my usual uses without all the excessive package bloat on standard installs.

The script I have made, derived from one i found online at : [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961) integrates all the necessary base packages installed via a minimal image of ubuntu and with apt-get flaged as --no-install-recommends.

the final part to my adventure requires my requesting the computer $HOSTNAME and the script recognizing it to copy the appropriate fstab backup i have on the media depending on the computer im installing it on.

Example: 

-------------------------------

desktop name: MERCURY - laptop name: SOLACE

-------------------------------

#!/bin/bash
echo "
[*] Installing configuration files..."
hostname
echo "Confirm computer name: "
read NAME
echo "Computer name is $NAME..."
N1=MERCURY
N2=mercury
N3=SOLACE
N4=solace
if [ $NAME=$N1 ];
        then sudo cp /media/CRUZER/desktop/fstab /home
    echo "Copying from /desktop/..."

elif [ $NAME=$N2 ];
        then sudo cp /media/CRUZER/desktop/fstab /home
    echo "Copying from /desktop/..."

elif [ $NAME=$N3 ];
        then sudo cp /media/CRUZER/laptop/fstab /home
    echo "Copying from /laptop/..."

elif [ $NAME=$N4 ];
        then sudo cp /media/CRUZER/laptop/fstab /home
    echo "Copying from /laptop/..."

fi


          


-----------------------

Even knowing some scripting commands and variables, I unfortunately am not able to get the damn thing running properly for the commands to pass..

Would there be anyone kind enough to explain to me how to set the syntax on this module?

Thank you :)

---

