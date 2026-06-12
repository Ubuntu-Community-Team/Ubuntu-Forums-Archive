---
title: "Installing from lan without internet"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by 2fast4u on 2006-07-24
hello,

habitualy, I resolve my problems from the french forum and it looks down today :mad: , so excuse my wrote.
I tried to use a debmirror script to use a local network repository and netboot install.
All the downloaded files are host on a win2003 server with apache
I can boot from lan with pxelinux and the installation start well, but i can't select my local mirror
I can download file from the mirror server with wget. What have i miss.

[[img]http://img50.imageshack.us/img50/7775/install01qc5.th.jpg[/img]](http://img50.imageshack.us/my.php?image=install01qc5.jpg)  [[img]http://img212.imageshack.us/img212/889/install02eo4.th.jpg[/img]](http://img212.imageshack.us/my.php?image=install02eo4.jpg)

hope you understand me :-|

---

### Post by 2fast4u on 2006-07-24
here is the script i used to make my local mirror :
```
#!/bin/sh

#Quelques Variables à adapter eventuellement :

DESTINATION=/media/usbdisk/ubuntu
SERVEURSOURCE=fr.archive.ubuntu.com
DIST=ubuntu
VERSION=dapper
ARCH=i386
IGNOREGPG=1

METHOD=rsync
#METHOD=ftp
#METHOD=http

SECTIONS=main
SECTIONS=main,restricted
#SECTIONS=main,restricted,multiverse
#SECTIONS=main,restricted,multiverse,universe

#Synchroniser quoi ?
MIRROR_DIST=1
MIRROR_SECURITY=1
MIRROR_UPDATES=1
MIRROR_BACKPORTS=1

# On ne devrait pas avoir à editer la suite
STARTTIME=`date '+%d-%m-%y %H:%M:%S'`
if [ "$METHOD" == "rsync" ]; then SPECRSYNC=: ; else SPECRSYNC="" ; fi
if [ $IGNOREGPG -eq 1 ]; then GPG="--ignore-release-gpg " ; else GPG="" ; fi

echo "Creation/Update d'un miroir $DIST $VERSION $ARCH vers $DESTINATION"

if [ $MIRROR_DIST -eq 1 ]; then
echo "============================================================"
echo "Miroir de $DIST $VERSION vers $DESTINATION"
echo "============================================================"
debmirror $DESTINATION --host=$SERVEURSOURCE $GPG\
--arch=$ARCH --nosource --method=$METHOD \
--root=$SPECRSYNC$DIST \
--dist=$VERSION \
--section=$SECTIONS \
--getcontents \
--cleanup \
--progress
fi

if [ $MIRROR_SECURITY -eq 1 ]; then
echo "============================================================"
echo "Miroir de $VERSION-security vers $DESTINATION/security"
echo "============================================================"
debmirror $DESTINATION/security --host=security.ubuntu.com $GPG\
--arch=$ARCH --nosource --method=$METHOD \
--root=$SPECRSYNC$DIST \
--dist=$VERSION-security \
--section=$SECTIONS \
--getcontents \
--cleanup \
--progress
fi

if [ $MIRROR_UPDATES -eq 1 ]; then
echo "============================================================"
echo "Miroir de $VERSION-updates vers $DESTINATION/updates"
echo "============================================================"
debmirror $DESTINATION/updates --host=$SERVEURSOURCE $GPG\
--arch=$ARCH --nosource --method=$METHOD \
--root=$SPECRSYNC$DIST \
--dist=$VERSION-updates \
--section=$SECTIONS \
--getcontents \
--cleanup \
--progress
fi

if [ $MIRROR_BACKPORTS -eq 1 ]; then
echo "============================================================"
echo "Miroir de $VERSION-backports vers $DESTINATION/backports"
echo "============================================================"
debmirror $DESTINATION/backports --host=$SERVEURSOURCE $GPG\
--arch=$ARCH --nosource --method=$METHOD \
--root=$SPECRSYNC$DIST \
--dist=$VERSION-backports \
--section=$SECTIONS \
--getcontents \
--cleanup \
--progress
fi

echo "============================================================"
echo Debut de la synchronisation du miroir : $STARTTIME
echo Fin de la synchronisation du miroir   : `date '+%d-%m-%y %H:%M:%S'`

echo .
APTSECTIONS=`echo $SECTIONS | sed 's/,/ /g'`
LOCALIP=`ifconfig eth0|grep "inet "|cut -d ":" -f 2|cut -d " " -f 1`

echo Pour utiliser ce miroir, $DESTINATION doit etre accessible via http://localhost/$DIST
echo "(Depots deb suivants à ajouter dans /etc/apt/sources.list)"

if [ $MIRROR_DIST -eq 1 ]; then
echo deb http://$LOCALIP/$DIST/ $VERSION $APTSECTIONS
fi

echo "============================================================"
echo Debut de la synchronisation du miroir : $STARTTIME
echo Fin de la synchronisation du miroir   : `date '+%d-%m-%y %H:%M:%S'`

echo .
APTSECTIONS=`echo $SECTIONS | sed 's/,/ /g'`
LOCALIP=`ifconfig eth0|grep "inet "|cut -d ":" -f 2|cut -d " " -f 1`

echo Pour utiliser ce miroir, $DESTINATION doit etre accessible via http://localhost/$DIST
echo "(Depots deb suivants à ajouter dans /etc/apt/sources.list)"

if [ $MIRROR_DIST -eq 1 ]; then
echo deb http://$LOCALIP/$DIST/ $VERSION $APTSECTIONS
fi

if [ $MIRROR_SECURITY -eq 1 ]; then
echo deb http://$LOCALIP/$DIST/security/ $VERSION-security $APTSECTIONS
fi

if [ $MIRROR_UPDATES -eq 1 ]; then
echo deb http://$LOCALIP/$DIST/updates/ $VERSION-updates $APTSECTIONS
fi

if [ $MIRROR_BACKPORTS -eq 1 ]; then
echo deb http://$LOCALIP/$DIST/backports/ $VERSION-backports $APTSECTIONS
fi

echo "============================================================"
echo Taille des depots :
for el in `ls -1p $DESTINATION |grep /` ; do du -s --block-size=M $DESTINATION/$el ; done
echo "============================================================"
#echo Detail :
#for el in `ls -1p $DESTINATION/dist/ |grep /` ; do du -s --block-size=M $DESTINATION/$el ; done
#for el in `ls -1p $DESTINATION/security/ |grep /` ; do du -s --block-size=M $DESTINATION/security/$el ; done
#for el in `ls -1p $DESTINATION/updates/ |grep /` ; do du -s --block-size=M $DESTINATION/updates/$el ; done
#for el in `ls -1p $DESTINATION/backports/ |grep /` ; do du -s --block-size=M $DESTINATION/backports/$el ; done
#echo "============================================================"

```

---

### Post by gushy on 2007-03-30
did you ever solve this?  I've just run into the same problem and it's driving me mad.

---

