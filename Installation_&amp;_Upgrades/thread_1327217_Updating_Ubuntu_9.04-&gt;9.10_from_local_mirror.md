---
title: "Updating Ubuntu 9.04-&gt;9.10 from local mirror"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by SSnacho on 2009-11-15
Hello.
In my LAN i maintain a local ubuntu mirror. It is created with debmirror, and the script that i found in help. Source for the updates is mirror.yandex.ru/ubuntu/
Me and other users in my network have problems with updating Ubuntu from this local mirror. After running update manager, and confirming changes in sources.list(it changes jaunty records to karmic), during the next stage of update an error occures:
"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."
And the goes a rather big list of different packages even for clean system(i installed Ubuntu on VirtualBox and still had the same problem).
Please help me to correct this errors, and if it possible without affecting other users. I would like to correct the errors by myself, as a mirror maintainer.
In addition, maybe it may help, I run mirroring script from the computer with Linux Mint 7, but the mirror files are located on another computer with Windows 2003 Server, which uses lighttpd as http-server.
And this is script, that I use to make a mirror:
```
#### Start script to automate building of Ubuntu mirror #####
## THE NEXT LINE IS NEEDED THE REST OF THE LINES STARTING WITH A # CAN BE DELETED

#!/bin/bash

## Setting variables with explanations.

#
# Don't touch the user's keyring, have our own instead
#
export GNUPGHOME=/home/mirrorkeyring

TODAY=`date "+%Y-%m-%d"`
LOGFILE=./update_${TODAY}.log

# Arch=         -a      # Architecture. For Ubuntu can be i386, powerpc or amd64.
# sparc, only starts in dapper, it is only the later models of sparc.
#
arch=i386,amd64

# Minimum Ubuntu system requires main, restricted
# Section=      -s      # Section (One of the following - main/restricted/universe/multiverse).
# You can add extra file with $Section/debian-installer. ex: main/debian-installer,universe/debian-installer,multiverse/debian-installer,restricted/debian-installer
#
section=main,restricted,universe,multiverse

# Release=      -d      # Release of the system (Dapper, Edgy, Feisty, Gutsy, Hardy, Intrepid), and the -updates and -security ( -backports can be added if desired)
#
release=jaunty,jaunty-security,jaunty-updates,jaunty-proposed,jaunty-backports,karmic,karmic-security,karmic-updates,karmic-proposed,karmic-backports,lucid,lucid-security,lucid-updates,lucid-proposed,lucid-backports
# Server=       -h      # Server name, minus the protocol and the path at the end
# CHANGE "*" to equal the mirror you want to create your mirror from. au. in Australia  ca. in Canada.
# This can be found in your own /etc/apt/sources.list file, assuming you have Ubuntu installed.
#
#server=cc.archive.ubuntu.com
server=77.88.19.74

# Dir=          -r      # Path from the main server, so [http://my.web.server/](http://my.web.server/)$dir, Server dependant
#
inPath=/ubuntu

# Proto=        -e      # Protocol to use for transfer (http, ftp, hftp, rsync)
# Choose one - http is most usual the service, and the service must be avaialbe on the server you point at.
#
proto=http

# Outpath=              # Directory to store the mirror in
# Make this a full path to where you want to mirror the material.
#
outPath=/media/ubuntumir/

# The --nosource option only downloads debs and not deb-src's
# The --progress option shows files as they are downloaded
# --source \ in the place of --no-source \ if you want sources also.
# --nocleanup  Do not clean up the local mirror after mirroring is complete. Use this option to keep older repository
# Start script
#
debmirror       -a $arch \
                --no-source \
      --ignore-release-gpg \
                -s $section \
                -h $server \
                -d $release \
                -r $inPath \
                --progress \
                -e $proto \
                $outPath


#### End script to automate building of Ubuntu mirror ####
```
P.S. I'm very sorry for my English. Maybe its not good enough.

---

### Post by SSnacho on 2009-11-18
up.
hope it is not against the rules.

---

### Post by OntO on 2010-04-16
up

---

